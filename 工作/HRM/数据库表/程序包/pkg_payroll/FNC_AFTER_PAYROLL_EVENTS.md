获取假期余额 [[PR_LEAVE_BAL_DTL]]
获取假期余额 [[LV_EE_LEAVE_BAL]]

> 这段 SQL 是一个 Oracle 存储过程，名为 FNC_AFTER_PAYROLL_EVENTS，接收了 10 个输入参数和 1 个输出参数。它的作用是检查指定员工在指定支付期间内的请假余额情况，并返回一个 Y 或 N 的值。
> 
> 其中，它使用了两个游标（c1_cur 和 c2_cur）来查询两个表内的数据。c1_cur 查询了 LV_EE_LEAVE_BAL 表内最近的员工请假余额信息，排除了年假和公司请假类型。而 c2_cur 则查询了 PR_LEAVE_BAL_DTL 表内的详细请假余额信息。
> 
> 当检查到错误时，会抛出 user_def_err 异常，并将错误信息赋值给 v_error_text 变量。当出现其他异常时，会将 SQLERRM 函数的返回值与错误信息组合成 pov_error_text 输出参数返回。
> 
> 如果一切正常，函数会将 pov_error_text 设为空，并返回 'Y' 值。