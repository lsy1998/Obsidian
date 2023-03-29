## logs

```
Caused by: io.lettuce.core.RedisCommandTimeoutException: io.lettuce.core.RedisCommandTimeoutException: Command timed out after 10 second(s)  
    at io.lettuce.core.LettuceFutures.awaitOrCancel(LettuceFutures.java:126)  
    at io.lettuce.core.FutureSyncInvocationHandler.handleInvocation(FutureSyncInvocationHandler.java:69)  
    at io.lettuce.core.internal.AbstractInvocationHandler.invoke(AbstractInvocationHandler.java:80)  
    at com.sun.proxy.$Proxy123.get(Unknown Source)  
    at org.springframework.data.redis.connection.lettuce.LettuceStringCommands.get(LettuceStringCommands.java:66)  
    ... 65 common frames omitted  
Caused by: io.lettuce.core.RedisCommandTimeoutException: Command timed out after 10 second(s)  
    at io.lettuce.core.ExceptionFactory.createTimeoutException(ExceptionFactory.java:51)  
    at io.lettuce.core.protocol.CommandExpiryWriter.lambda$potentiallyExpire$0(CommandExpiryWriter.java:167)  
    at io.netty.util.concurrent.PromiseTask.runTask(PromiseTask.java:98)  
    at io.netty.util.concurrent.ScheduledFutureTask.run(ScheduledFutureTask.java:170)  
    at io.netty.util.concurrent.DefaultEventExecutor.run(DefaultEventExecutor.java:66)  
    at io.netty.util.concurrent.SingleThreadEventExecutor$4.run(SingleThreadEventExecutor.java:989)  
    at io.netty.util.internal.ThreadExecutorMap$2.run(ThreadExecutorMap.java:74)  
    at io.netty.util.concurrent.FastThreadLocalRunnable.run(FastThreadLocalRunnable.java:30)  
    ... 1 common frames omitted  
14:39:38.397 [http-nio-8088-exec-2] ERROR c.a.d.f.s.StatFilter - [internalAfterStatementExecute,487] - slow sql 53408 millis. SELECT  
        a.organization_id,  
        a.name,  
        a.created_by,  
        to_char(a.created_date, 'YYYY-MM-dd HH24:MI:SS')         AS created_date,  
        a.modified_by,  
        to_char(a.modified_date, 'YYYY-MM-dd HH24:MI:SS')        AS modified_date  
        FROM  
        organization_defn a  
         WHERE 1=1   
        ORDER BY  
        a.organization_id[]  
14:39:42.083 [http-nio-8088-exec-2] DEBUG c.s.p.e.m.O.queryDatalist - [debug,137] - <==      Total: 9  
14:39:51.013 [QuartzScheduler_HRMScheduler-NON_CLUSTERED_MisfireHandler] ERROR c.a.d.f.s.StatFilter - [internalAfterStatementExecute,487] - slow sql 24839 millis. SELECT COUNT(TRIGGER_NAME) FROM QRTZ_TRIGGERS WHERE SCHED_NAME = 'HRMScheduler' AND NOT (MISFIRE_INSTR = -1) AND NEXT_FIRE_TIME < ? AND TRIGGER_STATE = ?[1680071954174,"WAITING"]  
14:39:49.345 [http-nio-8088-exec-2] DEBUG c.s.p.e.m.D.queryDatalist - [debug,137] - ==>  Preparing: SELECT a.depart_id, a.e_name, a.c_name, a.created_by, to_char(a.created_date, 'YYYY-MM-dd HH24:MI:SS') AS created_date, a.modified_by, to_char(a.modified_date, 'YYYY-MM-dd HH24:MI:SS') AS modified_date FROM department_defn a WHERE 1=1 ORDER BY a.depart_id  
14:39:49.345 [HRMScheduler_QuartzSchedulerThread] ERROR c.a.d.f.s.StatFilter - [internalAfterStatementExecute,487] - slow sql 15929 millis. SELECT TRIGGER_NAME, TRIGGER_GROUP, NEXT_FIRE_TIME, PRIORITY FROM QRTZ_TRIGGERS WHERE SCHED_NAME = 'HRMScheduler' AND TRIGGER_STATE = ? AND NEXT_FIRE_TIME <= ? AND (MISFIRE_INSTR = -1 OR (MISFIRE_INSTR != -1 AND NEXT_FIRE_TIME >= ?)) ORDER BY NEXT_FIRE_TIME ASC, PRIORITY DESC["WAITING",1680072003415,1680071961415]  
Exception in thread "http-nio-8088-Acceptor" java.lang.OutOfMemoryError: Java heap space  
14:49:20.866 [http-nio-8088-exec-14] ERROR o.a.c.h.Http11NioProtocol - [log,175] - Failed to complete processing of a request  
java.lang.OutOfMemoryError: Java heap space  
14:50:09.854 [http-nio-8088-exec-17] ERROR o.a.c.h.Http11NioProtocol - [log,175] - Failed to complete processing of a request  
java.lang.OutOfMemoryError: Java heap space  
14:47:47.237 [http-nio-8088-exec-16] ERROR o.a.c.h.Http11NioProtocol - [log,175] - Failed to complete processing of a request  
java.lang.OutOfMemoryError: Java heap space  
    at java.nio.HeapByteBuffer.<init>(HeapByteBuffer.java:57)  
    at java.nio.ByteBuffer.allocate(ByteBuffer.java:335)  
    at org.apache.coyote.http11.Http11InputBuffer.init(Http11InputBuffer.java:746)  
    at org.apache.coyote.http11.Http11Processor.setSocketWrapper(Http11Processor.java:475)  
    at org.apache.coyote.http11.Http11Processor.service(Http11Processor.java:247)  
    at org.apache.coyote.AbstractProcessorLight.process(AbstractProcessorLight.java:65)  
    at org.apache.coyote.AbstractProtocol$ConnectionHandler.process(AbstractProtocol.java:868)  
    at org.apache.tomcat.util.net.NioEndpoint$SocketProcessor.doRun(NioEndpoint.java:1590)  
    at org.apache.tomcat.util.net.SocketProcessorBase.run(SocketProcessorBase.java:49)  
    at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149)  
    at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624)  
    at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:61)  
    at java.lang.Thread.run(Thread.java:748)  
14:51:58.258 [http-nio-8088-exec-22] ERROR o.a.c.h.Http11NioProtocol - [log,175] - Failed to complete processing of a request  
java.lang.OutOfMemoryError: Java heap space  
2023-03-29 14:55:02  
Full thread dump Java HotSpot(TM) 64-Bit Server VM (25.311-b11 mixed mode):

"http-nio-8088-exec-25" #83 daemon prio=5 os_prio=0 tid=0x00007fe0304ec800 nid=0x7b87 runnable [0x0000000000000000]  
   java.lang.Thread.State: RUNNABLE

"http-nio-8088-exec-23" #82 daemon prio=5 os_prio=0 tid=0x00007fe068050800 nid=0xc14 runnable [0x00007fdfdfd97000]  
   java.lang.Thread.State: RUNNABLE  
    at java.util.Arrays.copyOf(Arrays.java:3332)  
    at java.lang.AbstractStringBuilder.ensureCapacityInternal(AbstractStringBuilder.java:124)  
    at java.lang.AbstractStringBuilder.append(AbstractStringBuilder.java:448)  
    at java.lang.StringBuilder.append(StringBuilder.java:136)  
    at java.lang.ThreadGroup.uncaughtException(ThreadGroup.java:1060)  
    at java.lang.ThreadGroup.uncaughtException(ThreadGroup.java:1052)  
    at java.lang.Thread.dispatchUncaughtException(Thread.java:1959)

"http-nio-8088-exec-22" #81 daemon prio=5 os_prio=0 tid=0x00007fe06804e000 nid=0x1ed95 runnable [0x00007fdfe33f2000]  
   java.lang.Thread.State: RUNNABLE  
    at org.apache.tomcat.util.threads.TaskThreadFactory.newThread(TaskThreadFactory.java:48)  
    at java.util.concurrent.ThreadPoolExecutor$Worker.<init>(ThreadPoolExecutor.java:619)  
    at java.util.concurrent.ThreadPoolExecutor.addWorker(ThreadPoolExecutor.java:932)  
    at java.util.concurrent.ThreadPoolExecutor.processWorkerExit(ThreadPoolExecutor.java:1025)  
    at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1167)  
    at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624)  
    at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:61)  
    at java.lang.Thread.run(Thread.java:748)
```
## 原因
![[Pasted image 20230329151919.png]]
内存设置过小导致溢出

## 问题思路
1.  tomcat 是否挂掉了，如果挂掉了，一般就是内存满了，或者CPU飚高了。 一般调高内存大小，然后再重启
2.  tomcat 没挂，CPU和内存都没飚高，那么就看下数据库和其他IO，是否有问题。
一般都是先让用户能用，一般调高内存大小，然后再重启