---
title: Bankers Rounding
date: 2024-12-08T01:00:00Z
image: /images/post/post-1.png
categories: ['math', 'python']
featured: true
draft: false
---

This is a rounding method that consists of the following rules:

- If the number before the digit to be rounded is higher than 5, round up
- If the number before the digit to be rounded is lower than 5, round down

**The interesting behavior occurs when the number to be rounded is exactly 5.**
 When the digit is 5, the rounding depends on the number before 5:

- If the number before 5 is even, round down
- If the number before 5 is odd, round up

In other words, round to the even number closer to the original number.
I encountered this method while reading a thread that posed an intriguing coding question:


**Why does this happen?**

```python
>>> round(6.045)
6.04
>>> round(6.035)
6.04
# -----------------
>>> round(6.5)
6
>>> round(5.5)
6
```

In both cases, it returns 6.04. We would think that the first line returns 6.05 because of what we learned in school, but now we know that certain programming languages round this way because it is more efficient.



In the following table, see the efficacy of the banker's rounding

|                  | **Standard rounding** |                 | **Banker's rounding** |                        |
| ---------------- | --------------------- | --------------- | --------------------- | ---------------------- |
| **Interest**     | **Result**            | **Deviation**   | **Result**            | **Deviation**          |
| 0.005            | 0.01                  | 0.005           | 0                     | -0.005                 |
| 0.015            | 0.02                  | 0.005           | 0.02                  | 0.005                  |
| 0.025            | 0.03                  | 0.005           | 0.02                  | -0.005                 |
| 0.035            | 0.04                  | 0.005           | 0.04                  | 0.005                  |
| 0.045            | 0.05                  | 0.005           | 0.04                  | -0.005                 |
| **Sum:**       |                       |                 |                       |                        |
| 0.125            | 0.15                  | 0.025           | 0.12                  |             0.005      |



_The banker's rounding has the smallest difference from the original value. So it is more accurate_