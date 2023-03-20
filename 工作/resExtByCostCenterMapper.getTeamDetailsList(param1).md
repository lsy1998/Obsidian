
```sql
SELECT  
    ejd.department_id,  
    estm.section_id,  
    estm.sub_section_id,  
    NVL(estm.team_id, '1') as team_id,  
    estm.description  
FROM ee_job_dtl ejd, ee_section_team_member estm  
WHERE ejd.ee_id IN  
(  
SELECT prd.ee_id  
FROM pr_result_dtl prd  
WHERE pay_period_group = NVL(#{payPeriodGroup}, prd.pay_period_group)  
    AND prd.pay_period = #{payPeriod}  
)  
AND ejd.effective_date = pkg_slookup.fnc_ee_job_dtl_edate(ejd.ee_id, #{payToDate})  
AND ejd.version_no = pkg_slookup.fnc_ee_job_dtl_mver(ejd.ee_id, ejd.effective_date)  
AND ejd.division_id = #{organId}  
AND ejd.department_id = #{departId}  
AND ejd.ee_id = estm.ee_id (+)  
and ejd.grading &gt;= NVL(#{fromGrade}, ejd.grading)  
and ejd.grading &lt;= NVL(#{toGrade}, ejd.grading)  
AND EXISTS  
(  
SELECT /*+ index(emt, pk_ee_employ_term)*/ 1  
FROM ee_employ_term emt  
WHERE emt.ee_id = ejd.ee_id  
    AND emt.effective_date = pkg_slookup.fnc_ee_employ_term_edate(emt.ee_id, #{payToDate})  
    AND emt.version_no = pkg_slookup.fnc_ee_employ_term_mver(emt.ee_id, emt.effective_date)  
    AND emt.ee_group = NVL(#{eeGroup}, emt.ee_group)  
    AND emt.pay_period_group = NVL(#{payPeriodGroup}, emt.pay_period_group)  
    AND emt.shift_type = NVL(#{shift}, emt.shift_type)  
    AND DECODE(emt.termination_date, NULL, 'N' , 'Y') = #{terminateFlag}  
    <if test="termFromDate != null or termToDate != null">  
    AND NVL (emt.termination_date, TO_DATE ('1950-01-01', 'RRRR-MM-DD'))  
    BETWEEN NVL(#{termFromDate,jdbcType=DATE}, NVL(emt.termination_date, TO_DATE ('1950-01-01', 'RRRR-MM-DD')))  
    AND NVL (#{termToDate,jdbcType=DATE}, NVL(emt.termination_date, TO_DATE ('1950-01-01', 'RRRR-MM-DD')))  
    </if>  
GROUP BY  
    ejd.department_id,  
    estm.section_id,  
    estm.sub_section_id,  
    estm.team_id,  
    estm.description
```
