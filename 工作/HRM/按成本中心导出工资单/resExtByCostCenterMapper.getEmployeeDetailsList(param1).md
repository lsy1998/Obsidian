## SQL

```sql
SELECT  
    ejd.ee_id,  
    estm.section_id,   
    estm.sub_section_id,  
    ejd.position,  
    ejd.grading, <!-- 20220817 取grading的值 -->  
    ejd.cost_center, <!-- 20221206 取costCenter的值 -->  
    DECODE(emt.job_category, 'D','Direct', 'I', 'Indirect', null) as job_Category, <!-- 20221206 取workday类别的值 -->  
    ejd.version_no,  
    ejd.effective_date,  
    emt.ee_group  
FROM ee_job_dtl ejd, ee_section_team_member estm, ee_employ_term emt  
WHERE ejd.ee_id IN (SELECT prd.ee_id  
FROM pr_result_dtl prd  
WHERE pay_period_group = NVL(#{payPeriodGroup}, prd.pay_period_group)  
AND prd.pay_period = #{payPeriod})  
AND ejd.effective_date = pkg_slookup.fnc_ee_job_dtl_edate(ejd.ee_id, #{payToDate})  
AND ejd.version_no = pkg_slookup.fnc_ee_job_dtl_mver(ejd.ee_id, ejd.effective_date)  
AND ejd.division_id = #{organId}  
AND ejd.ee_id              = estm.ee_id (+)  
AND NVL(estm.team_id, '1') = #{teamId}  
AND ejd.department_id      = #{departId}  
AND emt.ee_id              = ejd.ee_id  
AND emt.effective_date     = pkg_slookup.fnc_ee_employ_term_edate(emt.ee_id, #{payToDate})  
AND emt.version_no         = pkg_slookup.fnc_ee_employ_term_mver(emt.ee_id, emt.effective_date)  
AND emt.ee_group           = NVL(#{eeGroup}, emt.ee_group)  
AND emt.pay_period_group      = NVL(#{payPeriodGroup}, emt.pay_period_group)  
AND emt.shift_type         = NVL(#{shift}, emt.shift_type)  
AND ejd.grading             &gt;= NVL(#{fromGrade}, ejd.grading)  
AND ejd.grading             &lt;= NVL(#{toGrade}, ejd.grading)  
AND        DECODE(emt.termination_date, NULL, 'N' , 'Y') =  #{terminateFlag}  
<if test="termFromDate != null or termToDate != null">  
    AND NVL (emt.termination_date, TO_DATE ('1950-01-01', 'RRRR-MM-DD'))  
    BETWEEN NVL(#{termFromDate,jdbcType=DATE}, NVL(emt.termination_date, TO_DATE ('1950-01-01', 'RRRR-MM-DD')))  
    AND NVL (#{termToDate,jdbcType=DATE}, NVL(emt.termination_date, TO_DATE ('1950-01-01', 'RRRR-MM-DD')))  
</if>  
AND estm.section_id = #{sectionId, jdbcType=VARCHAR}  
AND estm.sub_section_id = #{subSectionId, jdbcType=VARCHAR}  
ORDER BY  
    ejd.division_id,  
    estm.sub_section_id,  
    ejd.ee_id
```
## 作用
根据 <font color="#ff0000">terminationFlag</font> 筛选离职员工还是未离职员工