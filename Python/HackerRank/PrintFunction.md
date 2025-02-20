# [Python Function](https://www.hackerrank.com/challenges/python-print/problem)

## Task

The included code stub will read an integer, n, from STDIN.
Without using any string methods, try to print the following:
123•. •n

Note that"..." represents the consecutive values in between.

### Example
n = 5
Print the string 12345.

### Input Format
The first line contains an integer n.

### Constraints

1≤n ≤ 150

### Output Format
Print the list of integers from 1 through n as a string, without spaces.

```
SAMPLE CODE HERE
```

## My attempts

<details>
<summary> ❌ Attempt #1: passing looped output into an array or set?</summary>

I'm not sure how to print al the numbers to a single line without spaces, but I do know how to solve this problem if I print to a new line each time, so let's start with that:

  ```
i = 1
while i <= n:  
    print(i)  
    i += 1
  ```

My first thought is to splice the output of this loop into an array (or set?), and then find a way to remove the delimiters in that array and print the output.

... That seems too complicated, though, as this is an `easy` problem with a 97% complete rate. I'll check [the notes](https://www.hackerrank.com/challenges/python-print/tutorial) to see how the creator intended this problem to be approached. 

</details>

<details>
<summary> ✅ Attempt #2: The print function takes arguments!</summary>

It turns out that the `print()` function doesn't _have_ to print its output to a new line each time! You can customize this by adjusting the `end` argument of the function, which lets you define the delimiter.  

That means this problem is indeed much easier than I had expected:

  ```
i = 1
while i <= n:  
    print(i, end="")  
    i += 1
  ```
</details>

## Key learnings

* 🧠 `print()` is a function, and as a function, it has multiple pre-programmed arguments... beyond just the thing it's printing to the console.

* 🧠 One of `print()`'s arguments is `end="/n"`, which defines its delimiter, and you can change this delimiter from `/n` (new line) to anything you want... including nothing!

## Final solution

```
i = 1
while i <= n:  
    print(i, end="")  
    i += 1
```
 
