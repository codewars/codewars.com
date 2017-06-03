---
title: Codewars Testing Framework
language: javascript
---

# Codewars Testing Framework

The `Test` object provides the testing functionality needed to validate a kata's requirements.
It is a frozen object and cannot be modified.

## Assertions

### `Test.expect(passed[, msg])` {#expect}

Core assertion method that all other methods build off of.
`msg` argument is optional.
If it is not provided then a generic message will be used.
Best practice is to provide your own message.
Pass/Fail status will be written to the output stream.

### `Test.assertEquals(actual, expected[, msg])` {#assert-equals}

Checks that the actual value equals (`===`) the expected value.
A useful message will be displayed for both pass and fail outcomes.
The `msg` argument is optional. If given it will be displayed in addition to the typical message used.

{% comment %}

### `Test.assertNotEquals(actual, unexpected[, msg])` {#assert-not-equals}

{% endcomment %}

<h3 id="assert-not-equals"><code>Test.assertNotEquals<br class="dn-ns">(actual, unexpected[, msg])</code></h3>

Checks that the actual value does not equal (`!==`) the unexpected value.
A useful message will be displayed for both pass and fail outcomes.
The `msg` argument is optional.
If given it will be displayed in addition to the typical message used.

### `Test.assertSimilar(actual, expected[, msg])` {#assert-similar}

Checks that the actual value equals (`===`) the expected value.
[`Test.inspect`](#inspect) is used to wrap the values being tested,
allowing for similar values to be considered the same.
A useful message will be displayed for both pass and fail outcomes.
The `msg` argument is optional. If given it will be displayed in addition to the typical message used.

### `Test.assertNotSimilar(actual, unexpected[, msg])` {#assert-not-similar}

Checks that the actual value does not equal (`!==`) the unexpected value.
[`Test.inspect`](#inspect) is used to wrap the values being tested,
allowing for similar values to be considered the same.
A useful message will be displayed for both pass and fail outcomes.
The `msg` argument is optional. If given it will be displayed in addition to the typical message used.

### `Test.assertDeepEquals(actual, expected[, msg])` {#assert-deep-equals}

Checks that the actual value equals the expected value by performing deep comparison.
Unlike [`Test.assertSimilar`](#assert-similar), values are not turned into strings.
A useful message will be displayed for both pass and fail outcomes.
The `msg` argument is optional. If given it will be displayed in addition to the typical message used.

### `Test.assertNotDeepEquals(actual, unexpected[, msg])` {#assert-not-deep-equals}

Checks that the actual value does not equal the unexpected value by performing deep comparison.
Unlike [`Test.assertNotSimilar`](#assert-not-similar), values are not turned into strings.
A useful message will be displayed for both pass and fail outcomes.
The `msg` argument is optional. If given it will be displayed in addition to the typical message used.

### `Test.assertContains(actual, expected[, msg])` {#assert-contains}

Checks that the actual value contains the expected element.
A useful message will be displayed for both pass and fail outcomes.
The `msg` argument is optional. If given it will be displayed in addition to the typical message used.

### `Test.assertNotContains(actual, unexpected[, msg])` {#assert-not-contains}

Checks that the actual value does not contain the unexpected element.
A useful message will be displayed for both pass and fail outcomes.
The `msg` argument is optional. If given it will be displayed in addition to the typical message used.

### `Test.expectError([msg, ]fn)` {#expect-error}

Useful for testing that an error was expected to happen.
`msg` is optional but best practice is to provide one.

### `Test.expectNoError([msg, ]fn)` {#expect-no-error}

Useful for testing that an error was not expected to happen.
`msg` is optional but best practice is to provide one.

## Spec Methods

### `Test.describe(subject, fn)` {#describe}

Top level method for describing/grouping a set of tests.
Globally aliased as `describe`.

```javascript
describe("Foo", function() {

});

// or

Test.describe("Foo", function() {

});
```

### `Test.it(subject, fn)` {#it}

Used in conjunction with describe to group related sets of tests in a spec.
Globally aliased as `it`.

```javascript
describe("Foo", function() {
  it("should be defined", function() {
    Test.expect(this.Foo, "Foo is not defined");
  });
});
```

### `Test.before(callback)` {#before}

Any callbacks sent to this method will be called before each it spec is ran.
Globally aliased as `before`.

```javascript
// this is a contrived example
describe("Foo", function() {
  var a = 0;

  // called before each spec is ran
  before(function() {
    a++;
  });

  it("should should do something", function() {
    Test.assertEquals(a, 1);
  });

  it("should do something else", function() {
    Test.assertEquals(a, 2);
  });
});
```

## Helper Methods

### `Test.inspect(object)` {#inspect}

Returns a string representation of the object.

### `Test.randomize(array)` {#randomize}

Returns a shuffled array.

### `Test.randomNumber()` {#random-number}

Returns a random integer.

### `Test.randomToken()` {#random-token}

Returns a random string of characters.

### `Test.sample(array)` {#sample}

Returns a single, randomly chosen item from an array.

{% comment %}

- <https://www.codewars.com/docs/js-slash-coffeescript-test-reference>
- <https://www.qualified.io/kb/languages/javascript/cw-2>

- Removed `Test.callCount(methodName) → Integer`
- Added `Test.assertDeepEquals`
- Added `Test.assertNotDeepEquals`
- Added `Test.assertContains`
- Added `Test.assertNotContains`

{% endcomment %}
