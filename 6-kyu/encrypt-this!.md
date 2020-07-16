# [Encrypt this!](https://www.codewars.com/kata/5848565e273af816fb000449)

This function is used to create secret messages depending on the following rules;

1. Your message is a string containing space separated words.
1. You need to encrypt each word in the message using the following rules:
   1. The first letter needs to be converted to its ASCII code.
   1. The second letter needs to be switched with the last letter
1. Keepin' it simple: There are no special characters in input.

## Syntax

> encryptThis(`string`) -> `string`

### Parameters

**string**: `string`

- Any given string of words

### Return Value: `string`

The output will be the text which has been encrypted according to the rules.

## Examples

This function's behavior is relatively simple to understand. This exercise didn't include complicated edge cases.

Example 1:

```js
const string = ["Hello"];
const result = encryptThis(string);
console.log(result); // "72olle"
```

Example 2:

```js
const string = ["good"];
const result = encryptThis(string);
console.log(result); // "103doo"
```

Example 3:

```js
const string = ["hello world"];
const result = encryptThis(string);
console.log(result); // "104olle 119drlo"
```

---

---

## [notwaving](https://www.codewars.com/users/notwaving)

```js
const encryptThis = (text) =>
  text
    .split(" ")
    .map((word) =>
      word
        .replace(/(^\w)(\w)(\w*)(\w$)/, `$1$4$3$2`)
        .replace(/^\w/, word.charCodeAt(0))
    )
    .join(" ");
```

### Strategy

This solution has been chosen as the best practice. The strategy is applying the encryption rules on each word using higher order functions.

### Implementation

Firstly she has turned the text into an array of words. Then each word is modified using `.map()` and `.replace()` functions. Then the array is turned into text by simply joining.

**split()**: The function is used to turn text into array of words

**map()**: The function is used to encrypt each word in the array

**replace()**: The replace() method is used to rearrange the characters according to the rules

**regular expression: (^\w)**: finds the first character

**regular expression: (\w)**: finds the next character

**regular expression: (\w\$)**: finds the last character

**regular expression: (\w\*)**: finds the remaining characters

**regular expression: `$1$4$3$2`**: reordering previously defined characters

**.charCodeAt()**: This returns ASCII code of the selected character.

**join()**: The function is used to turn sorted array in to a string

### Possible Refactors

This strategy could also be implemented with these Implementation ...

- code can be written in a single line, but readability will then decrease.

## Notes

The strategy is easy to understand but I had difficulty to understand the regular expressions. There are very useful but for me difficult to grasp.

---

## [phatcabbage](https://www.codewars.com/users/phatcabbage)

```js
const encryptWord = (w) => {
  const first = w.charCodeAt(0);
  let res;
  switch (w.length) {
    case 0:
      return "";
    case 1:
      return first;
    case 2:
      res = [first, w[1]];
      break;
    case 3:
      res = [first, w[2], w[1]];
      break;
    default:
      res = [first, w.slice(-1), w.slice(2, -1), w[1]];
      break;
  }
  return res.join("");
};

const encryptThis = (text) => text.split(" ").map(encryptWord).join(" ");
```

### Strategy

_phatcabbage_, firstly defined a new function that encrypts a word. This function uses conditions according to the number of letters in the word. Then he uses this function to encrypt all the words of the text

### Implementation

The new function uses `switch` statement for different cases which are the number of letters. The main funtions simply `split`s, `map`s using the new function and then `join`s.

**.charCodeAt()**: This returns ASCII code of the selected character.

**switch**: The switch statement is used to perform different actions based on different conditions. In this case, the different number of letters.

**.slice()**: The slice() method extracts parts of a string and returns the extracted parts in a new string.

**.split()**: The function is used to turn text into array of words

**.map()**: The function is used to encrypt each word in the array

**.join()**: The function is used to turn sorted array in to a string

### Possible Refactors

This strategy could also be implemented with these Implementation ...

- instead of `switch`, nested _if_ statements can be used

- `replace` function could have been used.

---

## Notes

The code is easy to read, understandable. I have practiced `switch` and `slice()` here.
