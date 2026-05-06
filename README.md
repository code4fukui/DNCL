# Description of the Common Test Procedure Description Standard Language (DNCL)

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

- National Center for University Entrance Examinations
- January 2022

In high school education concerning algorithms and programming, a variety of programming languages are adopted, and the amount of practical programming time also varies. Taking these circumstances into consideration, the National Center for University Entrance Examinations uses the procedure description language for the Common Test (DNCL) when setting questions for "Information-Related Basics".

Below, the basics of DNCL are explained for reference. However, for reasons such as simplifying the problem text, questions may sometimes be presented in a format that does not adhere to the descriptions in this document. Therefore, when taking the "Information-Related Basics" exam, please pay attention to the explanations and instructions within the specific problem text and answer accordingly.

## 1 Variables and Values

A variable name is a sequence of alphanumeric characters and "_" that begins with a letter.

- Example: kosu, kosu_gokei, Tokuten

Unless otherwise specified, a variable starting with a lowercase letter represents a normal variable, and a variable starting with an uppercase letter represents an array. In addition, a variable in all uppercase letters represents a value that does not change during execution.

An element of an array is specified by its element number using an index. For two or more dimensions, indices are separated by ",". For example, elements of the (one-dimensional) array Tokuten and the two-dimensional array Gyoretu are represented as Tokuten[2] and Gyoretu[3，2].

The value of an index is an integer of 0 or greater, but depending on the problem, only indices of 1 or greater are handled.

Unless otherwise specified, numbers are represented in decimal. A string is represented by enclosing a sequence of characters in "「" and "」", or in "\"" and "\"".

- Example: 100
- Example: 99.999
- Example: 「見つかりました」
- Example: "It was found."

## 2 Display Statement

A display statement displays the values of numbers, strings, and variables. In a display statement, when displaying multiple values, they are listed separated by 『と』, and 『を表示する』 is written at the end.

- Example: 「整いました」を表示する (「整いました」 is displayed.)
- Example: kosu と「個見つかった」を表示する (When kosu is 3, 「3 個見つかった」 is displayed.)
- Example: "(" と x と "，" と y と ")" を表示する (When x is 5 and y is −1, 「(5，-1)」 is displayed.)

## 3 Assignment Statements

An assignment statement sets a value to a variable. Write the variable or subscripted array on the left side of "←", and the value to be assigned on the right side. Also, it is possible to assign the same value to all elements of an array at once, or to replace them with the contents of another array.

- Example: kosu ← 3
- Example: Tokuten[4] ← 100
- Example: Tokuten のすべての要素に 0 を代入する
- Example: Tokuten ← {87, 45, 72, 100}

Multiple assignment statements can be placed side by side, separated by "， ". In this case, the assignment statements are executed in order from the left.

- Example: kosu_gokei ← kosu，tokuten ← kosu × (kosu ＋ 1)

Assignments involving addition or subtraction to the same variable (increment or decrement) can also be expressed by "～を～増やす" or "～を～減らす".

- Example: "kosu を 1 増やす" is the same as "kosu ← kosu ＋ 1".
- Example: "saihu を syuppi 減らす" is the same as "saihu ← saihu － syuppi".

To assign a value input from the outside, it may also be written as follows.

- Example: x ←【外部からの入力】

## 4 Operations

This section explains arithmetic operations, comparison operations, and logical operations. Comparison operations and logical operations that combine them can be used in the 〈Condition〉 of conditional branching statements (Section 5.1) and conditional repetition statements (Section 5.2).

### 4.1 Arithmetic Operations

The four basic arithmetic operations of addition, subtraction, multiplication, and division are specified using '＋', '－', '×', and ' / '.

In integer division, the quotient can be calculated using '÷' and the remainder using '％'.

- Example: atai ← 7 / 2 (3.5 is assigned to atai.)
- Example: syo ← 7÷ 2 (3 is assigned to syo.)
- Example: amari ← 10％ 3 (1 is assigned to amari.)

