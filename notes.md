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
SELECT customer_id, inventory_id, rental_date
FROM dvd_rentals.rental
ORDER BY inventory_id, rental_date DESC LIMIT 8;
```

2. For the films with the longest `length`, what is the `title` of the "R" rated film with the lowest `replacement_cost` in `dvd_rentals.film` table?
Answer:
```
SELECT category, total_sale
FROM dvd_rentals.sales_by_film
ORDER BY category_id DESC LIMIT 1;
```


3. Who was the `manager` of the store with the highest `total_sales` in the `dvd_rentals.sales_by_store` table?


4. What is the `postal_code`of the city with the 5th highest `city_id` in the `dvd_rentals.address` table?
