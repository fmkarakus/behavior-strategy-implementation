# [Vowel count](https://www.codewars.com/kata/54ff3102c1bad923760001f3)

This function return the number (count) of vowels in the given string.

## Syntax

> getCount(`string`) -> `number`

### Parameters

**str**: `string`

- Any given string of letters

### Return Value: `number`

The output will be the number (count) of vowels in the given string.

## Examples

This function's behavior is relatively simple to understand. This exercise didn't include complicated edge cases.

Example 1:

```js
const str = ["abracadabra"];
const result = getCount(str);
console.log(result); // 5
```

Example 2:

```js
const str = ["fabgcde"];
const result = getCount(str);
console.log(result); // 2
```

Example 3:

```js
const str = ["cxvzxcvmnb"];
const result = getCount(str);
console.log(result); // 0
```

---

---

## [Balkoth](https://www.codewars.com/users/Balkoth)

```js
function getCount(str) {
  return (str.match(/[aeiou]/gi) || []).length;
}
```

### Strategy

This solution has been chosen as the best practice and clever. The strategy is simply making a new string with the vowels of the given string and then measure the length of the new string.

### Implementation

_Balkoth_ has used `match` method to select vowels from the string using regular expressions. Then the length of this string is the number of vowels. These functions are used;

**match()**: The match() method retrieves the result of matching a string against a regular expression.

**/[aeiou]/gi**: This regular expression indicates the vowels. `/g` is needed to find all the matches. `/i` is needed to make the match case insensitive

**|| []**: Incase the string is empty, in order to get zero.

**.length**: the length of the new string is the number of the voels

### Possible Refactors

This strategy could also be implemented with these Implementation ...

- instead of `.match`, `.filter`
- `.replace` could be used in order to replace consonants with ''.

## Notes

The solution is perfectly clean and understandable. Very good use of regular expressions. At first glance I didn't understand `|| []` part then, I realized why it is needed.

---

## [cameronsima](https://www.codewars.com/users/cameronsima)

```js
function getCount(str) {
  var vowelsCount = 0;

  vowels = "aeiou";
  for (var i = 0; i < str.length; i++) {
    if (vowels.indexOf(str[i]) != -1) {
      vowelsCount++;
    }
  }
  return vowelsCount;
}
```

### Strategy

The strategy of _cameronsima_ is getting each letter of the string and checking whether it is in the string of vowels and count the number of occurrence.

### Implementation

At the beginning _cameronsima_ defines a string variable for the vowels; `vowels = "aeiou"`. Then using a for loop s/he checks whether each letter of the given string in the `vowels` by `.indexOf` method.

**for loop**: It was used to access each character of the string

**.indexOf()**: The indexOf() method returns the position of the first occurrence of a specified value in a string. This method returns -1 if the value to search for never occurs.

### Possible Refactors

This strategy could also be implemented with these Implementation ...

- instead of `.indexOf`, `.includes` could have been used

---

## Notes

I have solved the problem using same strategy but slightly different implementation.