In the calculation of expressions using multiple operators, the operator on the left is basically calculated first, but '×', ' / ', '÷', and '％' are calculated before '＋' and '－'. Additionally, you can explicitly specify the order of operations by enclosing the expression in parentheses '(' and ')'.

- Example: sogaku ← ne1－ ne2－ ne3 is the same as sogaku ← (ne1－ ne2)－ ne3.
- Example: kosu ← 1＋ kazu÷ 3 is the same as kosu ← 1＋ (kazu÷ 3).
- Example: heikin ← (hidari＋ migi)÷ 2 is different from heikin ← hidari＋ migi÷ 2.

### 4.2 Comparison Operations

Comparison operations for numeric values are specified using '＝', '≠' (or ' ≠'), '＞', '≧', '≦', and '＜'. The result of the operation is a true or false value.

- Example: kosu ＞ 3 (Evaluates to true if kosu is greater than 3.)
- Example: ninzu× 2 ≦ 8 (Evaluates to true if 2 times ninzu is less than or equal to 8.)
- Example: kaisu ≠ 0 (Evaluates to true if kaisu is not equal to 0.)

For string comparison operations, '＝' and '≠' (or ' ≠') can be used. '＝' evaluates to true if the left and right sides are the same string, and false otherwise. '≠' (or ' ≠') evaluates to true if the left and right sides are different strings, and false otherwise (if they are the same string).

- Example: 「あいうえお」＝「あいうえお」 (Evaluates to true.)
- Example: 「あいうえお」＝「あいう」 (Evaluates to false.)
- Example: "ABC"＝"ABC" (Evaluates to true.)
- Example: "ABC"＝"abc" (Evaluates to false.)
- Example: 「あいうえお」≠「あいうえお」 (Evaluates to false.)
- Example: 「あいうえお」≠「あいう」 (Evaluates to true.)
- Example: "ABC"≠"ABC" (Evaluates to false.)
- Example: "ABC"≠"abc" (Evaluates to true.)

### 4.3 Logical Operations

Logical operations are operations on expressions that return true or false, and are specified using the 'かつ', 'または', and 'でない' operators. There is no precedence among logical operators, and the logical operation on the left is executed first, but you can specify the order of operations using parentheses '(' and ')'.

'〈Expression 1〉 かつ 〈Expression 2〉' evaluates to true if the results of both 〈Expression 1〉 and 〈Expression 2〉 are true, and false otherwise. '〈Expression 1〉 または 〈Expression 2〉' evaluates to true if the result of either 〈Expression 1〉 or 〈Expression 2〉 is true, and false otherwise. '〈Expression〉 でない' evaluates to false if the result of 〈Expression〉 is true, and true if it is false.

- Example: kosu ≧ 12 かつ kosu ≦ 27 (Evaluates to true if kosu is greater than or equal to 12 and less than or equal to 27.)
- Example: kosu％ 2 ＝ 0 または kosu ＜ 0 (Evaluates to true if kosu is an even number or a negative value.)
- Example: kosu ＞ 75 でない (Evaluates to true if kosu is not greater than 75.)
- Example: kosu ＞ 12 かつ kosu ＜ 27 でない is the same as (kosu ＞ 12 かつ kosu ＜ 27) でない. (Because the logical operator on the left is executed first.)
- Example: kosu ＞ 12 かつ kosu ＜ 27 でない is different from kosu ＞ 12 かつ (kosu ＜ 27 でない).

## 5 Control Statements

Conditional branching statements (Section 5.1), conditional repetition statements (Section 5.2), and sequential repetition statements (Section 5.3) are collectively called control statements. As the `<processing>` within a control statement, one or more display statements (Section 2), assignment statements (Section 3), functions that do not return a value (Section 6.2), conditional branching statements, sequential repetition statements, and conditional repetition statements can be used in sequence. Also, as the `<condition>` within conditional branching statements and conditional repetition statements, comparison operations (Section 4.2) and logical operations (Section 4.3) can be used.

### 5.1 Conditional Branching Statements

Conditional branching statements switch the processing to be executed depending on whether the `<condition>` is satisfied.

