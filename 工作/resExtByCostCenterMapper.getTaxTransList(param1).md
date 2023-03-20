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
