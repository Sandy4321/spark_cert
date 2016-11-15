## Certification spark 

## Programme Spark certification
### 1. Data Ingest
	- Import data from MySQL into HDFS using Sqoop
	- Export data to MySQL from HDFS using Sqoop
	- Change the delimiter and file format during Sqoop import
	- Streaming data into HDFS using Flume
	- Import and export data using the hdfs dfs commands
### 2. Data Analysis
	- Load and store data on HDFS using Spark
	- Join datasets with Spark
	- Calculate aggregate statistics using Spark
	- Filter data using Spark
	- Write a query producing sorted data using Spark
### 3. Transform, Stage, Store
	- Read or create a table in the Hive metastore
	- Extract an Avro schema using avro-tools
	- Create a table in Hive metastore using Avro file format and external schema file
	- Imporve query performance by creating partitioned tables in the Hive metastore
	- Evolve Avro schema by changing JSOn files


## Data Ingest

*  MySQL table available
```SQL
sqoop list-tables \
--connect jdbc:mysql://localhost/loudacre \
--username training \
--password training

sqoop list-databases \
--connect jdbc:mysql://localhost/loudacre \
--username training \
--password training
```

*  MySQL expression from sqoop
```SQL
sqoop eval \
--query "SELECT * FROM accounts LIMIT 5" \
--connect jdbc:mysql://localhost/loudacre \
--username training \
--password training
```

*  Import MySQL  from sqoop
```SQL
sqoop import \
--table accounts \
--warehouse-dir /loudacre/test_import \
--connect jdbc:mysql://localhost/loudacre \
--username training \
--password training
```

*  Change the delimiter and file format during Sqoop import
```SQL
sqoop import \
--table accounts \
--warehouse-dir /loudacre/test_import \
--fields-terminated-by '\t' \
--connect jdbc:mysql://localhost/loudacre \
--username training \
--password training
```


*  Export data to MySQL from HDFS using Sqoop
```SQL
sqoop export \
--connect jdbc:mysql://localhost/loudacre \
--username training \
--password training \
--update-mode allowinsert \
--table test_export \
--export-dir /loudacre/test_import/accounts \
--input-fields-terminated-by '\t'
```