# Project: Analyzing Vehicle Charging Habits

As electronic vehicles (EVs) become more popular, there is an increasing need for access to charging stations, also known as ports. To that end, many modern apartment buildings have begun retrofitting their parking garages to include shared charging stations. A charging station is shared if it is accessible by anyone in the building.

But with increasing demand comes competition for these ports — nothing is more frustrating than coming home to find no charging stations available! In this project, you will use a dataset to help apartment building managers better understand their tenants’ EV charging habits.

The data has been loaded into a PostgreSQL database with a table named `charging_sessions` with the following columns:

## Database: charging_sessions

| Column | Definition | Data type |
|-|-|-|
|`garage_id`| Identifier for the garage/building|`VARCHAR`|
|`user_id` | Identifier for the individual user|`VARCHAR`|
|`user_type`|Indicating whether the station is `Shared` or `Private`| `VARCHAR` |
|`start_plugin`|The date and time the session started |`DATETIME`|
|`start_plugin_hour`|The hour (in military time) that the session started | `NUMERIC`|
|`end_plugout`|The date and time the session ended | `DATETIME` |
|`eng_plugin_hour`|The hour (in military time) that the session ended | `NUMERIC`|
|`duration_hours`| The length of the session, in hours|`NUMERIC`|
|`el_kwh`| Amount of electricity used (in Kilowatt hours)|`NUMERIC`|
|`month_plugin`| The month that the session started |`VARCHAR`|
|`weekdays_plugin`| The day of the week that the session started|`VARCHAR`|

## Project start

My progress through the project is as follows.

[x] Created GitHub landing page
<br>
[] Tried project once by myself
<br>
[] Checked solution — annotated what I learned if my answer was wrong
<br>
[] Document will not be edited further
<br>

### What does this database look like?
In Datacamp's first project, [Analyzing International Debt Statistics](DataCamp/analyzing-international-debt-statistics.md) I got the second question wrong because I did not preview the database output and/or did not know about how debt is tracked. I assumed that each row would be a country plus its gross national debt, but the database actually contained multiple different types of debt. This meant that each country was listed multiple times: one per debt code. As such, I needed to `SELECT` not `debt`, but rather `SUM(debt)`. 

To avoid having this issue again, I am first going to query the entire database. 

```
SELECT *
FROM charging_sessions
LIMIT 10;
```

Which gave me an output of:

| garage_id                        | user_id   | user_type   | start_plugin   | start_plugin_hour   |   end_plugout | end_plugout_hour    |   el_kwh |   duration_hours |   month_plugin | weekdays_plugin   | Unnamed: 11   |
|:---------------------------------|:----------|:------------|:---------------|:--------------------|--------------:|:--------------------|---------:|-----------------:|---------------:|:------------------|:--------------|
| 0                                | AdO3      | AdO3-4      | Private        | 2018-12-21 10:20:00 |            10 | 2018-12-21 10:23:00 |       10 |             0.3  |       0.05     | Dec               | Friday        |
| 1                                | AdO3      | AdO3-4      | Private        | 2018-12-21 10:24:00 |            10 | 2018-12-21 10:32:00 |       10 |             0.87 |       0.136667 | Dec               | Friday        |
| 2                                | AdO3      | AdO3-4      | Private        | 2018-12-21 11:33:00 |            11 | 2018-12-21 19:46:00 |       19 |            29.87 |       8.21639  | Dec               | Friday        |
| 3                                | AdO3      | AdO3-2      | Private        | 2018-12-22 16:15:00 |            16 | 2018-12-23 16:40:00 |       16 |            15.56 |      24.4197   | Dec               | Saturday      |
| 4                                | AdO3      | AdO3-2      | Private        | 2018-12-24 22:03:00 |            22 | 2018-12-24 23:02:00 |       23 |             3.62 |       0.970556 | Dec               | Monday        |
| 5                                | AdO3      | AdO3-2      | Private        | 2018-12-24 23:32:00 |            23 | 2018-12-25 17:37:00 |       17 |            16.14 |      18.0778   | Dec               | Monday        |
| 6                                | AdO3      | AdO3-2      | Private        | 2018-12-25 18:25:00 |            18 | 2018-12-26 16:08:00 |       16 |            10.33 |      21.7208   | Dec               | Tuesday       |
| 7                                | AdO3      | AdO3-4      | Private        | 2018-12-26 10:41:00 |            10 | 2018-12-26 16:52:00 |       16 |            27.66 |       6.18806  | Dec               | Wednesday     |
| 8                                | AdO3      | AdO3-2      | Private        | 2018-12-26 18:46:00 |            18 | 2018-12-26 21:08:00 |       21 |             8.83 |       2.37111  | Dec               | Wednesday     |
| 9                                | AdO3      | AdO3-2      | Private        | 2018-12-29 16:04:00 |            16 | 2018-12-29 20:55:00 |       20 |             8.58 |       4.85611  | Dec               | Saturday      |

I'm not sure 
