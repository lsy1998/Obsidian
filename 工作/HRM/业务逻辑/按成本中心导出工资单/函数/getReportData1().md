## 输入
```js
param,  
rowDataList,  
rowSumDataList,  
preRowWithoutSection,  
preRowWithSection,  
payPeriodDefn,  
grossSectionTotal,  
taxableSectionTotal,  
netPaymentSectionTotal,  
sectionTtlHseTaxableEmpr,  
sectionTtlHseTaxableEmpe,  
grossGrandTotal,  
netPaymentGrandTotal,  
taxableGrandTotal,  
grandTtlHseTaxableEmpe,  
grandTtlHseTaxableEmpr,  
grandSocialInsuranceEmpr,  
grandAccumulationFundEmpr,  
grandTotalBasicSalary,  
sectionTotalBasicSalary,  
deptCName,  
sectionId,  
beforeTaxPayrollTransId,  
afterTaxPayrollTransId,  
beforeTaxSectionCol,  
afterTaxSectionCol,  
beforeTaxTotalCol,  
afterTaxTotalCol,  
beforeTaxPayrollList,  
afterTaxPayrollList,  
beforeTaxColumnCount2,  
afterTaxColumnCount2,  
beforeTaxCount,  
afterTaxCount,  
grandHeadCount,  
numSectionItem,  
sectionHeadCount
```
1. 如果 `payPeriodDefn` 不为空
2. 获取厂区和部门的 <font color="#ff0000">organAndDepartList</font> 通过  [[resExtByCostCenterMapper.getOrganAndDepartList(param1)]]
3. 遍历 <font color="#ff0000">organAndDepartList</font>
4. 遍历过程中获取 <font color="#ff0000">teamDetailsList</font> 通过 [[resExtByCostCenterMapper.getTeamDetailsList(param1)]]
5. 遍历 <font color="#ff0000">teamDetailsList</font> 
6. 遍历过程中获取 <font color="#ff0000">employeeDetailsList</font> 通过  [[resExtByCostCenterMapper.getEmployeeDetailsList(param1)]]
7. 遍历 <font color="#ff0000">employeeDeatils</font> 
9. 遍历过程
	1. 将固定的表头加到 <font color="#92d050">addProperties</font>
	2. 获取<font color="#92d050"> salaryRate</font> 通过 [[resExtByCostCenterMapper.getSalaryRate(param1)]]
	3. 获取 <font color="#92d050">deptCName</font> 通过[[resExtByCostCenterMapper.getDeptName(DEPARTMENT_ID)]] 
	4. 将员工相关基础信息添加到 <font color="#92d050">addProperties</font> 
	5. 开始计算税前项，通过 [[resExtByCostCenterMapper.getTaxTransList(param1)]]获取<font color="#92d050">taxTransList</font>，判断税前项是不是在taxTransList中，是则将税前项目累加得到总金额；判断是不是收税项目，累加到taxable
	6. 将 <font color="#92d050">总金额</font> 加入 <font color="#92d050">addProperties</font>
	7. 开始结算税后项，通过[[resExtByCostCenterMapper.getTaxTransList(param1)]]获取 <font color="#92d050">taxTransList</font>，判断税后项是不是在taxTransList中，是则将税后项目累加到总金额得到工资净额；判断是不是收税项目，累加到taxable得到应税额
	8. 将<font color="#92d050">应税额</font>和<font color="#92d050">工资净额</font>加入<font color="#92d050">addProperties</font>
	9. 单独获取<font color="#92d050">Housing Fund Taxable(雇主)</font>通过[[resExtByCostCenterMapper.getEmprHousingTaxable(param1)]]
	10. 单独获取<font color="#92d050">Housing Fund Taxable(雇员)</font>通过[[resExtByCostCenterMapper.getEmpeHousingTaxable(param1)]]
	11. 单独获取<font color="#92d050">社保合计(雇主)</font>通过[[resExtByCostCenterMapper.getEmprSocialInsurance(param1)]]
	12. 单独获取<font color="#92d050">公积金合计(雇员)</font>通过[[resExtByCostCenterMapper.getEmprAccumulationFund(param1)]]