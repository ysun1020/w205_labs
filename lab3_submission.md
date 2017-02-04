#Lab 3 Submission 
## Yifan Sun

Q1: List the execution time of the weblog aggregation query for Hive, SparkSQL, and SparkSQL on Parquet.

Execution Time for Hive: 117.583 seconds
Execution time for SparkSQL: 30.97 seconds
Execution time for SparkSQL on Parquet: 8.655 seconds 

Q2: How many jobs does Hive launch? Does SparkSQL launch jobs?

Hive launches 2 jobs for the aggregation function, SparkSQL does not launch jobs. 

Q3: Write a query which joins weblogs_parquet to user_info and counts the top 5 locations. List the locations.

```sql
SELECT ui.location, COUNT(DISTINCT wb.user_id) AS log_count
	FROM weblogs_parquet wb JOIN user_info ui 
	ON wb.user_id = ui.user_id
	GROUP BY ui.location
	ORDER BY log_count DESC 
	LIMIT 5;
```
Top 5 locations are: 

| Location		| Count 	|
|-------------|---------|
|	Hamilton			|	19			|
|	Axis					|	18			|
|	Hazel Green	|	16			|
|	La Fayette 	|	16			|
|	Albertville	| 16			|
