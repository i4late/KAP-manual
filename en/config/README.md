## Configuration File
After deploying KAP on cluster, we need configure KAP to fit into Hadoop cluster working with Apache Hadoop, Apache HBase and Aapche Hive. Performance tunning also depends on these configuration files. 
These configuration files locates in ${KYLIN_HOME}/conf directory. They are listed bellow:
###	kylin.properties
This is the global configuration file, all configurations about KAP are in this file. Detailed explanations are on the next page.
###	kylin\_hive\_conf.xml
Apache Hive related configurations are in this file. They're used in first step of cube building process, generating intermediate table.
###	kylin\_job\_conf\_inmem.xml
This is Map Reduce configuration file used in cube building process when Fast Cubing algorithm chosen.
###	kylin\_job\_conf.xml
This is Map Reduce configuration file used in cube building process when Layer Cubing algorithm chosen.