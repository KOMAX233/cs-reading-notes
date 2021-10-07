# SQL functions
many input args n -> function -> one output result value
- ## limit clause
  - limit the result of a query to a number of results 
  - display n results only
  - save return time
  - `limit n`
- ## operators (with where) (return NULL unless specified)
  - ### logical operator
    - and 
    - or 
    - not
  - ### arithmetic operator
    - \+
    - \-
    - \*
    - \/
  - ### comparison operator
    - return true/false
    - \>
    - \<
    - \>=
    - \<=
    - \!=
    - between
      - search in certain range
      - e.g. `where column1 between 1 and 5`
    - like 
      - similar to `where`
      - search specific info
    - in 
      - similar to `where`
      - search multiple specific values
      - e.g. `where column1 in ('A', 'B', 'C')`
- ## IS (NOT) NULL operator
  - lack of data
  - identify null records
  - used with `where`
- ## wildcard operator %
  - match anything before '%' symbol
  - e.g. `where column1 like 'ABC%`: match records starting with 'ABC'

- ## conditional statements
  - if(condition, true_result, false_result):
    - boolean expression
    - true -> true result
    - false -> false result
  - ifNull(expression, result):
    - null -> return results
    - not null -> do not return results
  - coaleasce(expression, result):
    - similar to `ifnull()`
    - can take multiple args
    - null -> return results
    - not null -> do not return
  - case:
    - check all conditions for all rows
    - true -> return result
    - no condition is true -> return else_result
    - can end with `end` and then add `as newName`
    ``` 
    case
    when column=condition1 then result1
    when column=condition2 then result2
    else column=condition3 then result3
    end as columnName 
    ```
- ## string functions
  - manipulate strings and queries
  - `substr(value, starting position, length>0)`: extract substring
  - `concat(column1, ' KM', ...)`: join 2/more strings
  - `length`: return length of a string (trailing space not included / leading space included)
  - `lower/upper(column1)`: convert a column to lower/uppercase
  - `ltrim/rtrim/trim`: remove leading/trailing characters
  - `split`: split string by delimiter

- ## subqueries
  - queries inside queries (recursion?)
  - they are not temporary tables but actual views
  - express complex sequential operations
  - can be chained
  - must have `order by` if using `limit`
  - using `with` syntax
  - subqueries used more memory than allocated will make GBQ crash
- ## common table expressions (CTE)
  - used before actual/main query
  - used for: 
    - temporary table's name
    - list of column names
    - query expression or statement such as select
  - `with`:
    - give subquery block a name (subquery refactoring)
    ```
      with tableNewName as (
        select .. 
        from ..
        where ..
      )
      select ... 
      from tableNewName
      where ...
     ```
  - diff: CTE vs. subqueries
    - recursive vs. cannot be recursive
    - reusable vs. not reusable
    - readable vs. not as readable
    - must be named vs. not required to be named
    - cannot be used in `where` vs. can be used in `where`
    - cannot be used as columns vs. can be used as columns
- ## datetime functions
  - 2 integers: date + time
  - `extract(part from timestamp)`: return `part` from the `timestamp`
  - `timestamp_diff(timestamp expression a, timestamp expression b, interval)`: return the number of intervals between a and b
  - `date_sub(Date Expression , interval N date_part)`: subtract the interval `N date_part` from `date`
    - `current_date()` : get today's date
  - `Format_datetime(format_string, Datetime Expression)`: format datetime by [format string](https://cloud.google.com/bigquery/docs/reference/standard-sql/datetime_functions#supported_format_elements_for_datetime)
  - `Format_date(format_string, Date Expression)`: format date by [format string](https://cloud.google.com/bigquery/docs/reference/standard-sql/date_functions#supported_format_elements_for_date)
  - `date(Date Expression)`: format to a date object
- ## comment
  - inline: `#` or `--`
  - multiline: `/* */`
