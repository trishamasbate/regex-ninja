# Regex Tutorial: Matching a Hex Value 🎨

Welcome to this brief yet insightful guide on matching hex values with regex! ✨
<br>
If you have ever needed to identify those essential color codes like `#FF5733`, you are in the right place. By the end, you will have the skills to use regex for accurately capturing hex values, adding a valuable tool to your coding arsenal.

## Summary

***The Regex in this Tutorial:***

```
/^#?([a-f0-9]{6}|[a-f0-9]{3})$/
```

In this tutorial, we'll explore a simple regex pattern designed to match hex values, typically used for color codes in web development. We’ll break down each component: the # symbol, the character classes for matching digits and letters, and the quantifiers that allow for both 3 and 6 character hex codes. By the end, you'll understand how each part of this regex contributes to accurately identifying valid hex values.

## Table of Contents

- [Regex Tutorial: Matching a Hex Value 🎨](#regex-tutorial-matching-a-hex-value-)
  - [Summary](#summary)
  - [Table of Contents](#table-of-contents)
  - [Regex Components](#regex-components)
    - [📌 Anchors](#-anchors)
      - [Two Main Types of Anchors:](#two-main-types-of-anchors)
      - [Examples of How Anchors Work:](#examples-of-how-anchors-work)
    - [📌 Quantifiers](#-quantifiers)
      - [Common Quantifiers in Regex:](#common-quantifiers-in-regex)
    - [📌 OR Operator](#-or-operator)
    - [📌 Character Classes](#-character-classes)
    - [📌 Bracket Expressions](#-bracket-expressions)
    - [📌 Greedy and Lazy Match](#-greedy-and-lazy-match)
  - [Author](#author)

## Regex Components

### 📌 Anchors

**/`^`#?([a-f0-9]{6}|[a-f0-9]{3})`$`/**

Regular expressions (regex) are versatile tools for pattern matching in text, and understanding anchors is key to their effective use. Anchors, represented by ^ and $, define where a pattern should match within a string—either at the start, end, or both.

#### Two Main Types of Anchors:
1. **Start Anchor `^`**: Denotes that a string must begin with the characters immediately following it.
2. **End Anchor `$`**: Denotes that a string must end with the characters immediately preceding it.

#### Examples of How Anchors Work:

- **Caret `^` Matching the Start of the String**: The regex `^a` matches the string `abc`. The caret ^ matches the position before the first character. In this case, it matches the position right before `a`, making the regex successful.

- **Caret `^` Failing to Match**: The regex `^b` does not match the string `abc`. The caret ^ tries to match the position right before the first character. Since `b` is not at the start of the string, the regex does not find a match.

- **Dollar Sign `$` Matching the End of the String** : The regex `c$` matches the string `abc`. The dollar sign $ matches the position right after the last character. Here, it successfully matches the position after c at the end of the string.

- **Dollar Sign `$` Failing to Match**: The regex `a$` does not match the string `abc`. The dollar sign $ attempts to match the position after the last character. Since `a` is not at the end of the string, the regex does not find a match.

- **Attempting to Match a String with Extra Characters**: The regex `^#?([a-f0-9]{6}|[a-f0-9]{3})$` does not match `#1a2b3c something`. The extra text after the valid hex code violates the $ anchor, which requires the string to end immediately after the hex characters.

These examples demonstrate how anchors are crucial in ensuring that the regex pattern accurately matches only valid hex values, without allowing for any extraneous characters and helping to "anchor" the match at specific points in the string. This precision is essential for reliable pattern matching, especially when validating hex color codes.

### 📌 Quantifiers

**/^#`?`([a-f0-9]`{6}`|[a-f0-9]`{3}`)$/**

Quantifiers are symbols that tell the pattern how many times the character or group of characters right before them should show up in the text to make a match. They let you control whether a character should appear a specific number of times or within a certain range of repetitions.

In the regex pattern `/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`, the `#` symbol specifically matches the literal # character, which is commonly used at the beginning of hex color codes in web development (e.g., #1a2b3c).

The `?` following the `#` makes it optional, meaning that the pattern can match a string whether or not it includes the #. For example, it will match both #1a2b3c and 1a2b3c.

#### Common Quantifiers in Regex:
-  Asterisk or `*` : Matches zero or more occurrences of the preceding element. So, `a*` matches `a`, `aa`, and an empty string.

- Plus or `+` : Matches one or more occurrences of the preceding element. So, `a+` matches `a`, `aa`, but not an empty string.

- Question Mark or `?` : Matches zero or one occurrence of the preceding element, making it optional. So, `a?` matches `a` and an empty string, but not `aa`.

- Curly Braces or `{n}` : Matches exactly n occurrences of the preceding element. So, `a{3}` matches `aaa` but not `aa` or `aaaa`.

- Curly Braces with Lower Bound or `{n,}` : Matches n or more occurrences of the preceding element. So, `a{2,}` matches `aa`, `aaa`, and so on.

- Curly Braces with Range or `{n,m}` : Matches between n and m occurrences of the preceding element. So, `a{2,4}` matches `aa`, `aaa`, and `aaaa`, but not `a` or `aaaaa`.

### 📌 OR Operator

**/^#?([a-f0-9]{6}`|`[a-f0-9]{3})$/**

The `|` symbol is the OR operator. It acts as a logical OR, meaning it allows the regex to match one pattern or another.

In this specific case:

- **[a-f0-9]{6}** matches exactly six characters that can be any combination of the hexadecimal digits a through f and 0 through 9.
- **[a-f0-9]{3}** matches exactly three characters that can be any combination of those same hexadecimal digits.
  
The OR operator `|` in the pattern allows the regex to match either a 6-character hex value or a 3-character hex value. So, this regex can successfully match both full-length hex color codes (like #1a2b3c) and shorthand hex codes (like #1a2).

### 📌 Character Classes

**/^#?(`[a-f0-9]`{6}|`[a-f0-9]`{3})$/**

Character classes are a way to define a set of characters that you want to match. They are built-in shorthand notation for common sets of characters. The character class `a-f0-9` matches any single character that is either a lowercase letter from a to f or a digit from 0 to 9.

**How It Works in the Regex:**

- **[a-f0-9]{6}**: This matches exactly six characters, where each character can be any lowercase letter from a to f or any digit from 0 to 9. This is typically used to match a 6-digit hexadecimal value.

- **[a-f0-9]{3}**: Similarly, this matches exactly three characters from the same set, typically used to match a 3-digit shorthand hexadecimal value.

Character classes are useful because they allow you to specify a range or set of characters that can match at a particular position in the string, giving you flexibility in pattern matching.

### 📌 Bracket Expressions

**/^#?`([a-f0-9]{6}|[a-f0-9]{3})`$/**

Bracket expressions are similar to character classes but with a broader meaning. They define a set of characters that you want to match at a particular position in the string. Bracket expressions are enclosed in square brackets `[]`, and they allow for more complex matching possibilities by including ranges, individual characters, and even special constructs like negations.

**How Bracket Expressions Work in the Regex:**
- **a-f**: This part of the bracket expression is a range that includes all lowercase letters from a to f.
- **0-9**: This part of the bracket expression is a range that includes all digits from 0 to 9.

When combined in `[a-f0-9]`, this bracket expression tells the regex to match any one character that is either a letter from a to f or a digit from 0 to 9.

**Key Points About Bracket Expressions:**
- **Range Matching**: You can specify a range of characters using a hyphen - (e.g., a-z for all lowercase letters).
- **Multiple Characters**: You can include multiple specific characters without a range (e.g., [abc] matches a, b, or c).
- **Negation**: Adding a caret ^ at the start of a bracket expression negates it, meaning it matches any character except those specified (e.g., [^a-f] matches any character that is not between a and f).

### 📌 Greedy and Lazy Match

**/^#`?`([a-f0-9]{6}|[a-f0-9]{3})$/**

Greedy and lazy matching refer to how a regex engine processes quantifiers when trying to match a pattern in a string.

**Greedy Matching**: This is the default behavior in regex. A greedy match tries to match as much of the string as possible. When a quantifier like `*`, `+`, or `{n,m}` is used, the regex engine will expand the match as far as it can while still satisfying the pattern.

**Lazy Matching**: Also known as "non-greedy" or "reluctant" matching, a lazy match tries to match as little of the string as possible. To make a quantifier lazy, you add a `?` after it (e.g., *?, +?, {n,m}?). The regex engine will match the smallest possible portion of the string that satisfies the pattern.

In the context of the regex we have, the `?` after the `#` makes the `#` optional. However, since it's not followed by a quantifier like * or +, the concept of greedy versus lazy doesn't directly apply here. The `?` here is simply indicating that the # character may or may not be present at the beginning of the string. If the pattern were something like `^#([a-f0-9]{6}|[a-f0-9]{3})?$`, where there was a quantifier followed by a ?, then the match would be lazy. `^#([a-f0-9]{6}|[a-f0-9]{3})?$` matches the hex code but stops as soon as a match is found, if there's more content after the hex code, it wouldn't expand to include it.

## Author

📍 Follow me on Github at [Trisha Masbate](https://github.com/trishamasbate). 
<br>
Questions or Concerns? Reach out! 🙌🏻
<br>
[![github-follow](https://img.shields.io/github/followers/trishamasbate?label=Follow&logoColor=purple&style=social)](https://github.com/trishamasbate)

🔗 Deployed GitHub-Gist Link: [Regex Tutorial: Matching a Hex Value](https://gist.github.com/trishamasbate/7e3f4c35fb028b55a8f684175c5dba4e)

© 2024 [Trisha Masbate](https://github.com/trishamasbate). All Rights Reserved.