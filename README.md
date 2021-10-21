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


-- Drop table

-- DROP TABLE pulsar."public/default".iotjetsonjson;

CREATE TABLE pulsar."public/default".iotjetsonjson (
	camera varchar,
	cpu double,
	cputemp varchar,
	cputempf varchar,
	diskusage varchar,
	filename varchar,
	gputemp varchar,
	gputempf varchar,
	host varchar,
	host_name varchar,
	imageinput varchar,
	"ipaddress" varchar,
	macaddress varchar,
	memory double,
	networktime double,
	runtime varchar,
	systemtime varchar,
	te varchar,
	top1 varchar,
	top1pct double,
	"uuid" varchar,
	"__partition__" integer,
	"__event_time__" timestamp,
	"__publish_time__" timestamp,
	"__message_id__" varchar,
	"__sequence_id__" bigint,
	"__producer_name__" varchar,
	"__key__" varchar,
	"__properties__" varchar
);

CREATE TABLE pulsar."public/default".weathersink
(
 noNamespaceSchemaLocation varchar ,
 version varchar ,
 location  varchar , 
 observation_time  varchar , 
 credit  varchar , 
 credit_url  varchar , 
 image  varchar , 
 suggested_pickup  varchar , 
 suggested_pickup_period bigint,
 station_id  varchar , 
 latitude double, 
 longitude double, 
 observation_time_rfc822  varchar , 
 weather_string  varchar , 
 temperature_string varchar   ,
 temp_f DOUBLE, temp_c double, 
 relative_humidity bigint, 
 wind_string varchar    , 
 wind_dir  varchar , 
 wind_degrees bigint, 
 wind_mph double, 
 wind_gust_mph double, 
 wind_kt bigint,
 wind_gust_kt bigint, 
 pressure_string varchar   , 
 pressure_mb double, 
 pressure_in double, 
 dewpoint_string varchar    , 
 dewpoint_f double, 
 dewpoint_c double, 
 windchill_string varchar    ,
 windchill_f bigint, 
 windchill_c bigint, 
 visibility_mi double, 
 icon_url_base  varchar , 
 two_day_history_url  varchar , 
 icon_url_name  varchar , 
 ob_url  varchar , 
 disclaimer_url  varchar ,
 copyright_url  varchar , 
 privacy_policy_url  varchar 
)

```

## Consume Pulsar Topics From Console Client

```
bin/pulsar-client consume "persistent://public/default/iot3" -s "iot3reader" -n 0
bin/pulsar-client consume "persistent://public/default/iotjetsonjson" -s "iotjjreader" -n 0
```

## References

* https://pulsar.apache.org/docs/en/sql-deployment-configurations/
* https://pulsar.apache.org/docs/en/sql-getting-started/
* https://pulsar.apache.org/docs/en/sql-rest-api/
* https://pulsar.apache.org/docs/en/sql-overview/
* https://www.slideshare.net/streamnative/interactive-analytics-on-pulsar-with-pulsar-sql-pulsar-virtual-summit-europe-2021
* https://www.slideshare.net/streamnative/trino-a-ludicrously-fast-query-engine-pulsar-summit-na-2021
* https://www.slideshare.net/streamnative/interactive-querying-of-streams-using-apache-pulsarjerry-peng
* https://www.slideshare.net/streamnative/using-the-flipn-stack-for-edge-ai-flink-nifi-pulsar-pulsar-virtual-summit-europe-2021

## Pulsar SQL / PrestoSQL - Trino

![pulsar](https://pulsar.apache.org/docs/assets/pulsar-sql-arch-1.png)
