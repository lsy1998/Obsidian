1. 代码
2. 模版
3. 数据字典
```sql
insert into sys_dict_type select * from sys_dict_type@DBL_ATGD_HRM_TEST where dict_type in('NO_ABNORMAL_ATTENDANCE_EMAIL','EMPLOYEE_STATUS','FAMILY_RELATIONS','PAY_SLIP_COMPANY_CONTRIBUTION');
insert into sys_dict_data select * from sys_dict_data@DBL_ATGD_HRM_TEST where dict_type in('NO_ABNORMAL_ATTENDANCE_EMAIL','EMPLOYEE_STATUS','FAMILY_RELATIONS','PAY_SLIP_COMPANY_CONTRIBUTION');
```
4. 菜单
5. 数据库
	1. 新字段
	2. 新表
	3. 新脚本

