## SQL

```sql
SELECT  
<!-- salary_rate -->  
<!-- 20220810 modify by sam 考虑老系统数据兼容性 -->  
(  
    case  
    when  
        nvl(base_salary,0) + nvl(prc_er_benefit_encash, 0) + nvl(local_er_pfund_encash, 0) &gt; salary_rate  
    then  
        nvl(base_salary,0) + nvl(prc_er_benefit_encash, 0) + nvl(local_er_pfund_encash, 0)  
    when  
        nvl(base_salary,0) + nvl(pfund_adjust, 0) &gt; salary_rate  
    then  
        nvl(base_salary,0) + nvl(pfund_adjust, 0)  
    else  
        nvl(salary_rate,0)  
    end  
) salary_rate  
FROM   ee_payment_term  
WHERE  ee_id          = #{eeId}  
AND    effective_date    = pkg_slookup.fnc_ee_payment_term_edate(ee_id, #{entryDate})  
AND    version_no        = pkg_slookup.fnc_ee_payment_term_mver(ee_id, effective_date)
```
[[ee_payment_term]] 