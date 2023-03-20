## SQL

```sql
SELECT  
payroll_trans_id,  
payroll_amount  
FROM       pr_result_dtl  
WHERE      pay_period_group  =  NVL(#{payPeriodGroup}, pay_period_group)  
AND        pay_period        =  #{payPeriod}  
AND        ee_id             =  #{eeId}  
ORDER BY   payroll_trans_id
```
## 作用
获取某个员工某个付薪周期内的pr项及金额