由于经常会再oracle中获取当月的第一天/后一天/上一天/最后一天/上个月这一天，所以整理出下面的oracle获取日期大全出来，有什么更好的建议可以留言补充一下。
|日期说明	|oracle语句（假设现在是2018-11-28 11:11:11）|	返回日期|
|-|-|-|
|当月第一天	|select trunc(sysdate, ‘mm’) from dual	|2018-11-1|
|当年第一天	|select trunc(sysdate,‘yy’) from dual	|2018-1-1|
|当前年月日	|select trunc(sysdate,‘dd’) from dual	|2018-11-28|
|当年第一天	|select trunc(sysdate,‘yyyy’) from dual	|2018-1-1|
|当前星期的第一天 （也就是星期天）	|select trunc(sysdate,‘d’) from dual	|2018-11-28|
|当前日期	|select trunc(sysdate) from dual	|2018-11-28|
|当前时间（准确到小时）	|select trunc(sysdate, ‘hh’) from dual	|2018-11-28 11:00:00|
|当前时间（准确到分钟）	|select to_char(trunc(sysdate, ‘mi’),‘yyyy-MM-dd HH:mm:ss’) from dual	|2018-11-28 11:11:00|
|前一天的日期|	select TRUNC(SYSDATE - 1) from dual	|2018-11-27|
|前一个月的日期	|select add_months(trunc(sysdate),-1) from dual	|2018-10-28|
|后一个月的日期	|select add_months(trunc(sysdate),1) from dual	|2018-12-28|
|本月最后一天	|select to_char(last_day(sysdate), ‘yyyy-mm-dd’) from dual	|2018-11-30|
## TRUNC()
trunc()函数返回以指定元素格式截去一部分的日期值，或者直接对数字格式的数据进行截断。![[Pasted image 20230406095546.png]]