`attendEmployeeList`是mybatis直接返回的list，被pagehelper的包装成了`Page`的实例，只有在list是Page实例的时候才能获得正确的总数。而这个函数返回的`collect`显然不是`Page`的实例，所以在外层调用这个函数时无法获取我们想要的总数。
```java
public List<AttendDto> selectAttendEmployee(AttendDto attendDto) {  
  
    //获取各个培训的出席员工信息数据  
    List<AttendDto> attendEmployeeList = attendMapper.selectAttendEmployeeList1(attendDto);  
    if(attendEmployeeList instanceof Page){  
        int i=1;  
    }  
  
    //优化导出时数据的显示  
    List<AttendDto> collect = attendEmployeeList.stream().map(e -> {  
        // 是否有协议判断  
        if (StringUtils.isNotEmpty(e.getRainingAgreement()) && e.getRainingAgreement().contains("Y")) {  
            e.setRainingAgreement("是");  
        } else if (StringUtils.isNotEmpty(e.getRainingAgreement()) && e.getRainingAgreement().contains("N")) {  
            e.setRainingAgreement("否");  
        }  
        // 状态判断  
        if (StringUtils.isNotEmpty(e.getAgreementStatus()) && e.getAgreementStatus().contains("Active")) {  
            e.setAgreementStatus("正在进行");  
        } else if (StringUtils.isNotEmpty(e.getAgreementStatus()) && e.getAgreementStatus().contains("Complete")) {  
            e.setAgreementStatus("已完成");  
        } else if (StringUtils.isNotEmpty(e.getAgreementStatus()) && e.getAgreementStatus().contains("Withdrawn")) {  
            e.setAgreementStatus("撤销");  
        }  
        return e;  
    }).collect(Collectors.toList());  
    if(collect instanceof Page){  
        int i=1;  
    }  
    return collect;  
}
```
## 修改方案
直接for循环`attendEmployeeList`，然后返回`attendEmployeeList`