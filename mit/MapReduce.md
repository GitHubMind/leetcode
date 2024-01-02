# MIT 6.824  Lecture1

## 1.1 Introduction

    Distributed system

+ sharing
+ increase capacity tough parallelism 
+ tolerate faults
+ achiveve security via isolation(I don't think it )

## history
   
+ The distributed systems is come form 1980s
+ Dns,GFS,Email,mapstruct  is distributed system

##  Diffculties

+ newowrk partition -> divsion of computer /network 
+ many concurrent part
+ realize the performance benefits ( how ?)
+ how to make KPIS for it?(think self)

## Support the underlying infrastructure distribute system content

+ strong consistency
+ compuation
+ Comminication
RPC:
+ utmost once 
+ at most once
+ at least once
+ exactly once


## Important!

> fault tolerance
>> availabitity  (p99 ->99% of the requests should be faster than given latency， in other words only 1% of the request are allened to be slower)
>> consistenncy
>> performance


## mapreduce

 I think it is good idea aboue program model .It keen at high-storage data processing. map -> reduce -> combine
