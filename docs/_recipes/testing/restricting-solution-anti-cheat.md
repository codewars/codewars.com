---
title: Restricting Solution Anti-Cheat
chapter: Testing
number: 2
languages:
  - javascript
---

## Problem

Prevent certain code from being used even if the solution rewrites `solutions.txt`.

## Solution

Read `solution.txt` in preloaded section.

### JavaScript

by @10XL ([src](https://www.codewars.com/kumite/579d80d97cb1f385ed000231?sel=58e0f03292d04c7805000012))

**Preloaded Code**:

```javascript
const realSolution = require('fs').readFileSync('/home/codewarrior/solution.txt', 'utf8');
```

**Test Cases**:

```javascript
describe("Check Real Solution", function() {
  it("should prevent the '+' symbol from being used anywhere in the code", function() {
    Test.expect(realSolution.indexOf('+') == -1, "Your code isn't allowed to include the + symbol!");
  });
});
```
