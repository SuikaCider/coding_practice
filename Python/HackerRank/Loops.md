# [Python Loops Intro](https://www.hackerrank.com/challenges/python-loops/problem?isFullScreen=true)

## Task

The provided code stub reads an integer, n, from STDIN. For all non-negative integers i < n, print i? .

```
if __name__ == '__main__':
    n = int(input())
```

## My attempts

<details>
<summary> ❌ Attempt #1</summary>

  ```
while i < n:
    print(i**2)
    i += 1 
  ```

This yielded a runtime error.

</details>

<details>
<summary> ✅ Attempt #2</summary>

  ```
i =0
while i < n:
    print(i**2)
    i += 1 
  ```
</details>

## Key learnings

🧠 Variables cannot be used unless initialized. If I wish to use `i` as a counter in a while loop, I should establish that `i=0` before beginning the loop. 

## Final solution

```
i =0
while i < n:
    print(i**2)
    i += 1
```
