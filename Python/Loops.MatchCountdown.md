# [Loops: Match Countdown](https://www.boot.dev/lessons/d6a705f8-7d2b-4be5-aa38-6bad6c5eabb7)

## Task

Write a loop that counts down from `10` to `1`. At each iteration, print the number with an ellipsis:

`i...`

However, when `i` is `1`, it should print `1...Fight!` instead.

## My attempts

<details>
<summary> ❌ Attempt #1: Shouldn't use `while` loop</summary>

I initially wanted to use a `while` loop for this, so that I could print the final string once the condition `i>1` was no longer true. 

  ```
def countdown_to_start():
    while i > 1:
        i = 10
        print(f"{i}...")
        i -= 1
    print("1...Fight!")
  ```

This resulted in a traceback error because the variable `i` was needed in local scope but had not been first made available in global scope. 

Instead, I should write this as a `for` loop:

</details>

<details>
<summary> ❌ Attempt #2: Loops can be inverted!</summary>

I translated that `while` loop to a `for` loop like this:

  ```
def countdown_to_start():
  for i in range (1, 10, -1):
    if i > 1:
      print(f"{i}...")
  Print("1...Fight!"
  ```

And there were two notable problems with this:
1. The loop _starts_ at one, and iterates by negative one, so we never get the countdown from 10 to 1
2. My first condition expects `i` to be greater than 1... so even if the countdown logic worked, we'd be skipping it anyway

</details>

<details>
<summary> ✅ Attempt #2</summary>

I've made two adjustments:
1. The loop now begins at 10
2. I now us an if/else sequence that first checks to see if we're at the exit condition of 1
3. I change the assignment operator `=` to the comparison operator `==` — I always forget this 🥲

  ```
def countdown_to_start():
    for i in range(10, 0, -1): 
        if i == 1:  # When should we print "Fight!"?
            print("1... Fight!")
        else:
            print(f"{i}...")
  ```
</details>

## Key learnings

* 🧠 Loops do not need to be ascending; they can be descending, too
* 🧠 `if x = 1` does not check whether x = 1, but rather assigns x as being equal to 1. To better visualize what that means:

```
x = 5
if x == 5:
    print("Equal!")
if x == 6:
    print("Not going to print!")
```



## Final solution

```
def countdown_to_start():
    for i in range(10, 0, -1): 
        if i == 1:  # When should we print "Fight!"?
            print("1... Fight!")
        else:
            print(f"{i}...")
  ```
 
