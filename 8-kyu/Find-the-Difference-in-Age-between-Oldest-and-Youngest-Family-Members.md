# [Find the Difference in Age between Oldest and Youngest Family Members](https://www.codewars.com/kata/5720a1cb65a504fdff0003e2)

At the annual family gathering, the family likes to find the oldest living family member’s age and the youngest family member’s age and calculate the difference between them.

There will be an array of all the family members' ages, in any order. The ages will be given in whole numbers, so a baby of 5 months, will have an ascribed ‘age’ of 0. Return a new array (a tuple in Python) with [youngest age, oldest age, difference between the youngest and oldest age].

## Syntax

> differenceInAges(`array`) -> `array`

### Parameters

**ages**: `array`

- The array contains natural numbers

### Return Value: `array`

The output will be an array with 3 elements.

## Examples

This function's behavior is relatively simple to understand. This exercise didn't include complicated edge cases.

Example 1:

```js
const ages = [82, 15, 6, 38, 35];
const result = differenceInAges(ages);
console.log(result); // [6, 82, 76]
```

Example 2:

```js
const ages = [62, 19, 26, 0, 55];
const result = differenceInAges(ages);
console.log(result); // [0, 62, 62]
```

Example 3:

```js
const ages = [57, 99, 14, 32];
const result = differenceInAges(ages);
console.log(result); // [14, 99, 85]
```

---

---

## [slicklash](https://www.codewars.com/users/slicklash)

```js
function differenceInAges(ages) {
  let max = Math.max(...ages),
    min = Math.min(...ages);
  diff = max - min;

  return [min, max, diff];
}
```

### Strategy

This solution has been chosen as the best practice. The strategy is simply finding the maximum and minimum argument mathematically.

### Implementation

**Spread syntax (...)**: This function allows an iterable such as an array expression or string to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected.

**Math.max()**: The function returns the largest of the zero or more numbers given as input parameters.

**Math.min()**: The function returns the smallest of the zero or more numbers given as input parameters.

**let...,...**: The coma is used to assign more than one variable with one `let`

### Possible Refactors

This strategy could also be implemented with these Implementation ...

- Math.min.apply(null, ages) or Math.max.apply(null, ages) could have been used

## Notes

The solution is perfectly clean and understandable. Very good use of spread syntax. I would have named the variables 'max and min' as 'oldest and youngest', though.

---

## [andorey](https://www.codewars.com/users/andorey)

```js
function differenceInAges(ages) {
  let x = ages.sort((a, b) => a - b)[0];
  let y = ages.sort((a, b) => a - b)[ages.length - 1];
  return [x, y, y - x];
}
```

### Strategy

The strategy of andorey is finding the lowest and greatest values by remapping the array by sorting. Then the first element of the array is the lowest and the last element is the greatest value.

### Implementation

Although the implementation is harder to read. The code is pretty short.

**.sort((a, b) => a - b)**: The sort() method sorts the elements of an array in place and returns the sorted array. The default sort order is ascending, built upon converting the elements into strings, then comparing their sequences of UTF-16 code units values. In order to order numbers in ascending order we need to add '(a, b) => a - b'.

**Array access by index**: It was used to access the first and the last element of the array

**.length - 1**: It was used to access the last element of the array.

### Possible Refactors

This strategy could also be implemented with these Implementation ...

- oldest could have been accessed by `ages.pop()`

---

## Notes

I have learned a lot about `sort` function which, I think, is very useful.
