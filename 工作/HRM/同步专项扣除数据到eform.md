
1. 定时执行[[DBMS_JOB$_142]]

2. 调用[[PRC_SYNC_EPAYSLIP_BY_SITE]]

3. 调用[[PRC_SYNC_EPAYSLIP_BY_PAY_GROUP]]     

4. 调用[[FNC_GEN_EPAYSLIP_BY_EE]]

5. 调用[[FNC_GEN_SPEC_TAX_DEDUCT_AMT]] 

6. 通过dblink将数据插入eform数据库 [[hr_ess_spec_tax_deduct_dtl]]

```sql
CURSOR cur_pr_spec_tax_deduct_dtl (piv_ee_id            IN VARCHAR2,
                                           piv_pay_period       IN VARCHAR2) IS
            SELECT
                pstdd.pay_period, 
                pstdd.ee_id, 
                pstdd.category_id, 
                tsdcd.description, 
                pstdd.deduct_amount
            FROM    
                pr_spec_tax_deduct_dtl pstdd, 
                tx_spec_deduct_category_defn tsdcd
            WHERE
                pstdd.category_id        = tsdcd.category_id     AND
                pstdd.ee_id              = piv_ee_id             AND
                pstdd.pay_period         = piv_pay_period
           ORDER BY pstdd.category_id;

......

FOR rec_pr_spec_tax_deduct_dtl IN cur_pr_spec_tax_deduct_dtl (piv_ee_id,piv_pay_period) LOOP
        
            -- 3.1. Encrypt Data
            BEGIN
                v_encrypted_deduct_amt := pkg_eform.fnc_encrypt_data(rec_pr_spec_tax_deduct_dtl.deduct_amount, v_key);
                v_encrypted_catecory_desc := pkg_eform.fnc_encrypt_data(rec_pr_spec_tax_deduct_dtl.description, v_key);
            EXCEPTION
                WHEN OTHERS THEN
                    v_log_type   := c_error;
                    v_log_msg    := c_package_name||'.FNC_GEN_SPEC_TAX_DEDUCT_AMT [3]: '||
                                    'Failed to Encrypt Deductible Amount. ' || 
                                    '[ee_id:'||piv_ee_id||']';
                RAISE user_def_err;
            END;
            
            -- 3.2. INSERT Itemized Special Tax Deductible Amount
            BEGIN
                INSERT INTO hr_ess_spec_tax_deduct_dtl@DBL_PSG_EFORM.WORLD(
                    pay_period, 
                    ee_id, 
                    category_id, 
                    category_description,
                    deduct_amount,
                    synchronized_by,
                    synchronized_date
                ) VALUES (
                    rec_pr_spec_tax_deduct_dtl.pay_period,
                    rec_pr_spec_tax_deduct_dtl.ee_id,
                    rec_pr_spec_tax_deduct_dtl.category_id,
                    v_encrypted_catecory_desc,
                    v_encrypted_deduct_amt,
                    piv_opr_user_id,
                    SYSDATE
                );
                
            EXCEPTION
                WHEN DUP_VAL_ON_INDEX THEN
                    v_log_type   := c_error;
                    v_log_msg    := c_package_name||'.FNC_GEN_SPEC_TAX_DEDUCT_AMT [4]: '||
                                    'Duplicate payslip detail entry. '||
                                    '[ee_id:'||piv_ee_id||',pay_period:'||piv_pay_period||',payroll_trans_id:'||rec_pr_spec_tax_deduct_dtl.category_id;
                WHEN OTHERS THEN
                    v_log_type   := c_error;
                    v_log_msg    := c_package_name||'.FNC_GEN_SPEC_TAX_DEDUCT_AMT [5]: '||
                                    'Failed to insert Itemized Special Tax Deductible Amount. ' || 
                                    '[ee_id:'||piv_ee_id||',pay_period:'||piv_pay_period||',payroll_trans_id:'||rec_pr_spec_tax_deduct_dtl.category_id;
                RAISE user_def_err;
            END;
                
        END LOOP;
```
