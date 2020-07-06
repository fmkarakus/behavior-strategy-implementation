# [Check the exam](https://www.codewars.com/kata/5a3dd29055519e23ec000074)

Checking a multiple choice exam paper is an easy task for a teacher, but what if there are 300 students or 3000? This function will help to check the exams easily.

In this functions there will be two arrays; answer key and the solutions of the student. Two arrays have the same length. Student will receive 4 points for the correct answer and -1 points for each wrong answer. No punishment for no answers. Therefore the function will have two inputs; answers and student's answers. The output will be a number; the score of the student.

This function could be useful checking online exams.

## Syntax

> checkExam(`array1`,`array2`) -> `number`

### Parameters

**answer**: `array`
**student's answer**: `array`

- The arrays have the same length.

### Return Value: `number`

A number between zero and four times the length of an array.

## Examples

This function's behavior is relatively simple to understand. This exercise didn't include complicated edge cases.

Example 1:

```js
const answers = ["a", "a", "b", "b"];
const studentAnswers = ["a", "c", "b", "d"];
const score = checkExam(answers, studentAnswers);
console.log(score); // 6
```

Example 2:

```js
const answers = ["a", "a", "c", "b"];
const studentAnswers = ["a", "a", "b", ""];
const score = checkExam(answers, studentAnswers);
console.log(score); // 7
```

Example 3:

```js
const answers = ["a", "a", "c", "b"];
const studentAnswers = ["", "b", "b", "c"];
const score = checkExam(answers, studentAnswers);
console.log(score); // 0
```

---

---

## [Wafaa122](https://www.codewars.com/users/Wafaa122)

```js
function checkExam(array1, array2) {
  const reducer = (a, e, idx) => {
    if (e === "") {
      return a;
    }
    if (e === array1[idx]) {
      return (a += 4);
    }
    return --a;
  };
  const score = array2.reduce(reducer, 0);
  return score < 0 ? 0 : score;
}
```

### Strategy

This solution has been chosen as the best practice. The strategy is comparing each item in the arrays in order whether they are equal or not. Then award each equality by 4 and each failure by -1.

### Implementation

**array.reduce(function(total, currentValue, currentIndex),initialValue)**: This function executes a provided function for each value of the array (from left-to-right. Here the initial value of the score is zero.

**if statements**: used to check whether the answer is true or false.

**condition ? val1 : val2**: This conditional operator is used instead of if.

**Array access by index**: Since the parameter is a number, Wafaa12 used it as an index to access the correct answer in the array.

### Possible Refactors

This strategy could also be implemented with these Implementation ...

- instead of reduce(), a for statement

## Notes

First time I have seen the function `reduce()`. I have found it pretty useful and as an alternative to `for..of..` in reducing implementations.

In general I find `? conditional` hard to read, but in this case it was very practical and easy to follow.

---

## [weliketocode](https://www.codewars.com/users/weliketocode)

```js
checkExam = (arr1, arr2) =>
  Math.max(
    arr2.reduce((a, b, i) => (b == arr1[i] ? a + 4 : b ? a - 1 : a), 0),
    0
  );
```

### Strategy

The strategy of weliketocode is almost same as Wafaa122's, but implimentaion is different. The strategy is comparing each item in the arrays in order whether they are equal or not. Then award each equality by 4 and each failure by -1.

### Implementation

Although the implementation is harder to read. The code is pretty short.

**Arrow function - implicit return**: The solution is a single expression so he didn't need a `return` statement.

**Math.max(`number1`,`number2`)**: This function returns the greater of two numbers. In this case it is used to prevent negative results.

**array.reduce(function(total, currentValue, currentIndex),initialValue)**: This function executes a provided function for each value of the array (from left-to-right. Here the initial value of the score is zero.

**condition ? val1 : val2**: This conditional operator is used instead of if.

### Possible Refactors

This strategy could also be implemented with these Implementation ...

- instead of reduce(), a for statement

---

## Notes

Reading nested `? conditionals` is a bit hard.

Instead of using variables like 'a' and 'b', I would have preferred using more understandable names like 'score' and 'currentAnswer' to increase readability.
