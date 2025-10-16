# [Uncategorized Basic SQL Problems]([url](https://www.hackerrank.com/domains/sql))

Basic SQL tasks from HackerRank that are not related to the (a) demographics assignment or (b) weather report assignment.

Note: At the time of doing these tasks, I have not used/read SQL or Python for over one year. 

## Key learnings & Questions

🧠 Remember to end lines in `;`
❓ Is there ever a time where I will `SELECT` something other than `*` ?

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
