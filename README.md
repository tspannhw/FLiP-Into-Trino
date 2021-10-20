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


```
