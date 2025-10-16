# [Uncategorized Basic SQL Problems]([url](https://www.hackerrank.com/domains/sql))

Basic SQL tasks from HackerRank that are not related to the (a) demographics assignment or (b) weather report assignment.

Note: At the time of doing these tasks, I have not used/read SQL or Python for over one year. 

The presence of ⚡️ next to a question means I learned something new by solving it. 

## Key learnings & Questions

<details>
<summary>🧠 Observe my brain grow </summary>

  - Remember to end lines in `;`
  - `ORDER BY` can take multiple parameters, separated by commas; later parameters trigger in the event of a ite
  - `RIGHT` is used to select characters from the end of a string

</details>

<details>
<summary> ✅ Resolved questions questions</summary>

- Is there ever a time where I will `SELECT` something other than `*` ?  
   - Only `SELECT` `*` if asked to return all information that fits certain parameters. If you know you are querying for a specific piece of information, a more specific field than `*` may be used.

</details> 

<details>
<summary> ❓ Pending questions questions</summary>

- Are there other "substring" functions than `RIGHT` ?
- What should/shouldn't be capitalized in SQL?

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

## [4. Select by ID ](https://www.hackerrank.com/challenges/select-by-id/problem?isFullScreen=true)

<details>
<summary> Expand to see chicken scratch </summary>

_Query all columns for a city in CITY with the ID 1661._

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
SELECT * 
FROM CITY
WHERE ID = 1661;
  ```

Again, nothing to learn here. 

</details>


### Key learnings

🧠 N/A
❓ N/A

</details>

--- 

## ⚡️ [Score > 75](https://www.hackerrank.com/challenges/more-than-75-marks/problem?isFullScreen=true)

<details>
<summary> Expand to see chicken scratch </summary>

_Query the Name of any student in STUDENTS who scored higher than  Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID._

_Input Format_

_The STUDENTS table is described as follows:_

```

| Column | Type    |
|--------|---------|
| ID     | Integer |
| Name   | String  |
| Marks  | Integer |

```

### My attempts

<details>
<summary> ❌ Attempt #1</summary>

I tried:

  ```
SELECT NAME
FROM STUDENTS
WHERE MARKS > 75
ORDER BY ASC;
  ```

But I don't remember:
- How `order by` works
- How to focus on certain characters within a string
- The difference between a primary and secondary sort

I learned about the `right` function, which extracts a number of characters from the right of a string or fields in a column:

```
RIGHT(column_here, number_of_characters)
```
And I learned that `order by` can take an initial parameter, but then use a second parameter in the event of a tie:

```
ORDER BY PARAMETER_1 ASC/DESC, PAREMETER_2 ASC/DESC
```

And I think this will let me solve the problem. 

</details>

<details>
<summary> ✅ Attempt #2</summary>

I tried:

  ```
SELECT NAME AS N
FROM STUDENTS
WHERE MARKS > 75 
ORDER BY RIGHT(N, 3), ID ASC
  ```

And that worked!

</details> 


### Key learnings

🧠 `ORDER BY` can take multiple parameters, separated by commas; later parameters trigger in the event of a item    
🧠 `RIGHT` is used to select characters from the end of a string  
❓ Are there other "substring" functions?  

</details>

--- 

## [Japanese cities attributes](https://www.hackerrank.com/challenges/japanese-cities-attributes/problem?isFullScreen=true)

<details>
<summary> Expand to see chicken scratch </summary>

_Query all attributes of every Japanese city in the CITY table. The COUNTRYCODE for Japan is JPN._

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
SELECT * 
FROM CITY
WHERE COUNTRYCODE = 'JPN';
  ```

Again, easy. 

</details>


### Key learnings

🧠 N/A
❓ N/A

</details>

--- 

## [Japanese cities' names]([url](https://www.hackerrank.com/challenges/japanese-cities-name/problem?isFullScreen=true))

<details>
<summary> Expand to see chicken scratch </summary>

_Query the names of all the Japanese cities in the CITY table. The COUNTRYCODE for Japan is JPN._
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
SELECT NAME
FROM CITY
WHERE COUNTRYCODE = 'JPN';
  ```

And was right. 

</details>


### Key learnings

🧠 n/a
❓ n/a

</details>

--- 
## [Task](url)

<details>
<summary> Expand to see chicken scratch </summary>

taskhere

```
codestubhere
```

### My attempts

<details>
<summary> ❌✅ Attempt #1</summary>

I tried:

  ```
querygoeshere
  ```

commentgoeshere

</details>


### Key learnings

🧠 bigbrainstuffhere
❓ questionshere

</details>

--- 
