- ## tables
  - store related data with same column structure
  - record/row
  - 3 basic tables:
    1. standard tables
      - single table
      - can be appended to or overwritten
      - all rows are scanned in queries
    2. date-sharded tables
      - consist of tables ending in `_YYYYMMDD` or `YYYYMMDD`
      - grouped in UI
      - actually separate tables
      ```sql
      SELECT ColumnName1, ColumnName2
      FROM TableName
      WHERE _TABLE_SUFFIX = '20180501'
      ```
    3. partitioned tables
      - single table in UI
      - exist as single table
      - datais partitioned in memory by ingestion date
      - pesudo-column `_PARTITIONTIME` splits data by ingestion date
      ```sql
      SELECT ColumnName1, ColumnName2
      FROM TableName
      WHERE _PARTITIONTIME = '2018050'
      ```
    partitioned vs. sharded tables
    - partitioned preferred:
      - exist as single table
      - a set of schema descriptions and table tags to manage
      - data compliance easily checked
      - table, metadata includes all related data
      - ingested data automatically appended
      - can force a `_partitiontime` in `where`
- ## query issues with large tables solution:
  - reduce data requirements
  - distribute size-based limit
  - hash/mod: split into parallel
  - dataflow
  - reduce data size
  - remove unnecesary order by
  - further partition
  - sample from data subsets
  - \_TABLE_SUFFIX \ for date sharded table
  - \_PARTITIONTIME \ for partitioned table
  - Do not use SELECT * by default
  - columns in WHERE, GROUP BY, and ORDER BY clauses are all processed
- ## journey of a query
  - board by google
- ## how GBQ calculate analysis cost/size?
  - columnar database: stores date in columns not a big table
  - unused column will be ignored by GBQ
  - all used columns in the queries added to cost (regardless of whether in selet clause)

- ## temporary functions is a type of user defined functions (UDF)
  - temporary function syntax:
    ```sql
    CREATE [OR REPLACE] {TEMPORARY | TEMP} FUNCTION [IF NOT EXISTS]
    function_name
    ([named_parameter[, ...]])
    [RETURNS data_type]
    { sql_function_definition }
    ```
- ## spacial reference data
  - geohash to determine location
  - timezone stored in geohash timezone 
  - column
- ## sql loop
  - Looping Structures / Iterative control structures
  - used to execute a single command or a set of statements repeatedly
  1. LOOP statement:
    - repeats until `BREAK` or `LEAVE`
    - separated using the semicolons;
    - syntax:
      ```sql
      LOOP
        sql_statements
      END LOOP; 
      ```
  2. WHILE Loop statement ![](https://everpath-course-content.s3-accelerate.amazonaws.com/instructor%2Fjoyeetarahman_geotab_com_nc2pmg%2Fpublic%2F1608093988%2Fflow-chart-of-the-sql-while-loop-1.1608093987036.png):
    - syntax:
      ```sql
      DECLARE variable
      WHILE boolean_expression DO
           sql_statements
      END LOOP; 
      ```
      
