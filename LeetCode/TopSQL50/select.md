# TopSQL 50 — SELECT challenges


## 🎯 Question 1: Recyclable & Low Fat Products

Question text:
> Write a solution to find the ids of products that are both low fat and recyclable.
> Return the result table in any order.

<details>
  <summary>See `Products` Schema Here</summary>

|-------------|---------|
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

I learned the `enum` data type, and that the `Y` `N` values within it are considered to be strings. 

## 🎯 Question 2: ...