When a certain processing is to be executed if the `<condition>` is satisfied, and there is no processing to execute if the `<condition>` is not satisfied, it is specified with "ならば" as follows.

*General Form*
```
もし 〈条件〉 ならば
   〈処理〉
を実行する
```

*Example:*
```
もし x ＜ 3 ならば
  x ← x＋ 1
  y ← y－ 1
を実行する
```

If the `<processing>` is only one line, the whole statement can also be written on a single line as follows.

*General Form*
```
もし 〈条件〉 ならば 〈処理〉 を実行する
```

*Example:*
```
もし x ＜ 3 ならば x ← x＋ 1 を実行する
```

When a certain processing is to be executed if the `<condition>` is satisfied, and a different processing is to be executed if the `<condition>` is not satisfied, it is specified by combining "ならば" and "そうでなければ" as follows.

*General Form*
```
もし 〈条件〉 ならば
  〈処理 1〉
を実行し，そうでなければ
  〈処理 2〉
を実行する
```

*Example:*
```
もし x ＜ 3 ならば
  x ← x＋ 1
を実行し，そうでなければ
  x ← x－ 1
を実行する
```

Since the execution result does not change depending on the line break position, when each processing can be written on a single line, it may also be written as follows.

*General Form*
```
もし 〈条件〉 ならば 〈処理 1〉 を実行し，
そうでなければ 〈処理 2〉 を実行する
```

*Example:*
```
もし x ＜ 3 ならば x ← x＋ 1 を実行し，
そうでなければ x ← x－ 1 を実行する
```

If you want to switch the processing to be executed based on multiple conditions within a conditional branch, conditions are added using "そうでなくもし" between "ならば" and "そうでなければ" as follows.

*General Form*
```
もし 〈条件 1〉 ならば
  〈処理 1〉
を実行し，そうでなくもし 〈条件 2〉 ならば
  〈処理 2〉
を実行し，そうでなければ
  〈処理 3〉
を実行する
```

*Example:*
```
もし x ＝ 3 ならば
  x ← x＋ 1
を実行し，そうでなくもし y ＞ 2 ならば
  y ← y＋ 1
を実行し，そうでなければ
  y ← y－ 1
を実行する
```

Since the execution result does not change depending on the line break position, when each processing can be written on a single line, it may also be written as follows.

*General Form*
```
もし 〈条件 1〉 ならば 〈処理 1〉 を実行し，
そうでなくもし 〈条件 2〉 ならば 〈処理 2〉 を実行し，
そうでなければ 〈処理 3〉 を実行する
```

*Example:*
```
もし x ＝ 3 ならば x ← x＋ 1 を実行し，
そうでなくもし y ＞ 2 ならば y ← y＋ 1 を実行し，
そうでなければ y ← y－ 1 を実行する
```

### 5.2 Conditional Repetition Statements

There are two types of conditional repetition statements: "pre-test" and "post-test".

#### 5.2.1 Pre-test

While the `<condition>` is satisfied, the `<processing>` is repeatedly executed.

Because it is evaluated whether the `<condition>` is satisfied before executing the `<processing>`, the `<processing>` may not be executed even once.

*General Form*
```
〈条件〉 の間，
  〈処理〉
を繰り返す
```

*Example:*
```
x ＜ 10 の間，
  gokei ← gokei＋ x
  x ← x＋ 1
を繰り返す
```

#### 5.2.2 Post-test

The `<processing>` is repeatedly executed until the `<condition>` is satisfied.

Because it is evaluated whether the `<condition>` is satisfied after executing the `<processing>`, the `<processing>` is executed at least once.

*General Form*
```
繰り返し，
  〈処理〉
を， 〈条件〉 になるまで実行する
```

*Example:*
```
繰り返し，
  gokei ← gokei＋ x
  x ← x＋ 1
を，x ≧ 10 になるまで実行する
```

#### 5.3 Sequential Repetition Statements

Sequential repetition statements repeatedly execute the `<processing>` while increasing the value of the `<variable>`.

