---
title: Igloo
language: cpp

basic_setup: |-
  ```cpp
  int add(int a, int b) {
    return a + b;
  }
  ```

  ```cpp
  Describe(basic_tests)
  {
    It(should_add_numbers)
    {
      Assert::That(add(1, 1), Equals(2));
    }
  };
  ```

---

# {{ page.title }}

BDD style unit testing framework [Igloo](http://igloo-testing.org/) can be used to test C++ code.

## Basic Setup

{{ page.basic_setup | markdownify }}


## Assertions

An assertion in Igloo is written using the following format:

```cpp
Assert::That(actual_value, <constraint expression>);
```

where `<constraint expression>` is an expression that
`actual_value` is evaluated against when the test is executed.

See [Igloo Assertions](http://igloo-testing.org/assertions.html) for the list of available expressions.

{% comment %}

- <https://www.qualified.io/kb/languages/cpp/igloo>

{% endcomment %}
