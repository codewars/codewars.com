---
title: Ginkgo
language: go

basic_setup: |-
  ```go
  package kata

  func Add(a, b int) int {
    return a + b
  }
  ```

  ```go
  package kata_test

  import (
    . "github.com/onsi/ginkgo"
    . "github.com/onsi/gomega"
    . "codewarrior/kata"
  )

  var _ = Describe("Add", func() {
    It("should add integers", func() {
      Expect(Add(1, 1)).To(Equal(2))
    })
  })
  ```

  Package name (`kata` in above example) can be arbitrary (`[a-z][a-z\d]*`) and
  the import path is `codewarrior/{package name}`.

---

# {{ page.title }}

BDD testing framework [Ginkgo](http://onsi.github.io/ginkgo/)
with [Gomega](http://onsi.github.io/gomega/) matcher library
can be used to test Go code.


## Basic Setup

{{ page.basic_setup | markdownify }}

## Matchers

[Gomega](http://onsi.github.io/gomega/) matcher library is supported.

- [Provided Matchers](http://onsi.github.io/gomega/#provided-matchers)
- [Custom Matchers](https://onsi.github.io/gomega/#adding-your-own-matchers)
