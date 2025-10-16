# [Weather Observation Station](https://www.hackerrank.com/domains/sql)

A series of questions form HackerRank that are related to a weather observation station's database. 

⚡️ next to a question indicates that I learned something new which I consider to be of note.

## Key learnings & Questions

<details>
<summary>🧠 Observe my brain grow </summary>

  - ⚡️ Values to be output must appear between `SELECT` and `FROM`
  - `DISTINCT` modifies `SELECT` to filter out duplicates.
  - `DISTINCT` goes inside of (), not outside it 
  - `UNION` can be used to join the results of multiple queries into a single output  

</details>

<details>
<summary> ✅ Resolved questions questions</summary>

- questionhere
   - answerhere

</details> 

<details>
<summary> ❓ Pending questions questions</summary>

- I should learn about the order in which SQL queries are executed
- How does `UNION` / `UNION ALL` work?

</details> 

---

## [Question 1](https://www.hackerrank.com/challenges/weather-observation-station-1/problem?isFullScreen=true)

<details>
<summary> Expand to see chicken scratch </summary>

_Query a list of CITY and STATE from the STATION table._
_The STATION table is described as follows:_

```
| Field  | Type           |
|--------|----------------|
| ID     | NUMBER         |
| CITY   | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)    |
| LAT_N  | NUMBER         |
| LONG_W | NUMBER         |
```

### My attempts

<details>
<summary> ✅ Attempt #1</summary>

I tried:

  ```
SELECT CITY, STATE
FROM STATION;
  ```

Huzzah

</details>


### Key learnings

🧠 N/A  
❓ N/A  
 
</details> 

---

## ⚡️ [Question 2](https://www.hackerrank.com/challenges/weather-observation-station-2/problem?isFullScreen=true)

<details>
<summary> Expand to see chicken scratch </summary>

_Query the following two values from the STATION table:_

_1. The sum of all values in LAT_N rounded to a scale of 2 decimal places._
_2. The sum of all values in LONG_W rounded to a scale of 2 decimal places._

```
| Field  | Type           |
|--------|----------------|
| ID     | NUMBER         |
| CITY   | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)    |
| LAT_N  | NUMBER         |
| LONG_W | NUMBER         |
```

### My attempts

<details>
<summary> ❌ Attempt #1</summary>

I don't remember how to sum values, but I assume that the syntax will be something like `SUM(LAT_N, 2)`. Let's see how it goes.

  ```
SELECT LAT_N AS N, LONG_W as W
FROM STATION
SUM (N, 2)
SUM (W, 2);
  ```

I learned:
- `SUM()` is indeed a function, but it's syntax is not as I expected.
- `ROUND()` is needed for this problem. It's syntax is `ROUND(VALUE, #_DECIMAL_POINTS)`

</details>

<details>
<summary> ❌ Attempt #2</summary>

I tried:

  ```
SELECT LAT_N AS N, LONG_W as W
FROM STATION
ROUND(SUM(N), 2)
ROUND(SUM(W), 2);
  ```

I learned:
- You apparently can't use aliases with aggregate functions
- You cannot select multiple select columns (?) in line

</details>

<details>
<summary> 💀 Gave up</summary>

I decided that I was missing too much knowledge to solve this. I decided to see the answer, break it down, and move on.

  ```
SELECT 
  ROUND(SUM(LAT_N), 2) AS sum_lat_n,
  ROUND(SUM(LONG_W), 2) AS sum_long_w
FROM STATION;
  ```

