# 3.5. Totals

In many reports, we may need to show some total information: sum of the group, number of rows in the list, and many others. FastReport uses totals to perform this task. For the total, you need to indicate the following parameters:
 
- The total function type;
- The expression, which is supposed to be calculated. For the "Count" function, you do not need to indicate the expression;
- The condition. The function will be calculated if the condition is met. It's not obligatory to set up the condition.
- The data band, for which the function will be processed;
- The band, in which the total value will be printed.

The list of total functions is given below:

| Function | Description |
|:-|:-|
| `Sum` | Calculates the sum of the expression. |
| `Min` | Calculates the minimum value of the expression. |
| `Max` | Calculates the maximum value of the expression. |
| `Average` | Calculates the average value of the expression. |
| `Count` | Returns the number of rows. |


---

[System Variables](SystemVariables.md) | [Top Page](README.md) | [Expressions](Expressions.md)