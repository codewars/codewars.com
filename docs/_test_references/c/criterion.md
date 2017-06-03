---
title: Criterion
language: c

basic_setup: |-
  ```c
  int add(int a, int b) {
    return a + b;
  }
  ```

  ```c
  #include <criterion/criterion.h>

  int add(int, int);

  Test(basic_test, should_add_numbers) {
    cr_assert_eq(2, add(1, 1));
  }
  ```

---

# {{ page.title }}

[Criterion](https://github.com/Snaipe/Criterion) can be used to test C code.
See the [documentation](https://criterion.readthedocs.io/en/master/) to learn more.

## Basic Setup

{{ page.basic_setup | markdownify }}


{% comment %}

- <https://www.qualified.io/kb/languages/c/criterion>

{% endcomment %}
