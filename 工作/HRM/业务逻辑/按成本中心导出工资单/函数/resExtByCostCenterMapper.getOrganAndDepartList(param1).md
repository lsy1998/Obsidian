## 输入
```java
param1.setPayToDate(payPeriodDefn.get(0).get("POD_PAY_TO_DATE"));  
param1.setUsrId(param.getUsrId());  
param1.setProgId(param.getProgId());  
param1.setPayPeriodGroup(param.getPayPeriodGroup());  
param1.setPayPeriod(param.getPayPeriod());  
param1.setDepartId(param.getDepartId());  
param1.setEeGroup(param.getEeGroup());  
param1.setFromGrade(param.getFromGrade());  
param1.setToGrade(param.getToGrade());  
param1.setShift(param.getShift());  
param1.setTerminateFlag(param.getTerminateFlag());  
param1.setTermFromDate(param.getTermFromDate());  
param1.setTermToDate(param.getTermToDate());
```
## SQL
```sql
SELECT  
    division_id organization_id,  
    depart_id department_id  
FROM  
    <!-- organization_defn, od, -->  
    <!-- 20221228：因为员工定义那里取消了组织字段，所以此次需要改成查询厂区 -->  
    division_defn od,  
    department_defn dd  
WHERE EXISTS  
(  
    SELECT  1  
    FROM ee_job_dtl ejd  
    WHERE  
    <!-- od.organization_id = ejd.organization_id -->  
    od.division_id = ejd.division_id  
    AND dd.depart_id = ejd.department_id  
    and ejd.grading &gt;= NVL(#{fromGrade}, ejd.grading)  
    and ejd.grading &lt;= NVL(#{toGrade}, ejd.grading)  
    AND ejd.ee_id IN  
    (  
        SELECT prd.ee_id  
        FROM   pr_result_dtl prd  
        WHERE  pay_period_group = NVL(#{payPeriodGroup}, prd.pay_period_group  
    )  
    AND prd.pay_period = #{payPeriod})  
    AND ejd.effective_date = pkg_slookup.fnc_ee_job_dtl_edate(ejd.ee_id, #{payToDate})  
    AND ejd.version_no = pkg_slookup.fnc_ee_job_dtl_mver(ejd.ee_id, ejd.effective_date)  
    AND EXISTS  
    (  
        SELECT  
            /*+ index(emt, pk_ee_employ_term)*/ 1  
        FROM ee_employ_term emt  
        WHERE emt.ee_id = ejd.ee_id  
        AND emt.effective_date = pkg_slookup.fnc_ee_employ_term_edate(emt.ee_id, #{payToDate})  
        AND emt.version_no = pkg_slookup.fnc_ee_employ_term_mver(emt.ee_id, emt.effective_date)  
        AND emt.ee_group = NVL(#{eeGroup}, emt.ee_group)  
        AND emt.pay_period_group= NVL(#{payPeriodGroup}, emt.pay_period_group)  
        AND emt.shift_type = NVL(#{shift}, emt.shift_type)  
        AND DECODE(emt.termination_date, NULL, 'N', 'Y') = #{terminateFlag}  
        <if test="termFromDate != null or termToDate != null">  
            AND NVL (emt.termination_date, TO_DATE ('1950-01-01', 'RRRR-MM-DD'))  
            BETWEEN NVL(#{termFromDate,jdbcType=DATE}, NVL(emt.termination_date, TO_DATE ('1950-01-01', 'RRRR-MM-DD')))  
            AND NVL (#{termToDate,jdbcType=DATE}, NVL(emt.termination_date, TO_DATE ('1950-01-01', 'RRRR-MM-DD')))  
        </if>  
        <!-- AND pkg_svalidate.fnc_restrict_ee_grp_rtn(#{usrId,jdbcType=VARCHAR}, emt.ee_id, emt.ee_group, #{progId}) = 'Y' -->  
        <!-- AND pkg_svalidate.fnc_spec_restrict_ee_grp_rtn(#{usrId,jdbcType=VARCHAR}, emt.ee_id, emt.ee_group, #{progId}, 'DEPT') = 'Y' -->    )  
)  
AND depart_id = NVL(#{departId}, depart_id)
```
## 作用
根据输入参数获取<font color="#ff0000">厂区</font>和<font color="#ff0000">部门</font>