*General Form*
```
〈変数〉 を 〈初期値〉 から 〈終了値〉 まで 〈差分〉 ずつ増やしながら，
  〈処理〉
を繰り返す
```

Sequential repetition statements are executed in the following steps:
1. The `<initial value>` is assigned to the `<variable>`.
2. If the value of the `<variable>` is greater than the `<end value>`, the repetition terminates.
3. The `<processing>` is executed, the `<step>` is added to the value of the `<variable>`, and the process returns to step 2.

*Example:*
```
x を 1 から 10 まで 1 ずつ増やしながら，
  gokei ← gokei＋ x
を繰り返す
```

If "増やしながら" is changed to "減らしながら", the `<processing>` is repeatedly executed while decreasing the value of the `<variable>` from the `<initial value>` by the `<step>`, until the value becomes smaller than the `<end value>`.

*Example:*
```
x を 10 から 1 まで 1 ずつ減らしながら，
  gokei ← gokei＋ x
を繰り返す
```

## 6 Calling Provided Functions

Among the functions provided in advance, there are those that return a value and those that do not return a value. The behavior of the functions is defined in the problem statement.

### 6.1 Functions that Return a Value

In the problem statement,

- Provide a function 「二乗」 that returns the square of the specified value
- Provide a function 「べき乗 (m，n)」 that returns the value of m raised to the power of n
- Provide a function 「乱数 (m，n)」 that randomly returns one integer greater than or equal to m and less than or equal to n
- Provide a function 「奇数 (n)」 that returns true when the value n is an odd number, and returns false otherwise

functions defined as above can be used within display statements (Section 2), assignment statements (Section 3), arithmetic operations (Section 4.1), comparison operations (Section 4.2), or logical operations (Section 4.3). When calling a function, write the arguments between 『(』 and 『)』 following the function name. When specifying multiple arguments, separate them with 『，』.

- Example: y ← 二乗 (x) (The square of x is assigned to y.)
- Example: z ← 二乗 (x) ＋ べき乗 (x，y) (The sum of the square of x and x raised to the power of y is assigned to z.)
- Example: r ← 乱数 (1，6) (One of the integers from 1 to 6 is assigned to r.)

### 6.2 Functions that Do Not Return a Value

In the problem statement,

- Provide a function 「二進で表示する」 that displays the specified value in binary representation

functions that do not return a value may be defined as above.

- Example: 二進で表示する (11) (「1011」 is displayed.)

## 7 Defining New Functions

The definition of a new function is written using DNCL as follows.

《General Form》
```
関数 〈関数名〉 ( 〈引数列〉 ) を
  〈処理〉
と定義する
```

The values provided as arguments when the function is called are used via the variable names written in the argument list. When specifying multiple arguments, they are separated by `,`. The defined function can be called using the same notation as calling provided functions (Section 6).

- Example: An example definition of the function "和を表示する (n)" that displays the sum from 1 to a positive integer n.

```
関数 和を表示する (n) を
  wa ← 0
  i を 1 から n まで 1 ずつ増やしながら，
    wa ← wa＋ i
  を繰り返す
  wa を表示する
と定義する
```

- Example: An example definition of the function "べき乗を表示する (m，n)" that displays the value of m to the power of n.

```
関数 べき乗を表示する (m，n) を
  p ← 1
  i を 1 から n まで 1 ずつ増やしながら，
    p ← p × m
  を繰り返す
  p を表示する
と定義する
```

## reference

- [Explanation of the Common Test Standard Language for Procedure Description (DNCL), National Center for University Entrance Examinations, January 2022](https://www.dnc.ac.jp/albums/abm.php?d=67&f=abm00000819.pdf&n=R4_%E5%85%B1%E9%80%9A%E3%83%86%E3%82%B9%E3%83%88%E6%89%8B%E9%A0%86%E8%A8%98%E8%BF%B0%E6%A8%99%E6%BA%96%E8%A8%80%E8%AA%9E%EF%BC%88DNCL%EF%BC%89%E3%81%AE%E8%AA%AC%E6%98%8E.pdf)
