# Key Learnings
These are the main things I lerned while working through this problem set:

1. ENUM | Source: [Select Q1](https://github.com/SuikaCider/coding_practice/blob/main/LeetCode/TopSQL50/select_problems.md) </br>
 🧠 The enum data type exists. The `Y` `N` values within it are considered to be strings.

2. `!=` + `NULL` | Source: [Select Q2](https://github.com/SuikaCider/coding_practice/blob/main/LeetCode/TopSQL50/select_problems.md) 
</br> 🧠 `!=` will not return values that are `NULL`. To get `NULL`-inclusive results, you need to use a 2nd `WHERE` condition: `OR {field} IS NULL.`
