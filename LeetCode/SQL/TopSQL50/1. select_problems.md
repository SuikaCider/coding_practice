# TopSQL 50 — SELECT challenges

There are 5 problems which focus on the use of `SELECT`. Below is the problem, my queries to solve those problems, and anything I learn from writing these queries. 

## 🎯 Question 1: Recyclable & Low Fat Products

Question text:
> Write a solution to find the ids of products that are both low fat and recyclable.
> Return the result table in any order.

<details>
  <summary>See `Products` Schema Here</summary>


| Column Name | Type    |
|-------------|---------|
| product_id  | int     |
| low_fats    | enum    |
| recyclable  | enum    |

* product_id is the primary key (column with unique values) for this table.
* low_fats is an ENUM (category) of type ('Y', 'N') where 'Y' means this product is low fat and 'N' means it is not.
* recyclable is an ENUM (category) of types ('Y', 'N') where 'Y' means this product is recyclable and 'N' means it is not.

</details>

<details><summary>✅ Attempt 1</summary>

```
SELECT product_id
FROM products
WHERE low_fats = 'Y'
  AND recyclable = 'Y';
```

</details>

🧠 The `enum` data type, and that the `Y` `N` values within it are considered to be strings. 

## 🎯 Question 2: Find Customer Referee

Question text:
> Find the names of the customer that are not referred by the customer with id = 2.
> Return the result table in any order.

</details>

<details><summary>See `Customer` Schema Here</summary>

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| name        | varchar |
| referee_id  | int     |

* In SQL, id is the primary key column for this table.
* Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.

</details>

<details><summary>❌ Attempt 1</summary>

```
SELECT name
FROM Customer
WHERE referee_id NOT = 2;
```
Error: `NOT = 2` is not correct syntax. To get "INT value is not #" I should use `!=`.

</details>

<details><summary>❌ Attempt 2 </summary>

```
SELECT name
FROM Customer
WHERE referee_id != 2;
```
Error: This correctly filtered out `referee_id = 2`, but it did _not_ list the three people which had a `null` value. SQL treats `UNKNOWN` values as separate to `TRUE` or `FALSE`, so to get `NULL`-inclusive results, I need to append `OR referee_id IS NULL` to my query. 

</details>

<details><summary>✅ Attempt 3 </summary>

```
SELECT name
FROM Customer
WHERE referee_id != 2
  OR referee_id IS NULL;
```

</details>

🧠 `!=` will not return values that are `NULL`. To get`NULL`-inclusive, you need to use a 2nd `WHERE` condition: `OR {field} IS NULL`.

## 🎯 Question 3: Which countries are big?

Question text: 
> A country is big if:
> * it has an area of at least three million (i.e., 3000000 km2), or
> * it has a population of at least twenty-five million (i.e., 25000000).

> Write a solution to find the name, population, and area of the big countries.
> Return the result table in any order.

<details><summary>See `World` Schema Here</summary>


| Column Name | Type    |
|-------------|---------|
| name        | varchar |
| continent   | varchar |
| area        | int     |
| population  | int     |
| gdp         | bigint  |

* name is the primary key (column with unique values) for this table.
* Each row of this table gives information about the name of a country, the continent to which it belongs, its area, the population, and its GDP value.

</details>

<details><summary>✅ Attempt #1</summary>

```
Select name, population, area
FROM World
WHERE area > 3000000
  OR population > 25000000;
```
</details>

## 🎯 Question 4: Who viewed their own articles?

Question text: 
> Write a solution to find all the authors that viewed at least one of their own articles.
> Return the result table sorted by id in ascending order.

<details><summary>See `Views` Schema Here</summary>

| Column Name   | Type    |
|---------------|---------|
| article_id    | int     |
| author_id     | int     |
| viewer_id     | int     |
| view_date     | date    |

* There is no primary key (column with unique values) for this table, the table may have duplicate rows.
* Each row of this table indicates that some viewer viewed an article (written by some author) on some date. 
Note that equal author_id and viewer_id indicate the same person.

</details>

<details><summary>❌ Attempt #1</summary>

I'm wondering if I can just write a condition where `field X = field Y`. Probably not... but let's see!

```
Select author_id AS id
FROM Views
WHERE author_id = viewer_id;
```

Error: 
* The syntax actually works just fine!
* The problem is that there are duplicate datas, so I should have selected `DISTINCT` ids
* I forgot to sort in ascending order

</details>

<details><summary>✅ Attempt #2</summary>

```
Select DISTINCT author_id AS id
FROM Views
WHERE author_id = viewer_id
ORDER BY author_id;
```

</details>

## 🎯 Question 5: Identifying invalid tweets

Question text: 
> Write a solution to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is strictly greater than 15.
> Return the result table in any order.

<details><summary>See `Tweets` Schema Here</summary>

| Column Name    | Type    |
|----------------|---------|
| tweet_id       | int     |
| content        | varchar |

* tweet_id is the primary key (column with unique values) for this table.
* This table contains all the tweets in a social media app.

</details>

<details><summary>❌ Attempt #1</summary>

```
SELECT tweet_id 
FROM Tweets
WHERE content > 15;
```
ERROR: 
* Dumb mistake. I assumed `content` would be the character length, but (a) that wouldn't be called content, and (b) the filetype is `varchar` not `int`
* What I need to do is count the amount of characters in each tweet

</details>

<details><summary>✅ Attempt #2</summary>

```
SELECT tweet_id 
FROM Tweets
WHERE LENGTH(content) > 15;
```
</details>

--- 

## Reflections

Easy! I completed (and recorded here) all of the challenges here in under 20 minutes. 

I need to pay more attention to data types in order to avoid dumb mistakes.
