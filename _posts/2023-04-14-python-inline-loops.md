---
layout: post
tags: nerd, programming, python
cat: post
date: 2023-04-14
description: One of my teammates threw this python challenge. Read more
---

## Python Inline Loops
One of my teammates threw this challenge today.
The challenge is simple and is as follows:


There are ```n``` kids with candies. You are given an integer array ```candies```, where each ```candies[i]``` represents the number of candies the ```i```<sup>```th```</sup> kid has, and an integer ```extraCandies```, denoting the number of extra candies that you have.

Return _a boolean array_ ```result``` of length ```n```, where ```result[i]``` is ```True``` if, after giving the ```i```<sup>```th```</sup> kid all the ```extraCandies```, they will have the **greatest** number of candies among all the kids, or ```False``` otherwise

----
- Example 1:
    -   ```Input```:
        -   ```candies = [2, 3, 5, 1, 3]```
        -   ```extraCandies = 3```
    -   ```Output```:
        -   ```result = [True, True, True, False, True]```

- Example 2:
    -   ```Input```:
        -   ```candies = [4, 2, 1, 1, 2]```
        -   ```extraCandies = 1```
    -   ```Output```:
        -   ```result = [True, False, False, False, False]```
'''

----

<br>
The solution for this is very simple; it's below:

```python
result = [True if (x + extraCandies) >= max(candies) else False for x in candies]
```

But, I was wondering on all the options that we could try and thats how this post evolved.

----
## Traditional way of looping

```python

candies = [2, 3, 5, 1, 3]
extraCandies = 3
result = []

for c in candies:
    if c + extraCandies >= max(candies):
        result.append(True)
    else:
        result.append(False)

print(f'{result}\n')

```

```Output```

```
[True, True, True, False, True]
```

----

## Inline looping

```python

result = [True if (x + extraCandies) >= max(candies) else False for x in candies]
print('Inline looping over a list:')
print(f'{result}\n')

```

```Output```

```
[True, True, True, False, True]
```
----

<br>
In the problem, we were given two examples. So I thought I will run this inline loop for both the examples.
One way is to repeat the same code twice or put both the examples into a ```list```... ah no... it cannot be a ```list```,
because, we have different ```extraCandies``` for both the examples, so we need to use a ```dictionary```.

<br>

----

## Traditional looping over List of Dictionaries and Inline looping over each item

```python
candyDict = [
    {'candies' : [2, 3, 5, 1, 3],
     'extraCandies': 3},
    {'candies' : [4, 2, 1, 1, 2],
     'extraCandies': 1},
]

for cd in candyDict:
    result = [True if (x + cd['extraCandies']) >= max(cd['candies']) else False for x in cd['candies']]
    print(f'{result}')
```

```Output```

```
[True, True, True, False, True]
[True, False, False, False, False]

```
----
<br>


## Inline looping over the list of dictionaries and its underling data - nested inline

```python
result = [[True if c + cd['extraCandies'] >= max(cd['candies']) else False for c in cd['candies']] for cd in candyDict]
```

```Output```

```
[[True, True, True, False, True],
 [True, False, False, False, False]
]

```

----
Until now, the output is a ```list```. But we do not know which result refers to which set of data. To get that, we need our result as ```dictionary```. So, we've added key to the input and the same key will be part of the result

----

## Inline looping of dictionaries and its underling data, returning key value pair for each result

```python
candyDict = [
    {'id' : 'one',
     'candies' : [2, 3, 5, 1, 3],
     'extraCandies': 3},

    {'id' : 'two',
     'candies' : [4, 2, 1, 1, 2],
     'extraCandies': 1},
]

result = [[{cd['id']: True if c + cd['extraCandies'] >= max(cd['candies']) else False} for c in cd['candies']] for cd in candyDict]
```

```Output```

```
[[{'one': True}, {'one': True}, {'one': True}, {'one': False}, {'one': True}], [{'two': True},
  {'two': False}, {'two': False}, {'two': False}, {'two': False}
]]

```

----

## Inline looping of dictionaries and its underlying data, returning key value per result set

```python
result = [{cd['id']: [True if c + cd['extraCandies'] >= max(cd['candies']) else False for c in cd['candies']]} for cd in candyDict]
```

```Output```

```
[{'one': [True, True, True, False, True]},
 {'two': [True, False, False, False, False]}
]

```

You can see the same code [here](https://github.com/kirankumargosu/python/blob/main/inline-loop.py).
