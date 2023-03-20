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
8. 遍历过程
	1. 获取 <font color="#ff0000">salaryRate</font> 通过 [[resExtByCostCenterMapper.getSalaryRate(param1)]]