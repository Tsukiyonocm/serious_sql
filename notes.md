Explaination Template of what every query is based off of

```sql
SELECT
  column_name_1,
  column_name_2
FROM schema_name.table_name
```

Section 1: Select & Sort Data
Exercises
1. What is the `name` of the category with the highest `category_id` in the `dvd_rentals.category` table? \
Answer:
```
SELECT name, category_id
FROM dvd_rentals.category
ORDER BY category_id DESC LIMIT 1;
```

2. For the films with the longest `length`, what is the `title` of the "R" rated film with the lowest `replacement_cost` in `dvd_rentals.film` table? \
Answer:
```
SELECT length, title, replacement_cost, rating
FROM dvd_rentals.film
ORDER BY length DESC, replacement_cost LIMIT 10;
```


3. Who was the `manager` of the store with the highest `total_sales` in the `dvd_rentals.sales_by_store` table? \
Answer:
```
SELECT manager, total_sales
FROM dvd_rentals.sales_by_store
ORDER BY total_sales DESC LIMIT 10;
```

4. What is the `postal_code`of the city with the 5th highest `city_id` in the `dvd_rentals.address` table? \
Answer:
```
SELECT postal_code, city_id
FROM dvd_rentals.address
ORDER BY city_id DESC LIMIT 5;
```



### Section 2 Record Counts & Distinct Values
Getting a count of all the rows
```
SELECT
COUNT(*) AS row_count
FROM dvd_rentals.film_list;
```
`AS` is an alias and what will the name of the row that the above SQL code produces. If there was no `AS`, it would have simply been `COUNT` in this example.


Getting unique column values
```
SELECT DISTINCT
rating
FROM dvd_rentals.film_list;
```
The above code would generate a table that has each unique film rating on it. (PG, PG-13, etc)

Getting count of Unique Values
```
SELECT
COUNT(DISTINCT category) AS unique_category_count
FROM dvd_rentals.film_list;
```