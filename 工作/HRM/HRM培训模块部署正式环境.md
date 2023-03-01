### 代码：
nx017142 2023/2/14 16:29 fix(培训模块):功能完善及bug修复
nx017142 2023/2/14 9:45 fix(培训模块):功能完善及bug修复
nx017142 2023/2/10 11:43 fix(培训模块):功能完善及bug修复
nx017142 2023/2/8 10:44 fix(培训模块):功能完善及bug修复
nx017142 2023/2/7 14:25 fix(培训模块):功能完善及bug修复
nx017142 2023/2/6 16:34 fix(培训模块):功能完善及bug修复
nx017142 2023/2/6 15:22 fix(培训模块):功能完善及bug修复
nx017142 2023/2/6 14:39 fix(培训模块):功能完善及bug修复
nx017142 2023/2/1 8:51 fix(培训模块):功能完善及bug修复
nx017142 2023/1/31 14:21 fix(财务模块):无法删除，判空错误bug修复
nx017142 2023/1/18 17:15 feat(培训模块):功能优化与bug修复
nx017142 2023/1/5 18:12 feat(培训模块):功能优化与bug修复
nx017142 2022/12/14 15:03 feat(培训模块):修改菜单
nx017142 2022/12/14 14:51 feat(培训模块):修改菜单

### 数据库：
先备份，再删除，再从测试库复制
``` 
create table tr_attend_bak as select * from tr_attend
create table tr_attend_employee_bak as select * from tr_attend_employee

--删除表
tr_attend
tr_attend_employee

--复制测试数据库的表
create table tr_attend as select * from tr_attend@xxdblink
create table tr_attend_employee as select * from tr_attend_employee@xxdblink

--如果指导员组要保留培训数据
delete from tr_attend_employee where course_number in (select course_number from tr_attend_bak where type='2')
delete from tr_attend where type='2'

insert into tr_attend select 

```
tr_attend
tr_attend_employee

### 模板修改：
![[Pasted image 20230301094743.png]]

### 权限和角色：
![[Pasted image 20230301094909.png]]

### 菜单修改：
![[Pasted image 20230301095113.png]]

