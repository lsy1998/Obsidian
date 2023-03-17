sql:

```sql
SELECT  
    pay_from_date as pod_pay_from_date,  
    pay_to_date as pod_pay_to_date,  
    cutoff_from_date as pod_cutoff_fm_date,  
    cutoff_to_date as pod_cutoff_to_date  
FROM  
    pr_pay_period_defn  
WHERE pay_period_group = #{payPeriodGroup} AND pay_period = #{payPeriod}
```
通过<font color="#ff0000">付薪组别</font>和<font color="#ff0000">付薪月份</font>获取pay_from_date，pay_to_date，cutoff_from_date，cutoff_to_date
