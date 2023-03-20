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
## 作用
在 [[ee_payment_term]] 中取 <font color="#ff0000">(nvl(base_salary,0) + nvl(prc_er_benefit_encash, 0) + nvl(local_er_pfund_encash, 0))</font>，<font color="#00b050">(nvl(base_salary,0) + nvl(pfund_adjust, 0))</font>，<font color="#0070c0">salary_rate</font> 的最大值作为 salary rate