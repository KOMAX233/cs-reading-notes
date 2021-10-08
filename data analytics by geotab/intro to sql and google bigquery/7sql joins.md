# SQL JOIN

- ## syntax:
  ```
  SELECT  <column names> 
  FROM `BIG.QUERY.TABLE1` 
  Join TYPE  `BIG.QUERY.TABLE2` on (column names)
  WHERE <conditional statements>
  ```
- ## INNER JOIN
  join 2 tables based on common info (intersection)
  ![](https://everpath-course-content.s3-accelerate.amazonaws.com/instructor%2Fjoyeetarahman_geotab_com_nc2pmg%2Fpublic%2F1607104813%2FScreenshot+2020-12-04+at+12.45.29+PM.1607104813372.png)
  ```
  SELECT Table1.row
  FROM Table_1
  INNER JOIN Table_2 ON Table_2.row = Table_2.row;
  ```
  
- ## LEFT/RIGHT (OUTER) JOIN
  return all rows from the left and matching rows from right ![](https://everpath-course-content.s3-accelerate.amazonaws.com/instructor%2Fjoyeetarahman_geotab_com_nc2pmg%2Fpublic%2F1607477694%2FScreenshot+2020-12-08+at+8.33.50+PM.1607477694184.png)
  
- ## FULL (OUTER) JOIN
  return all rows from left and right, and give NULL if no matching
  ```
  SELECT country_name, city_name
  FROM Cities
  FULL OUTER JOIN Countries ON Countries.country_id = Cities.country_id;
  ```
  
  
- ## CROSS JOIN
  combine rows in first table to rows in second table
  
  
![](https://everpath-course-content.s3-accelerate.amazonaws.com/instructor%2Fjoyeetarahman_geotab_com_nc2pmg%2Fpublic%2F1607101498%2FScreenshot+2020-12-04+at+11.56.10+AM.1607101498686.png)
