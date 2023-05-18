## 同步逻辑
#### 1. 089服务器上自动任务从固定路径解密workday文件
自动任务和对应的执行脚本
![[Pasted image 20230518111243.png]]
四个脚本分别处理不同表的数据，脚本解密后的文件在hrm处理之后会删除，只保留处理日志和原始文件在processed文件夹下。
```shell
@echo off
::指定起始文件夹
set "fromDir=W:\APG_TEST\EE_Employ_Term\Input\"
::指定目标文件夹
set "toDir=W:\APG_TEST\EE_Employ_Term\Working\"
::文件名后缀
set suf="*.GPG"

::先将起始文件夹下面的所有GPG文件（不包括子文件夹里面的文件）移动到目标文件夹下面
for %%f in (%fromDir%%suf%) do move %%f %toDir%

::然后将目标文件夹下面的GPG文件（不包括子文件夹里面的文件）进行解密（解密调用ms089服务器安装的gpg程序），解密后的文件放在目标文件夹下面，
::解密后的文件名格式为：GPG文件名小写(没有文件名后缀)（如：将 Abc.gpg 文件解密后得到 abc 文件）
::APGHRMADMIN 是程序中解出来的私钥密码
for /f "delims=" %%i in ('dir /b/l %toDir%%suf%') do (
	gpg --batch --yes --passphrase "APGHRMADMIN" --output %toDir%%%~ni --decrypt %toDir%%%i
)

exit
```

#### 2. hrm通过定时任务从089上固定路径读取解密后的文件
hrm有三个不同时间的定时任务同步workday的数据，这三个定时任务的功能是一模一样的。![[Pasted image 20230518112642.png]]

#### 3. 跳过第一行之后逐行读取处理数据，数据通过校验后插入到相对应的workday原始数据表和对应表

## 例子

#### 同步[[ee_employee_term]]
解密后原始数据(**可通过将 "^" 替换成 ","，将后缀名改为csv将其转换为csv文件** )
```
EE_ID^EFFECTIVE_DATE^EE_GROUP^EMPLOY_TERM^JOIN_DATE^OFF_PROBATION_DATE^CONTRACT_START_DATE^CONTRACT_END_DATE^CONTRACT_PACKAGE_RMKS^TERMINATION_NOTICE_PERIOD^TERMINATION_NOTICE_UNIT^TERMINATION_NOTICE_DATE^TERMINATION_DATE^TERMINATION_REASON_ID^PAY_PERIOD_GROUP^ROSTER_FLAG^SHIFT_TYPE^PRODUCT_CLASS^HOLIDAY_CALENDAR^TRANSFER_FLAG^TRANSFER_DATE^PAST_EE_ID^TIME_CARD_NO^HOLIDAY_SCHEDULE_FLAG^SAP_ID
G00211^2023-05-12^STAFF^P^2021-08-06^2021-11-05^^^^^^^2023-05-12^S^ALL_STAFF^N^^I^^^^^^^33956335
047079^2023-05-08^OPERATOR^C^2023-05-08^2023-07-07^2023-05-08^2026-05-07^^^^^^^ALL_STAFF^Y^^D^^^^^^^33964923
047081^2023-05-08^OPERATOR^C^2023-05-08^2023-07-07^2023-05-08^2026-05-07^^^^^^^ALL_STAFF^Y^^D^^^^^^^33964925
047082^2023-05-08^OPERATOR^C^2023-05-08^2023-07-07^2023-05-08^2026-05-07^^^^^^^ALL_STAFF^Y^^D^^^^^^^33964927
047080^2023-05-08^OPERATOR^C^2023-05-08^2023-07-07^2023-05-08^2026-05-07^^^^^^^ALL_STAFF^Y^^D^^^^^^^33964924
047084^2023-05-08^OPERATOR^C^2023-05-08^2023-07-07^2023-05-08^2026-05-07^^^^^^^ALL_STAFF^Y^^D^^^^^^^33964926
047083^2023-05-08^OPERATOR^C^2023-05-08^2023-07-07^2023-05-08^2026-05-07^^^^^^^ALL_STAFF^Y^^D^^^^^^^33964928
```

数据整理后
![[result.json]]
