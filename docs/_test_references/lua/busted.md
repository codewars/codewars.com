---
title: busted
language: lua

basic_setup: |-
  ```lua
  local t = {}
  function t.add(a, b)
    return a + b
  end
  return t
  ```

  ```lua
  local t = require 'solution'
  describe("add(a, b)", function()
    it("should add numbers", function()
      assert.are.same(2, t.add(1, 1))
    end)
  end)
  ```
---

# {{ page.title }}

[busted](https://olivinelabs.com/busted/) can be used to test Lua code.

## Basic Setup

{{ page.basic_setup | markdownify }}
