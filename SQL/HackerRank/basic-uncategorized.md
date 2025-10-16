# [Uncategorized Basic SQL Problems]([url](https://www.hackerrank.com/domains/sql))

Basic SQL tasks from HackerRank that are not related to the (a) demographics assignment or (b) weather report assignment.

Note: At the time of doing these tasks, I have not used/read SQL or Python for over one year. 

## Key learnings & Questions

<details>
<summary>🧠 Observe my brain grow </summary>

  - Remember to end lines in `;`

</details>

<details>
<summary> ✅ Resolved questions questions</summary>

- Is there ever a time where I will `SELECT` something other than `*` ?  
   - Only `SELECT` `*` if asked to return all information that fits certain parameters. If you know you are querying for a specific piece of information, a more specific field than `*` may be used.

</details> 

<details>
<summary> ❓ Pending questions questions</summary>

- big question here

</details> 

---

## [1. Basic Select](https://www.hackerrank.com/challenges/revising-the-select-query/problem?isFullScreen=true)

<details>
<summary> Expand to see chicken scratch </summary>

  _Query all columns for all American cities in the CITY table with populations larger than 100000. The CountryCode for America is USA._

_The CITY table is described as follows:_

```
| Field       | Type           |
|-------------|----------------|
| ID          | NUMBER         |
| NAME        | VARCHAR2(17)   |
| COUNTRYCODE | VARCHAR2(3)    |
| DISTRICT    | VARCHAR2(20)   |
| POPULATION  | NUMBER         |

```

### My attempts

<details>
<summary> ❌ Attempt #1</summary>

I tried:

  ```
SELECT NAME
FROM CITY
WHERE COUNTRYCODE = 'USA'
WHERE POPULATION > 100000
  ```

Two errors:
- I forgot that I need to `select` all columns; the filtering will be done by the other commands
- I forgot that I needed to end in `;`
- I forgot the `and` parameter

</details>

<details>
<summary> ✅ Attempt #1</summary>

I tried:

  ```
SELECT *
FROM CITY
WHERE COUNTRYCODE = 'USA'
  AND POPULATION > 100000;
  ```

And this worked. First problem of the book passed 😅

</details> 

### Key learnings

🧠 I forgot a lot...  
❓ Is there ever a time where I will want to select something other than `*`?

</details>

---

## [2. Basic Select II](https://www.hackerrank.com/challenges/revising-the-select-query-2/problem?isFullScreen=true)

<details>
<summary> Expand to see chicken scratch </summary>

_Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA._

_The CITY table is described as follows:_

```
| Field       | Type           |
|-------------|----------------|
| ID          | NUMBER         |
| NAME        | VARCHAR2(17)   |
| COUNTRYCODE | VARCHAR2(3)    |
| DISTRICT    | VARCHAR2(20)   |
| POPULATION  | NUMBER         |

```

### My attempts

<details>
<summary> ❌ Attempt #1</summary>

I tried:

  ```
SELECT * 
FROM CITY
WHERE POPULATION > 120000
    AND COUNTRYCODE = 'USA'
  ```

And this failed. It returned the name of the cities alongside quite a bit of other information.

</details>

<details>
<summary> ✅ Attempt #2</summary>

I tried:

  ```
SELECT NAME 
FROM CITY
WHERE POPULATION > 120000
    AND COUNTRYCODE = 'USA'
  ```

This returned the names of the cities, as requested. 

</details> 

### Key learnings

🧠 The reason I queried `*` previously is because the task was `query all columns`. This task specifically requested to return `NAME`.

</details> 

---

## [3. Select All](https://www.hackerrank.com/challenges/select-all-sql/problem?isFullScreen=true)

<details>
<summary> Expand to see chicken scratch </summary>

_Query all columns (attributes) for every row in the CITY table._

_The CITY table is described as follows:_

```
| Field       | Type           |
|-------------|----------------|
| ID          | NUMBER         |
| NAME        | VARCHAR2(17)   |
| COUNTRYCODE | VARCHAR2(3)    |
| DISTRICT    | VARCHAR2(20)   |
| POPULATION  | NUMBER         |
```

### My attempts

<details>
<summary> ✅ Attempt #1</summary>

I tried:

  ```
SELECT ALL
FROM CITY
  ```

Which is of course super easy. Why wasnt this the first question 😭

</details>

### Key learnings

🧠 N/A  
❓ N/A  

</details>

--- 
