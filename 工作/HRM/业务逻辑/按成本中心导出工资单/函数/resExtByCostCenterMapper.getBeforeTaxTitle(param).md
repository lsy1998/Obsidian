## SQL

```sql
SELECT  
pid.payroll_trans_id,  
pid.item_category,  
pid.c_name c_name  
FROM       pr_item_defn      pid,  
pr_report_group   prg  
WHERE      pid.item_owner            = 'EE'  
AND        prg.payroll_trans_id      = pid.payroll_trans_id  
AND        prg.fnc_id                = #{progId}  
AND        prg.payroll_report_group  = 'BEFORE_TAX'  
AND        EXISTS    (SELECT  1  
FROM   pr_result_dtl   prd  
WHERE  prg.payroll_trans_id     =  prd.payroll_trans_id  
AND    prd.pay_period_group     =  NVL(#{payPeriodGroup}, prd.pay_period_group)  
AND    prd.pay_period           =  #{payPeriod}  
AND    prd.payroll_amount       &lt;&gt; 0)  
ORDER BY   pid.item_category, pid.payroll_trans_id
```
## 相关数据表
[[pr_item_defn]]
[[pr_report_group]]
[[pr_result_dtl]]
