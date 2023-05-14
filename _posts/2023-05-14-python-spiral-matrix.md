---
layout: post
tags: nerd, programming, python
cat: post
date: 2023-05-14
description: One of my teammates threw this python challenge. Read more
---

Yet another new challenge from the team. The ask is simple.
Given a positive integer ```n```, generate an ```n x n``` matrix filled with elements from ```1``` to ```n^2``` in spiral order

Examples are below
  
```
                                                           1 -->  2 -->  3 -->  4 --> 5
                                  1 -->  2 -->  3 --> 4                               |
                 1 --> 2 --> 3                        |   16 --> 17 --> 18 --> 19     6
       1 --> 2               |   12 --> 13 --> 14     5    |                    |     |
  1          |   8 --> 9     4    |             |     |   15     24 --> 25     20     7
       4 <-- 3   |           |   11     16 <-- 15     6    |      |             |     |
                 7 <-- 6 <-- 5    |                   |   14     23 <-- 22 <-- 21     8
                                 10 <--  9 <--  8 <-- 7    |                          |
                                                          13 <-- 12 <-- 11 <-- 10 <-- 9
       
n = 1   n = 2       n = 3                n = 4                       n = 5    
      
```

It was interesting and I did write some piece of code in python. However the code is an exact replica on how we would manually fill the matrix.

If you could find a better way, please do let me know!

You can see the same code [here](https://github.com/kirankumargosu/python/blob/main/spiral.py).

Thanks.

