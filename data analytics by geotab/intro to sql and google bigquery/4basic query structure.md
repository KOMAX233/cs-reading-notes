# basic queries

## statement vs. clauses

### - statement: query

e.g. select statement

; is the statement terminator

#### SQL includes DDL (data definiton language) & DML (data manipulation language) statements

#### DDL:
- create
- alter
- drop
- truncate
- rename

#### DML: 
- select
- update
- insert
- delete
- merge
- lock table


### - clause: condition of the statement
1. from: choose and join tables to get base data
2. where: filter base data
3. group by: aggregate base data
4. having: filter
5. select: return final data (distinct)
6. order by: sort final data (columnName asc/desc)
7. limit: limit returned data to a row count (#)




## row/record: collection of attributes/variables representing single entities

## table: collection of rows with the same attributes

## write basic SQL:

- select
  * column1, 
  * (as newname1) 
  * column2, 
  * ...
  - `*` for put all columns
  - 
- from
  * tablename 
- (where)
  * condition1
  * column1 > 1 and column2 < 1
  * column1 > 1 or column2 < 1
- (order by)
  * column1 asc(default)/desc
