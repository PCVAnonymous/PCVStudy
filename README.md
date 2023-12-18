# Artifacts for "Understanding How configuration Affects Software by Interacting with Variables&Constants"


This repository includes the artifacts of the our paper: [Who is in Charge here? Understanding How configuration Affects Software by Interacting with Variables&Constants]

The repository includes the following artifacts:

* `Interaction cases`: 851 cases from ten large-scale projects (HBase, HDFS, Hive, Httpd, MapReduce, MySQL, Nginx, Postgres, Yarn, Zookeeper). 

* `Sampled parameters`: 705 parameters we sample from these ten projects.

## 1. Interaction Cases

We present an exhaustive collection of all studied cases categorized by interaction patterns, encompassing the four types  and seven patterns elucidated in Section 3:



### 1.1 Overview of Data Files
 
The following seven files correspond to the seven interaction patterns described in Section 3 and Table 3. Each of the file contains all the interaction cases belonging to its respective interaction type.

1. Parameters operate autonomously without entanglement with constants or variables:
  
   *  P.csv : (Section 3.1) Parameters work independently.

2. Parameters interact with constants. This category encompasses two code patterns: 
   
   *  C $\rightarrow$ P.csv : (Section 3.2) Parameters constrained by constants.

   *  P-C.csv: (Section 3.2) Parameters and constants take equivalent space.

3. Parameter interacts with Variable, manifesting in three distinctive code patterns:
   *  V $\rightarrow$ P.csv: (Section 3.2) Parameters is constrained by variables.

   *  P $\rightarrow$ V.csv: (Section 3.2) Variables is constrained by parameters.

   *  P-V.csv : (Section 3.3) Parameters and variables take equicalent place.

4. Parameters intricately interact with both constants and variables, exemplified by a singular code pattern:
   
   *  P&amp;C&amp;V.csv : (Section 3.4) Parameters, constants and variables take equicalent place.
 
### 1.2 Attributes of Each CSV Row

Herein lies an explication of each row. Each of the row contains one code snippet of parameter. Noteworthy elements incorporated in each row comprise the code pattern (Section 3, anwsering to RQ1 and RQ2), effect on software (Section 4, anwsering to RQ3) and potential problem (Section 5, anwsering to RQ4) of the interaction code.

1. Base information of this code snippet (Section 3, RQ1 and RQ2).
   *  Software : Software name.

   *  Parameter : Parameter name. 
   
   *  Code Snippet : Interaction code snippet of the corresponding parameter.
   
   *  Code Pattern : Code pattern of the interaction.

2. Effect on software at runtime (Section4, RQ3).
   
   *  Overall Impact : Overall impact of this interaction code on software, e.g., performance, reliability and functionality and others (Section 4.1). 
   
   *  Effect on Software Behavior : How this interaction code affects software behaviors (Section 4.2).
	
   *  How to Control Software Behavior : The way of controlling software behavior obtained based on the issues and semantics. It is corresponding to the classfication illustrated in Figure 4 (Section 4.2, Figure 4).
   
   *  Special Effect on Software : Specail effect of this interaction code snippet on software, i.e., how this interaction affect resource utilization (Section 4.2).

3. Potential problems (Section 5, RQ4).
   
   *  Bad consequences : Bad consequences this interaction may lead to software, including runtime error, performance degradation and unexpected result (Section 5.1).
	  
   *  Log Information : Log information of this interaction code (Section 5.1).

   *  On-the-fly Update ：If this parameter support on-the-fly update (Section 5.1).

   *  The "Crisis" Behind Specific Interactions : Potential problem of the interaction (Section 5.2).

Take `hbase.region.store.parallel.put.print.threshold` for an example. This data row contain the following information:

hbase (software), hbase.region.store.parallel.put.print.threshold (parameter), 

      if (this.currentParallelPutCount.getAndIncrement() > this.parallelPutCountPrintThreshold) {
        LOG.trace("tableName={}, encodedName={}, columnFamilyName={} is too busy!",
          this.getTableName(), this.getRegionInfo().getEncodedName(), this.getColumnFamilyName());
      } (code snippet)

P→V (code pattern), Performance (overall impact), Workload Adaption (effect on software behavior), Resource Limitation (how to control software behavior), Prevent excessive resource utilization (Special Effect on Software), Performance Degradation (Bad consequences), 

      LOG.trace("tableName={}, encodedName={}, columnFamilyName={} is too busy!",
          this.getTableName(), this.getRegionInfo().getEncodedName(), this.getColumnFamilyName()); (log information)

no (On-the-fly Update), Inappropriate threshold in P→V (The "Crisis" Behind Specific Interactions).

## 2. Sampled Parameters

There are totally 705 parameters that we sample from ten software (Section 2).

### 2.1 Attributes of Each CSV Column

Each file contains all the parameters sampled from the corresponding software. For instance, HBase.csv containts 35 parameters.

   *  Parameter ：Parameter name.  
   
   *  Type ：The interaction type descriped in Section 3.
   
   *  On-the-fly Update ：If this parameter support on-the-fly update.

Take `binlog_order_commits` for an example: binlog_order_commits, P&V, yes.
