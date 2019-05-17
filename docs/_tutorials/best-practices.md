---
title: Kata Best Practices
---

# Kata Best Practices

## Overview

The purpose of this guide is to present authors and editors with a style guide for Codewars Kata. Since its creation, hundreds of kata have been written for CodeWars. Many different people come to CodeWars looking for different kinds of challenges. Because of this, there can really be no definitive guide suitable for everyone.

However, there are general criteria that all authors should consider:

- Titles
  - [Avoid Sequential Titles](#avoid-sequential-titles)
  
- Descriptions
  - [User Proper Grammar, Punctuation and Spelling](#use-proper-grammar-punctuation-and-spelling)
  - [Be Clear](#be-clear)
  
- Content
  - [Make Sure Content is New](#make-sure-content-is-new)
  - [Simplicity](#simplicity)
  - [Follow Conventions](#follow-conventions)

- Testing
  -[Use Behavioral Driven Development (BDD) Testing](use-behavioral-driven-development-bdd-Testing)
  -[Have Full Code Coverage](have-full-code-coverage)
  -[Test for Invariants](test-for-invariants)

### Avoid Sequential Titles

Many kata authors have in their mind a linear progression through exercises they have divised. Due to the non-linear nature of CodeWars, however, people cannot be expected to follow exercises in sequence. This leads to odd circumstances where kata intended later in a sequence are approved, while earlier ones are not. It is best to simply avoid sequential exercises all together.

>However this doesn't mean that creating related kata is not encouraged. You can use a title prefix to help group related kata so that they are easy to discover. For example. Sorting Arrays: Basic Sorting & Sorting Arrays: Bubble Sort. The prefix will cause the "related kata" section to be more accurate.

### Use Proper Grammar, Punctuation and Spelling

It is important, in an albeit superficial way, that kata be written in correct English. Many people are offput by kata that do not have proper grammar and spelling. So when authoring and editing kata, it is important to keep this in mind.

The most common grammatical mistakes in English are between it's and its, as well as there, their, and they're.

In addition to following conventional grammar and English, it is recommended that kata follow the Wikipedia Manual of Style. The Manual of Style suggests to avoid:

- First and second person pronouns
- Contractions

### Be Clear

It should be clear in the instructions what the codewarrior is expected to complete in the kata. This is not always straightforward, especially for more challenging exercises. It is helpful to:

- Include all relevant details 
  - Give clear definitions of technical terms, along with references
  - Mention all of the corner cases you intend to cover in your tests
- Motivate problems using concrete examples
- Give examples of input/output pairs

In general, it is best to avoid:

- Irrelevant details
- Very abstract concepts
- Overly complex specifications

Ideally, it should only take a reader a couple of minutes to get the idea behind a kata.

### Make Sure Content is New

Something important to consider when one is writing or editing kata: Is the concept behind this kata novel?

There are many standard exercises in programming that are well represented on CodeWars. Some examples include:

- FizzBuzz 
- Fibonacci Sequences 
- Reverse 

When working on a kata, make sure to check that it has not been done already. Every new kata should ideally teach something different.

### Simplicity

A good kata should be as simple as possible. Even though there are no hard and fast rules for ensuring simplicity, however the following is recommended:

- Limit the number of corner cases tested for
- Unless specified explicitly, only test on valid inputs declared in the description
- Focus on testing for behavior, rather than implementation details

### Follow Conventions

When writing a kata it is highly recommended to follow convention. Two subject areas with a lot of conventions are mathematics and software engineering.

In mathematics, conventions often include the (generally undefined) behavior of functions over degenerate inputs. In discrete mathematics (number theory and logic) conventions are generally chosen to allow for a recursive definitions and avoid a messy base case. Other branches of mathematics follow conventions as well. Some examples include:

- Number Theory 
  - partition function, defined by convention to have p(1) = 0
  - The binomial coefficient function is defined to be zero on negative inputs
- Logic 
  - ∨∅ = ⊥ and ∧∅ = ⊤ in Lattice Theory 
  - ∏∅ = {∅} in Set Theory 
- Analysis 
  - By convention, when extending a function's domain it should follow its analytic continuations 
    - The analytic continuation of the sum of the infinite geometric series 1, r, r2, ... is 1 /(1 - r)
    - The factorial function n! has the Gamma function as its analytic continuation

In software engineering, there are numerous sources of conventions. Some examples include:

- Specifications from standards committees 
  - EMCA 262
  - W3C's recommendations
- APIs of popular libraries 
  - jQuery
  - Underscore.js
- Abstract Interfaces 
  - List and other generic interfaces in Java
  - Monads and MonadPluses from Haskell
    
### Use Behavioral Driven Development (BDD) Testing

For Clojure, Java and Haskell, Codewars uses the industry standards in test frameworks. These frameworks naturally enforce a degree of structure to how tests are written.

- Clojure uses clojure.test 
- Haskell uses hspec 
- Java uses junit 

Other languages do not enforce any structure, however. Whenever possible, tests should ideally use RSpec style block structure.

Here are examples for various CodeWars languages:

- Javascript
```javascript
var expect = require('chai').expect,
    samples = [],
    p = 0.1,
    k = 20,
    sigma = Math.sqrt(k*p*(1-p));
    
for(var i = 0; i < 1000; i++)
  samples.push(binomial_distribution_rand(p,k));

Test.describe("Sample of function follows the statistics of a binomially distributed random number generator", function(){
  Test.it("should have k*p as its mean", function() {
    var average = samples.reduce(function(a,b) {return a + b;}) / samples.length;
    expect(average).to.be.within(p*k, 3*sigma);
  });
});
```
- Coffeescript
```coffeescript
expect = require("chai").expect
samples = []
p = 0.1
k = 20
sigma = Math.sqrt(k * p * (1 - p))
i = 0

while i < 1000
    samples.push binomial_distribution_rand(p, k)
    i++

Test.describe "Sample of function follows the statistics of a binomially distributed random number generator", ->
    Test.it "should have k*p as its mean", ->
      average = samples.reduce((a, b) -> a + b) / samples.length
      expect(average).to.be.within p * k, 3 * sigma
```
- Python
```python
from math import abs, sqrt
p = 0.1
k = 20
sigma = sqrt(p * k * (1-p))
samples = [binomial_distribution_rand(p, k) for _ in range(1000)]

test.describe("Sample of function follows the statistics of a binomially distributed random number generator")
test.it("should have k*p as its mean")
sample_average = sum(samples) / len(samples)
text.expect(abs(sample_average - p*k) < 3 * sigma, "Sample average {0} should be within three sigma (where sigma = {1}) of the expected average {2}".format(sample_average, sigma, p*k))
```
- Ruby
```ruby
p = 0.1
k = 20
samples = (1..1000).map {|_| binomial_distribution_rand(p, k)}
sigma = Math.sqrt(p * k * (1-p))
describe "Sample of function follows the statistics of a binomially distributed random number generator" do
  it "should have k*p as its mean" do
     average = samples.instance_eval { reduce(:+) / size.to_f }
     Test.expect((average - p*k).abs < 3*sigma, "Sample average #{average} should be within three sigma (where sigma = #{sigma}) of the expected average #{p*k}")
  end
end
```

### Have Full Code Coverage

While it is not possible to test for every possible input, you should aim for your tests to have Full Test Coverage.

This is perhaps easiest to do in Haskell. Here is an example, curtesy of bkaes:

>Description: The dot product is usually encountered in linear algebra or scientific computing. It's also called scalar product or inner product sometimes:

>>In mathematics, the dot product, or scalar product (or sometimes inner product in the context of Euclidean space), is an algebraic operation that takes two equal-length sequences of numbers (usually coordinate vectors) and returns a single number. Wikipedia

>In our case, we define the dot product algebraically for two vectors a = \[a1, a2, …, an\], b = \[b1, b2, …, bn\] as dot a b = a1 * b1 + a2 * b2 + … + an * bn.
Your task is to find permutations of a and b, such that dot a b is minimal, and return that value. For example, the dot product of \[1,2,3\] and \[4,0,1\] is minimal if we switch 0 and 1 in the second vector.

### Test for Invariants
 
Whenever possible, it is encouraged that kata test for invariants. These are laws that a solution must obey to be correct. Some examples of common invariants include:

- Invertibility, for when a lossless transformation is required, such as marshalling/unmarshalling and compression/decompression
- Homomorphisms, such as the rules ax + y = axay
- Monoid axioms, for when a kata defines a container (such as a list or heap)
- Triangle inequalities, for when a kata defines a distance function
- Monad laws for the more exotic situations where monads are appropriate


