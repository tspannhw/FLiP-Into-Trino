## FLiP-Into-Trino

FLiP into Trino.    Flink Pulsar Trino


## Pulsar SQL (Trino/Presto)


## Query Pulsar metrics / system

```
presto> SELECT * FROM system.runtime.nodes;
               node_id                |         http_uri         | node_version | coordinator | state  
--------------------------------------+--------------------------+--------------+-------------+--------
 ffffffff-ffff-ffff-ffff-ffffffffffff | http://192.168.1.70:8081 | testversion  | true        | active 
(1 row)

Query 20211020_194020_00000_98jf6, FINISHED, 1 node
Splits: 17 total, 17 done (100.00%)
0:04 [1 rows, 78B] [0 rows/s, 21B/s]


show catalogs;

show schemas in pulsar;

show tables in pulsar."public/default";

select * from pulsar."public/default"."weather";

show schemas in system;

show tables in system."metadata";

SELECT COUNT(*) AS number_of_messages 
FROM pulsar."public/default".iotjetsonjson;

select * from pulsar."public/default".iotjetsonjson;

select * from pulsar."public/default".generator_test;

select count(*) from pulsar."public/default".generator_test;

presto> show schemas in pulsar;
       Schema       
--------------------
 information_schema 
 public/default     
 public/functions   
 pulsar/system      
 sample/ns1         
(5 rows)


```

# Table Built with a Schema

```
presto> describe pulsar."public/default".iotjetsonjson;
      Column       |   Type    | Extra |                                   Comment                                   
-------------------+-----------+-------+-----------------------------------------------------------------------------
 camera            | varchar   |       | ["null","string"]                                                           
 cpu               | double    |       | "double"                                                                    
 cputemp           | varchar   |       | ["null","string"]                                                           
 cputempf          | varchar   |       | ["null","string"]                                                           
 diskusage         | varchar   |       | ["null","string"]                                                           
 filename          | varchar   |       | ["null","string"]                                                           
 gputemp           | varchar   |       | ["null","string"]                                                           
 gputempf          | varchar   |       | ["null","string"]                                                           
 host              | varchar   |       | ["null","string"]                                                           
 host_name         | varchar   |       | ["null","string"]                                                           
 imageinput        | varchar   |       | ["null","string"]                                                           
 ipaddress         | varchar   |       | ["null","string"]                                                           
 macaddress        | varchar   |       | ["null","string"]                                                           
 memory            | double    |       | "double"                                                                    
 networktime       | double    |       | "double"                                                                    
 runtime           | varchar   |       | ["null","string"]                                                           
 systemtime        | varchar   |       | ["null","string"]                                                           
 te                | varchar   |       | ["null","string"]                                                           
 top1              | varchar   |       | ["null","string"]                                                           
 top1pct           | double    |       | "double"                                                                    
 uuid              | varchar   |       | ["null","string"]                                                           
 __partition__     | integer   |       | The partition number which the message belongs to                           
 __event_time__    | timestamp |       | Application defined timestamp in milliseconds of when the event occurred    
 __publish_time__  | timestamp |       | The timestamp in milliseconds of when event as published                    
 __message_id__    | varchar   |       | The message ID of the message used to generate this row                     
 __sequence_id__   | bigint    |       | The sequence ID of the message used to generate this row                    
 __producer_name__ | varchar   |       | The name of the producer that publish the message used to generate this row 
 __key__           | varchar   |       | The partition key for the topic                                             
 __properties__    | varchar   |       | User defined properties                                                     
(29 rows)

```
