---
layout: post
title:      "SQL in ArcGIS"
date:       2018-02-07 00:33:25 +0000
permalink:  sql_in_arcgis
---


Some things need to be keep in mind when using SQL in ArcGIS. 

Here's a few:


**Strings**

- Strings must always be enclosed in single quotation marks (not double) in queries. (E.g. CITY_NAME = 'Berlin')

If the string contains a single quotation mark you will first need to use the escape character ' (another single quotation mark).

For example:
FICTIONAL_NAME = 'Noah''s Ark'

- Strings in expressions are case sensitive except when querying personal geodatabase feature classes and tables. To make a case-insensitive search in file-based data sources like geodatabases or shapefiles, the SQL function UPPER or LOWER can be used to convert all values to the same case.

For example the following expression will select country names that is stored as either Germany or GERMANY:

UPPER(COUNTRY) = 'GERMANY'

(In other words it returns a string qual to the string expression with all lowercase characters converted to uppercase).

- || returns a character string that is the result of concatenating two or more string expressions:

FIRST_NAME || MIDDLE_NAME || LAST_NAME



**Expressions, operatiors** that can be used in Arc:

- IS NULL  / IS NOT NULL

E.g. POPULATION IS NULL / POPULATION IS NOT NULL

- Additionally when quering numbers these operators can be used:

equal (=)
not equal (<>)
greater than (>)
less than (<)
greater than or equal to (>=)
less than or equal to (<=)
BETWEEN / NOT BETWEEN

For calculations:
+
- 
*
/ 

- The ROUND function can be used to round a number to a certain decimal:

ROUND(SQM,0) = 100

- EXITSTS / NOT EXISTS
Exists returns true if at least one record is true to the statement

EXISTS (SELECT * FROM property_owners WHERE "LAST_NAME" = 'Jones')

- Logical Operators AND, OR, NOT:
Example: 
"AREA" > 1500 AND "ROOMS" > 2
"AREA" > 1500 OR "ROOMS" > 2
NOT "STATE_NAME" = 'Washington'

- The LIKE operatior:
"STATE_NAME" LIKE 'Miss%'

Reference:
http://pro.arcgis.com/en/pro-app/help/mapping/navigation/sql-reference-for-elements-used-in-query-expressions.htm#GUID-940733A1-D6D1-4200-B290-24CA2E1056D4
