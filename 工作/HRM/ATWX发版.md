1. 代码
2. 模版
	整个打包上传过去
3. 数据字典
```sql
insert into sys_dict_type select * from sys_dict_type@DBL_ATGD_HRM_TEST where dict_type in('NO_ABNORMAL_ATTENDANCE_EMAIL','EMPLOYEE_STATUS','FAMILY_RELATIONS','PAY_SLIP_COMPANY_CONTRIBUTION');
insert into sys_dict_data select * from sys_dict_data@DBL_ATGD_HRM_TEST where dict_type in('NO_ABNORMAL_ATTENDANCE_EMAIL','EMPLOYEE_STATUS','FAMILY_RELATIONS','PAY_SLIP_COMPANY_CONTRIBUTION');

insert into sys_dict_data select * from sys_dict_data@DBL_ATGD_HRM_TEST where dict_type in('EE_GROUP_SORT');
insert into sys_dict_type select * from sys_dict_type@DBL_ATGD_HRM_TEST where dict_type in('EE_GROUP_SORT');
```
4. 菜单

5. 数据库
	1. 新字段
	![[Pasted image 20230620162815.png]]![[Pasted image 20230620162852.png]]![[Pasted image 20230620163126.png]]![[Pasted image 20230620164342.png]]![[Pasted image 20230620164719.png]]![[Pasted image 20230620164927.png]]
	3. 新表
```sql
create table tr_attend as select * from tr_attend@DBL_ATGD_HRM_TEST where 1=2;
create table tr_attend_employee as select * from tr_attend_employee@DBL_ATGD_HRM_TEST where 1=2;
create table tr_schedule as select * from tr_schedule@DBL_ATGD_HRM_TEST where 1=2;

create table EXAM_ACTUAL_OPERATION as select * from EXAM_ACTUAL_OPERATION@DBL_ATGD_HRM_TEST where 1=2;
create table EXAM_ACTUAL_OPERATION_DETAIL as select * from EXAM_ACTUAL_OPERATION_DETAIL@DBL_ATGD_HRM_TEST where 1=2;
create table EXAM_ACTUAL_TEMPLATE as select * from EXAM_ACTUAL_TEMPLATE@DBL_ATGD_HRM_TEST where 1=2;
```
	1. 新脚本

