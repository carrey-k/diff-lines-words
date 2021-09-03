# diff-lines-words
Enhanced npm package for https://github.com/google/diff-lines-words, it supports to split text with lines or words.

[![Build Status](https://img.shields.io/travis/kangchengkun/diff-lines-words/main.svg)](https://travis-ci.org/kangchengkun/diff-lines-words)
[![Dependency Status](https://img.shields.io/david/kangchengkun/diff-lines-words.svg)](https://david-dm.org/kangchengkun/diff-lines-words)
[![NPM version](https://img.shields.io/npm/v/diff-lines-words.svg)](https://www.npmjs.com/package/diff-lines-words)
[![Known Vulnerabilities](https://snyk.io/test/github/kangchengkun/diff-lines-words/badge.svg)](https://snyk.io/test/github/kangchengkun/diff-lines-words) 

## Installation

```npm
npm install diff-lines-words
```

## API

[Source](https://github.com/google/diff-match-patch/wiki/API)

### Initialization

The first step is to create a new `diff_match_patch` object. This object contains various properties which set the behaviour of the algorithms, as well as the following methods/functions:

### diff_main(text1, text2) → diffs

An array of differences is computed which describe the transformation of text1 into text2. Each difference is an array (JavaScript, Lua) or tuple (Python) or Diff object (C++, C#, Objective C, Java). The first element specifies if it is an insertion (1), a deletion (-1) or an equality (0). The second element specifies the affected text.

```diff_main("Good dog", "Bad dog") → [(-1, "Goo"), (1, "Ba"), (0, "d dog")]```

Despite the large number of optimisations used in this function, diff can take a while to compute. The `diff_match_patch.Diff_Timeout` property is available to set how many seconds any diff's exploration phase may take. The default value is 1.0. A value of 0 disables the timeout and lets diff run until completion. Should diff timeout, the return value will still be a valid difference, though probably non-optimal.

### diff_lines(text1, text2) → diffs

```diff_lines("Bad dog.\n Good cat", "Bad dog.\n Bad cat") → [(-1, "Good cat"), (0, "Bad dog."), (1, "Bad cat")]```

### diff_words(text1, text2) → diffs

```diff_words("Good dog", "Bad dog") → [(-1, "Good"), (0, "dog"), (1, "Bad")]```

## Others

Please refer to [Source](https://github.com/google/diff-match-patch/wiki/API).

## Usage
```javascript
import DiffLinesWords from 'diff-lines-words';

const dlw = new DiffLinesWords();
const diffs2 = dlw.diff_words("Good dog", "Bad dog");
const diffs1 = dlw.diff_lines("Bad dog.\n Good cat", "Bad dog.\n Bad cat");

```

## License

  http://www.apache.org/licenses/LICENSE-2.0