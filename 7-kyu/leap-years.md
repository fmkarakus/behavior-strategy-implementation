# [Leap years](https://www.codewars.com/kata/526c7363236867513f0005ca)

In this function you should simply determine, whether a given year is a leap year or not. Here are the rules:

- years divisible by 4 are leap years
- but years divisible by 100 are not leap years
- but years divisible by 400 are leap years

## Syntax

> isLeapYear(`number`) -> `boolean`

### Parameters

**year**: `number`

- The input is a year

### Return Value: `boolean`

Return value is 'true' if the year is a leap year, otherwise it is 'false'

## Examples

This function's behavior is relatively simple to understand. This exercise didn't include complicated edge cases.

Example 1:

```js
const year = "2020";
const result = isLeapYear(`year`);
console.log(result); // True
```

Example 2:

```js
const year = "1600";
const result = isLeapYear(`year`);
console.log(result); // True
```

Example 3:

```js
const year = "2100";
const result = isLeapYear(`year`);
console.log(result); // False
```

---

---

## [cloggy45](https://www.codewars.com/users/cloggy45)

```js
function isLeapYear(year) {
  return (year % 100 !== 0 && year % 4 === 0) || year % 400 === 0;
}
```

### Strategy

This solution has been chosen as the best practice. The strategy is simply checking whether the number is divisible by 4, 100 and 400.

### Implementation

**&& operator**: This operator checks whether the first value is 'false', otherwise returns the second value.

**|| operator**: This operator checks whether the first value is 'true', otherwise returns the second value.

**% operator**: Finds the remainder. So also checks divisibility.

### Possible Refactors

This strategy could also be implemented with these Implementation ...

- Nested if statements could have been used

## Notes

Here the tricky part was that the number which is divisible by 100 is not a leap year, but the number which is divisible by 400 is. A number which is divisible by 400 is also divisible by 4 and 100. Proper use of parentheses and `&&` and `||` fixes the issue.

---

## [TNCodeMonkey](https://www.codewars.com/users/TNCodeMonkey)

```js
function isLeapYear(a) {
  return new Date(a, 1, 29).getMonth() == 1;
}
```

### Strategy

The strategy of TNCodeMonkey is completely different. He/she lets the javascript do the calculation by using Date function. He/she simply asks whether the 29th of February of that year is in February!

### Implementation

**new Date(year, month, day)**: The Date object is used to work with dates and times.
Date objects are created with `new Date()`.

**.getMonth()**: Javascript date getMonth() method returns the month in the specified date according to local time. The value returned by getMonth() is an integer between 0 and 11. 0 corresponds to January, _1 to February_, and so on.

### Possible Refactors

This strategy could also be implemented with these Implementation ...

- using the same function we could have checked whether 31st of December is the 366th day

---

## Notes

I have learned about `new Date` and `getMonth()` properties. Interestingly `getMonth()` gives out 29th of February for non-leap years as 2 which is in fact March.
