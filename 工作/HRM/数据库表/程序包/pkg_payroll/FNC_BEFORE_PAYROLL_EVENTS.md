1. 找到除年假和公休假外，该员工拥有的其他假期余额数据 [[LV_EE_LEAVE_BAL]]
2. 找到该员工拥有的其他假期余额数据(临时表) [[PR_LEAVE_BAL_DTL]]
3. 在 [[LV_EE_LEAVE_BAL]] 插入新纪录
4. 在 [[PR_LEAVE_BAL_DTL]] 更新或插入新纪录
5. 删除“[[PR_RESULT_DTL]]”、“[[PR_RESULT]]”、“[[PR_TAX_RETURN_DTL]]”、“[[PR_COST_CENTER_RESULT]]”和“[[WRK_PR_COST_CENTER_RESULT]]”表中与指定员工在指定时间段内的记录。(可能是之前计算产生的工资数据)
6.  如果过程出现异常，则返回 N，并通过 OUT 参数“pov_error_text”传递异常信息；否则返回 Y。