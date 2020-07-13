# [Consecutive Letters](https://www.codewars.com/kata/5ce6728c939bf80029988b57)

This function simply checks whether a string contains consecutive letters as they appear in the English alphabet and if each letter occurs only once.

## Syntax

> solve(`string`) -> `boolean`

### Parameters

**s**: `string`

- Any given string of letters

### Return Value: `boolean`

The output will be true if the string contains consecutive letters otherwise false.

## Examples

This function's behavior is relatively simple to understand. This exercise didn't include complicated edge cases.

Example 1:

```js
const s = ["abcde"];
const result = solve(s);
console.log(result); // True
```

Example 2:

```js
const s = ["fabgcde"];
const result = solve(s);
console.log(result); // True
```

Example 3:

```js
const s = ["acde"];
const result = solve(s);
console.log(result); // False
```

---

---

## [in-dex](https://www.codewars.com/users/in-dex)

```js
function solve(s) {
  return "abcdefghijklmnopqrstuvwxyz".includes([...s].sort().join(""));
}
```

### Strategy

This solution has been chosen as the best practice. The strategy is simply checking whether the sorted text appears in the alphabet in string form.

### Implementation

in-dex has written all the alphabet and checks whether the sorted text appears in the alphabet using the following functions;

**includes()**: The includes() method determines whether an array includes a certain value among its entries, returning true or false as appropriate.

**Spread syntax (...)**: This function allows an iterable such as an array expression or string to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected.

**sort()**: The sort() method sorts the elements of an array in place and returns the sorted array. The default sort order is ascending, built upon converting the elements into strings, then comparing their sequences of UTF-16 code units values.

**join()**: The function is used to turn sorted array in to a string

### Possible Refactors

This strategy could also be implemented with these Implementation ...

- an arrow function would be shorter

## Notes

The solution is perfectly clean and understandable. Very good use of spread syntax.

---

## [jgdodson](https://www.codewars.com/users/jgdodson)

```js
function solve(s) {
  if (s.length === 1) {
    return true;
  }

  const sortedChars = s.split("").sort().join("");

  for (let i = 1; i < sortedChars.length; i++) {
    if (sortedChars.charCodeAt(i) - sortedChars.charCodeAt(i - 1) !== 1) {
      return false;
    }
  }

  return true;
}
```

### Strategy

The strategy of jgdodson is checking whether the letters are consecutive by checking their character codes, after sorting the text.

### Implementation

At the beginning an if statement checks the length of the string is 1 and return true if so. If not, firstly the string is sorted using _.split, .sort, .join_ methods. Then a _for loop_ checks whether two consecutive letters have consecutive character codes

**.split**: The split() method is used to split a string into an array of substrings, and returns the new array.

**.sort()**: The sort() method sorts the elements of an array in place and returns the sorted array. The default sort order is ascending, built upon converting the elements into strings, then comparing their sequences of UTF-16 code units values.

**join()**: The function is used to turn sorted array in to a string

**for loop**: It was used to access each character of the string

**str.charCodeAt(i) - str.charCodeAt(i - 1) !== 1)**: This expression returns true if the character codes difference is not 1, i.e. not consecutive.

### Possible Refactors

This strategy could also be implemented with these Implementation ...

- instead of _if_ in the loop we could use _&&_ and compare with previously assigned `result=true`

---

## Notes

I have solved the problem using same strategy but slightly different implementation.