I learned:
- My mistake seems to have primarily been a syntax issue; I should select the aggregate value, not whatever I did above
- You apparently need to escape the result of the aggregate function to something? (Not sure if _escape_ is the right term... it's what `>` does in command line)

</details> 

### Key learnings

🧠 Data that should be displayed as output must go between `SELECT` and `FROM`  
❓ I should learn about the order in which SQL queries are executed  

</details>

--- 

## [Question #3](https://www.hackerrank.com/challenges/weather-observation-station-3/problem?isFullScreen=true)

<details>
<summary> Expand to see chicken scratch </summary>

_Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer._
_The STATION table is described as follows:_

```
| Field  | Type           |
|--------|----------------|
| ID     | NUMBER         |
| CITY   | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)    |
| LAT_N  | NUMBER         |
| LONG_W | NUMBER         |
```

### My attempts

<details>
<summary> ✅ Attempt #1</summary>

I'm going to get this wrong because I don't remember how to filter for even or odd values. I am going to try using `%2 = 0` from Python, which should include only numbers that are cleanly divisible by 2. I also don't know how to exclude duplicates. 

  ```
SELECT CITY
FROM STATION
WHERE ID % 2 = 0;

  ```

I learned that `DISTINCT` modifies `SELECT` to filter out duplicates.

</details>


### Key learnings

🧠 `DISTINCT` modifies `SELECT` to filter out duplicates.  
❓ n/a  

</details>

--- 

## [Question #4](https://www.hackerrank.com/challenges/weather-observation-station-4/problem?isFullScreen=true)

<details>
<summary> Expand to see chicken scratch </summary>

_Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table._

```
| Field  | Type           |
|--------|----------------|
| ID     | NUMBER         |
| CITY   | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)    |
| LAT_N  | NUMBER         |
| LONG_W | NUMBER         |
```

### My attempts

<details>
<summary> ❌ Attempt #1</summary>

I will probably get this wrong because I don't know how to return differences in SQL. I will assume it uses the standard `-` operator.

  ```
SELECT 
    SUM(CITY) - DISTINCT SUM(CITY) AS DUPLICATE_CITIES
FROM STATION
  ```

I learned:
   - `SUM` and `COUNT` are different; `COUNT` returns the number of entities, while `SUM` requires some sort of numbers to operate
   - `DISTINCT` goes inside the (), not outside

</details>

<details>
<summary> ✅ Attempt #2</summary>

I tried:

  ```
SELECT 
    COUNT(CITY) - COUNT(DISTINCT CITY) AS DUPLICATE_CITIES
FROM STATION
  ```

And that worked. 

</details>

### Key learnings

🧠 `count` returns the number of entities, `sum` does math  
🧠 `DISTINCT` goes inside of (), not outside it  
❓ no questions  

</details>

--- 
## [Question #5](https://www.hackerrank.com/challenges/weather-observation-station-5/problem?isFullScreen=true)

<details>
<summary> Expand to see chicken scratch </summary>

_Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically._

```
| Field  | Type           |
|--------|----------------|
| ID     | NUMBER         |
| CITY   | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)    |
| LAT_N  | NUMBER         |
| LONG_W | NUMBER         |
```

### My attempts

<details>
<summary> ❌ Attempt #1</summary>

I can tell that this is another substring command, but I don't know how to count the characters in a string.  
→ I googled, it's `count`

So let's go:

  ```
SELECT
  MIN(LEN(CITY)) AS short_city,
  MAX(LEN(CITY)) AS long_city
FROM STATION
ORDER BY ASC
  ```

I learned:
- I need to put commas between items in `SELECT`
- I can't read; I'm supposed to return the city name, not the length of characters in the shortest/longest cityn ame. This apparently requires what's called a `subquery`

</details>

<details>
<summary> ❌ Attempt #2</summary>

I tried:

  ```
SELECT CITY, LENGTH(CITY) AS city_length
FROM STATION
WHERE LENGTH(CITY) = (SELECT MIN(LENGTH(CITY)) FROM STATION)
   AND LENGTH(CITY) = (SELECT MAX(LENGTH(CITY)) FROM STATION)
ORDER BY CITY ASC
  ```
I learned:
- And this doesn't work because `MIN(...)` and `MAX(...)` are both used within the same `WHERE` clause, meaning I'm looking for the value that is simultaneously the shortest and longest length within the dataset.
- I should limit my results (to 1) to get the smallest and largest value... otherwise I think I'll just order the cities by character length?
- I should use `UNION` to combine to separate queries into one output

</details>

<details>
<summary> ❌ Attempt #3</summary>

I tried:

  ```
SELECT CITY, LENGTH(CITY) AS city_len
FROM STATION
WHERE LENGTH(CITY) = (SELECT MIN(LENGTH(CITY)) FROM STATION)
ORDER BY CITY ASC
LIMIT 1

UNION

SELECT CITY, LENGTH(CITY) AS city_len
FROM STATION
WHERE LENGTH(CITY) = (SELECT MAX(LENGTH(CITY)) FROM STATION)
ORDER BY CITY ASC
LIMIT 1;
  ```

I expected it to work, but it didn't. Apparently it is also syntax stuff:
- I need to use `UNION ALL` instead of `UNION`, but don't know why
- Each query needs to be in (), but I don't know why

</details> 

<details>
<summary> 💀 Gave up</summary>

A solution is:

  ```
(SELECT CITY, LENGTH(CITY) AS city_length
 FROM STATION
 WHERE LENGTH(CITY) = (SELECT MIN(LENGTH(CITY)) FROM STATION)
 ORDER BY CITY
 LIMIT 1)
UNION ALL
(SELECT CITY, LENGTH(CITY) AS city_length
 FROM STATION
 WHERE LENGTH(CITY) = (SELECT MAX(LENGTH(CITY)) FROM STATION)
 ORDER BY CITY
 LIMIT 1);
  ```

For now, I'm satisfied that I understand what each line of the query is doing. I don't want to look into UNION/UNION ALL right now, so I will just wait to see what I learn the next time I have to use this command. 

</details> 

### Key learnings

🧠 `UNION` can be used to join the results of multiple queries into a single output  
❓ How does `UNION` / `UNION ALL` work?  

</details>

--- 
