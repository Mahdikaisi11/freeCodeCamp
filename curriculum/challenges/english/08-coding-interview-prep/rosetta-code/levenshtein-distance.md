---
id: 5a23c84252665b21eecc7ee2
title: Levenshtein distance
challengeType: 5
---

## Description
<section id='description'>
In information theory and computer science, the <strong>Levenshtein distance</strong> is a <a href="https://en.wikipedia.org/wiki/string metric">metric</a> for measuring the amount of difference between two sequences (i.e. an <a href="https://en.wikipedia.org/wiki/edit distance">edit distance</a>). The Levenshtein distance between two strings is defined as the minimum number of edits needed to transform one string into the other, with the allowable edit operations being insertion, deletion, or substitution of a single character.
Example:
The Levenshtein distance between "<strong>kitten</strong>" and "<strong>sitting</strong>" is 3, since the following three edits change one into the other, and there isn't a way to do it with fewer than three edits:
<ul>
  <li><strong>k</strong>itten &nbsp; <strong>s</strong>itten &nbsp;&nbsp; (substitution of 'k' with 's')</strong></li>
  <li>sitt<strong>e</strong>n &nbsp; sitt<strong>i</strong>n &nbsp;&nbsp; (substitution of 'e' with 'i')</strong></li>
  <li>sittin &nbsp; sittin<strong>g</strong> &nbsp;&nbsp; (insert 'g' at the end).</strong></li>
</ul>
<i>The Levenshtein distance between &nbsp; "<strong>rosettacode</strong>", &nbsp; "<strong>raisethysword</strong>" &nbsp; is  <strong>8</strong>.</i>
<i>The distance between two strings is same as that when both strings are reversed.</i>
</section>

## Instructions
<section id='instructions'>
Write a function that returns the Levenshtein distance between two strings given as parameters.
</section>

## Tests
<section id='tests'>

``` yml
tests:
  - text: <code>levenshtein</code> should be a function.
    testString: assert(typeof levenshtein == 'function', '<code>levenshtein</code> should be a function.');
  - text: <code>levenshtein("mist", "dist")</code> should return a number.
    testString: assert(typeof levenshtein("mist", "dist") == 'number', '<code>levenshtein("mist", "dist")</code> should return a number.');
  - text: <code>levenshtein("mist", "dist")</code> should return <code>1</code>.
    testString: assert.equal(levenshtein("mist", "dist"), 1, '<code>levenshtein("mist", "dist")</code> should return <code>1</code>.');
  - text: <code>levenshtein("tier", "tor")</code> should return <code>2</code>.
    testString: assert.equal(levenshtein("tier", "tor"), 2, '<code>levenshtein("tier", "tor")</code> should return <code>2</code>.');
  - text: <code>levenshtein("kitten", "sitting")</code> should return <code>3</code>.
    testString: assert.equal(levenshtein("kitten", "sitting"), 3, '<code>levenshtein("kitten", "sitting")</code> should return <code>3</code>.');
  - text: <code>levenshtein("stop", "tops")</code> should return <code>2</code>.
    testString: assert.equal(levenshtein("stop", "tops"), 2, '<code>levenshtein("stop", "tops")</code> should return <code>2</code>.');
  - text: <code>levenshtein("rosettacode", "raisethysword")</code> should return <code>8</code>.
    testString: assert.equal(levenshtein("rosettacode", "raisethysword"), 8, '<code>levenshtein("rosettacode", "raisethysword")</code> should return <code>8</code>.');
  - text: <code>levenshtein("mississippi", "swiss miss")</code> should return <code>8</code>.
    testString: assert.equal(levenshtein("mississippi", "swiss miss"), 8, '<code>levenshtein("mississippi", "swiss miss")</code> should return <code>8</code>.');
```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='js-seed'>

```js
function levenshtein(a, b) {
  // Good luck!
}
```

</div>

</section>

## Solution
<section id='solution'>

```js
function levenshtein(a, b) {
  var t = [], u, i, j, m = a.length, n = b.length;
  if (!m) { return n; }
  if (!n) { return m; }
  for (j = 0; j <= n; j++) { t[j] = j; }
  for (i = 1; i <= m; i++) {
    for (u = [i], j = 1; j <= n; j++) {
      u[j] = a[i - 1] === b[j - 1] ? t[j - 1] : Math.min(t[j - 1], t[j], u[j - 1]) + 1;
    } t = u;
  } return u[n];
}
```

</section>