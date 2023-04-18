1. 找到除年假和公休假外，该员工拥有的其他假期余额数据 [[LV_EE_LEAVE_BAL]]
2. 找到该员工拥有的其他假期余额数据(临时表) [[PR_LEAVE_BAL_DTL]]
3. 在 [[LV_EE_LEAVE_BAL]] 插入新纪录
4. 在 [[PR_LEAVE_BAL_DTL]] 更新或插入新纪录 