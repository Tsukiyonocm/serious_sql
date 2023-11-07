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



# Section 2 Record Counts & Distinct Values
#### Getting a count of all the rows
```
SELECT
COUNT(*) AS row_count
FROM dvd_rentals.film_list;
```
`AS` is an alias and what will the name of the row that the above SQL code produces. If there was no `AS`, it would have simply been `COUNT` in this example.


#### Getting unique column values
```
SELECT DISTINCT
rating
FROM dvd_rentals.film_list;
```
The above code would generate a table that has each unique film rating on it. (PG, PG-13, etc)

#### Getting count of Unique Values
```
SELECT
COUNT(DISTINCT category) AS unique_category_count
FROM dvd_rentals.film_list;
```

#### Exercise: Record Counts & Distinct Values
1. Which `actor_id` has the most number of unique `film_id` records in the `dvd_rentals.filmactor` table?
```
SELECT actor_id, COUNT(DISTINCT film_id)
FROM dvd_rentals.film_actor
GROUP BY actor_id
ORDER BY COUNT DESC
LIMIT 5;
```

2. How many distinct `fid` values are there for the 3rd most  common `price` value in the `dvd_rentals.nicer_but_slower_film_list` table?

```
SELECT
price, COUNT(DISTINCT fid)
FROM dvd_rentals.nicer_but_slower_film_list
GROUP BY price
ORDER BY count;
```


3. How many unique `country_id` values exist in the `dvd_rentals.city` table?
```
SELECT
COUNT(DISTINCT country_id) AS unique_countries
FROM dvd_rentals.city;
```

4. What percentage of overall `total_sales` does the Sports `category` make up in the `dvd_rentals.sales_by_film_category` table?

```
SELECT
category,
ROUND(
100 * total_sales::NUMERIC / SUM(total_sales) OVER (),
2
) AS percentage
FROM dvd_rentals.sales_by_film_category;
```


5. What percentage of unique `fid` values are in the Children `category` in the `dvd_rentals.film_list` table?
```
SELECT
category,
ROUND(
100 * COUNT(DISTINCT fid)::NUMERIC / SUM(COUNT(DISTINCT fid)) OVER(),
2
) AS percentage
FROM dvd_rentals.film_list
GROUP BY category
ORDER BY category;
```