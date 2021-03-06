## Recommended Configurations for KAP v2.1

The configuration files of KAP include following files: *kylin.properties*, *kylin_hive_conf.xml*, *kylin_job_conf.xml*, *kylin_job_conf_inmem.xml*. Among those files, *kylin.properties* is a major configuration parameter to control KAP's running behavior; *kylin_hive_conf.xml* is applied to configure parameters of interaction between KAP and Hive; *kylin_job_conf.xml* is applied to configure parameters of interaction between KAP and Hadoop cluster; *kylin_job_conf_inmem.xml is applied on in-memory* algorithm, *kylin_job_conf.xml* is applied on layer algorithm.

The following recommended configurations are classified according to the size of the cluster, system performance could be influenced by other external system parameters. Here our recommending configurations are based on experience.

*Sandbox* refers the testing environment for single machine sandbox virtual machine, dual core, 10GB internal storage, 10GB hard disk.

*Prod* represents recommended configuration for the production environment, usually, the Hadoop cluster consisting of at least 5 nodes, single machine 32 core, 128GB internal storage, 20TB hard disk.

### kylin.properties

| Properties Name                          | Sandbox    | Prod    |
| ---------------------------------------- | ---------- | ------- |
| kylin.hbase.default.compression.codec    | none       | snappy  |
| kylin.hbase.region.cut                   | 1          | 5       |
| kylin.hbase.hfile.size.gb                | 1          | 2       |
| kylin.hbase.region.count.min             | 1          | 1       |
| kylin.hbase.region.count.max             | 100        | 500     |
| kylin.job.concurrent.max.limit           | 10         | 20      |
| kylin.job.yarn.app.rest.check.interval.seconds | 10         | 10        |
| kylin.job.cubing.inmem.sampling.percent  | 100        | 100        |
| kylin.job.mapreduce.default.reduce.input.mb | 100        | 500     |
| kylin.job.mapreduce.max.reducer.number   | 100        | 500     |
| kylin.job.mapreduce.mapper.input.rows    | 200000     | 1000000 |
| kylin.job.step.timeout                   | 7200       | 7200        |
| kylin.cube.algorithm                     | auto       | auto        |
| kylin.cube.algorithm.auto.threshold      | 8          | 8        |
| kylin.cube.aggrgroup.max.combination     | 4096       | 4096        |
| kylin.dictionary.max.cardinality         | 5000000    | 5000000        |
| kylin.table.snapshot.max_mb              | 300        | 300        |
| kylin.query.scan.threshold               | 10000000   | 10000000        |
| kylin.query.mem.budget                   | 3221225472 | 3221225472        |
| kylin.query.coprocessor.mem.gb           | 3          | 3        |
| kylin.query.filter.derived_in.max        | 100        | 100        |


### kylin.properties for KAP Plus

| Properties Name                          | Sandbox | Prod   |
| ---------------------------------------- | ------- | ------ |
| kap.storage.columnar.conf.spark.driver.memory | 512m    | 8192m  |
| kap.storage.columnar.conf.spark.executor.memory | 512m    | 4096m  |
| kap.storage.columnar.conf.spark.yarn.am.memory | 512m    | 4096m  |
| kap.storage.columnar.conf.spark.executor.cores | 1       | 5      |
| kap.storage.columnar.conf.spark.executor.instances | 1       | 4      |
| kap.storage.columnar.page.compression    |         | SNAPPY |
| kap.storage.columnar.ii.spill.threshold.mb | 128     | 512    |




### kylin_hive_conf.xml

| Properties Name                          | Sandbox   | Prod                                     |
| ---------------------------------------- | --------- | ---------------------------------------- |
| dfs.replication                          | 2         | 2                                         |
| hive.exec.compress.output                | true      | true                                         |
| hive.auto.convert.join.noconditionaltask | true      | true                                         |
| hive.auto.convert.join.noconditionaltask.size | 100000000 | 100000000                                         |
| mapreduce.map.output.compress.codec      | N/A       | org.apache.hadoop.io.compress.SnappyCodec |
| mapreduce.output.fileoutputformat.compress.codec | N/A       | org.apache.hadoop.io.compress.SnappyCodec |
| mapreduce.output.fileoutputformat.compress.type | BLOCK     | BLOCK                                         |
| mapreduce.job.split.metainfo.maxsize     | -1        | -1                                         |

### kylin_job_conf.xml

| Properties Name                          | Sandbox | Prod                                     |
| ---------------------------------------- | ------- | ---------------------------------------- |
| mapreduce.job.split.metainfo.maxsize     | -1      | -1                                         |
| mapreduce.map.output.compress            | true    | true                                         |
| mapreduce.map.output.compress.codec      | N/A     | org.apache.hadoop.io.compress.SnappyCodec |
| mapreduce.output.fileoutputformat.compress | true    | true                                         |
| mapreduce.output.fileoutputformat.compress.codec | N/A     | org.apache.hadoop.io.compress.SnappyCodec |
| mapreduce.output.fileoutputformat.compress.type | BLOCK   | BLOCK                                         |
| mapreduce.job.max.split.locations        | 2000    | 2000                                         |
| dfs.replication                          | 2       | 2                                         |
| mapreduce.task.timeout                   | 3600000 | 3600000                                         |

### kylin_job_conf_inmem.xml

| Properties Name                          | Sandbox   | Prod                                     |
| ---------------------------------------- | --------- | ---------------------------------------- |
| mapreduce.job.split.metainfo.maxsize     | -1        | -1                                        |
| mapreduce.map.output.compress            | true      | true                                         |
| mapreduce.map.output.compress.codec      | N/A       | org.apache.hadoop.io.compress.SnappyCodec |
| mapreduce.output.fileoutputformat.compress | true      | true                                         |
| mapreduce.output.fileoutputformat.compress.codec | N/A       | org.apache.hadoop.io.compress.SnappyCodec |
| mapreduce.output.fileoutputformat.compress.type | BLOCK     | BLOCK                                         |
| mapreduce.job.max.split.locations        | 2000      | 2000                                         |
| dfs.replication                          | 2         | 2                                         |
| mapreduce.task.timeout                   | 7200000   | 7200000                                         |
| mapreduce.map.memory.mb                  | 3072      | 4096                                     |
| mapreduce.map.java.opts                  | -Xmx2700m | -Xmx3700m                                |
| mapreduce.task.io.sort.mb                | 200       | 200                                      |
