---
layout: slidedeck
title: Unit Testing Slides
---

{% highlight html %}
name: inverse
layout: true
class: center, middle, inverse

---

# Unit Testing

.title-logo[![Red logo](/public/img/red-logo-white.svg)]

---
layout: false

# What is a Test

- Think back to high school, why did you have quizzes?

- Were some quizzes better than others? Why?

- How are quizzes similar to **unit tests**?

---

# Why Test

Have a conversation about the following quotes. Share your thoughts and opinions with others.

---
class: middle

 > If you don’t like testing your product, most likely your customers won’t like to test it either. (Anonymous)

 > If McDonalds were managed like a software company, 1 out of every 100 Big Macs would give you food poisoning, and the response would be, ‘We’re sorry, here’s a coupon for two more.’ (Mark Minasi)

> A good programmer is someone who always looks both ways before crossing a one-way street. (Doug Linder)

---
class: middle

> Why do we never have time to do it right, but always have time to do it over? (Murphy’s Law)

> Engineers call them edge cases. I call them: what our users do. (Anonymous)

> If you're not testing code that people are paying you money to write you deserve to be fired. (Rob Conery)

---
class: middle center

# Testing Basics

> Reminds me of the awesome bug report I saw once: ‘Everything is broken. Steps to reproduce: do anything. Expected result: it should work’. (Felipe Knorr Kuhn)

### What are the four parts every test needs?

---

# Testing Basics

1. Setup
2. Expected
3. Result
4. Assert Expected === Result

---

### Test Example 1

Fill in the blanks with a partner.

1. Put toast in the toaster. Pressed the button.
2. Expected: (    )
3. Result: (    )

4. FAIL: Expected (    ), but got (   ).

---

### Test Example 2

Fill in the blanks with a partner.

1. Studied programming every day for 2 years.
2. Expected: (   )
3. Result: (   )

4. FAIL: Expected (   ), but got (   ).

---

# Types of Testing

There are many different types of testing. We will primarily look at two.

- Unit - test individual parts
- E2E - "end to end", test complete application

[See More](http://www.softwaretestinghelp.com/types-of-software-testing/)

---

# Unit Test

A basic unit test.

```js
function addOne(x) {
  return x + 1;
}


// Test: check the console
const result = addOne(1);
const expected = 2;
console.log('Test Passes?', result === expected);
```

---

# JS Test Frameworks

Testing frameworks may writing and organizing tests easy.

- [Mocha](http://mochajs.org/)
- [Jasmine](http://jasmine.github.io/)
- [QUnit](https://qunitjs.com/ja)
- [Ava](https://github.com/avajs/ava)
- [Jest](https://facebook.github.io/jest/)

---

![Ava](https://github.com/avajs/ava/raw/master/media/header.png)

Why Choose Ava?

ES2015, concurrent tests, easiest syntax, CLI

---
class: middle

# Ava Setup

1. `npm install -g ava`
2. new directory, run `npm init`
3. run `ava --init`

---

# First Test

Create the following file and test.

/test/logic.js

```js
// 1. load test framework
import test from 'ava';

// 2. write test
test(t => {
  const expected = true;
  const result = true;
  // 3. assertion
  t.is(expected, result);
});
```

---

# TDD

Write the following test.

/test/logic.js

```js
import test from 'ava';
// import file to test
import { add } from '../src';

test(t => {
  const expected = 3;
  const result = add(1, 2);
  t.is(result, expected);
});
```

---

# "Red/Green" Testing

1. **FAIL** *(red)*: run the test: `ava`.

2. **PASS** *(green)*: write working code.

Why is important to write failing tests first?

---

# Watch Tests

Setup Ava with [watch mode](https://github.com/avajs/ava/blob/master/docs/recipes/watch-mode.md).

---

# Second Test

Write a second test. Make it pass.

```js
test(t => {
  const expected = 1;
  const result = add(1);
  t.is(result, expected);
});
```

---

# Third Test

Write a third test. Make it pass.

```js
test(t => {
  const expected = 6;
  const result = add(1, 2, 3);
  t.is(result, expected);
});
```

---
template: inverse

# TDD

---

# TDD

This process of writing tests first is called **Test Driven Development**.

1. add a test
2. run tests, new test should fail
3. write code to make the test pass
4. run tests, see them pass
5. refactor code

---
template: inverse

# BDD

---

# BDD

**Behavior Driven Development** is like TDD, but for humans.

Tests have descriptive failure messages.

/test/logic.js

```js
test('add should sum two numbers', t => {
  const expected = 3;
  const result = add(1, 2);
  t.is(result, expected);
});
```

---
class: middle

## Challenge

1. Give proper test descriptions to each of your tests.

---
class: middle

### What makes a good test description?

---

### What makes a good test description?

- source of problem is clear if fails
- "should", "shouldn't" statement

---
template: inverse

# Testing Gotchas

---
## Test Challenge #1

Add the following test to "test/index.js".<br />
Make it PASS.

/src/index.js

```js
test('should add an item to the array', t => {
  const expected = [1, 2, 3];
  const result = add([1, 2], 3);
  // test equality
});
```
---

# Problem: Test Challenge #1

Reference vs. Value Equality

```js
true === true // true
'a' === 'a' // true
[1, 2, 3] === [1, 2, 3] // false
{ a: 1 } === { a: 1 } // false
```

---

# Solution: Test Challenge #1

Use `is` for simple reference equality.

`t.is(true, true) // true`

Use `deepEqual` for value equality.

`t.deepEqual([1, 2, 3], [1, 2, 3]) // true`

---

## Test Challenge #2

Add the following test to "test/index.js".<br />
Make it PASS.

/src/index.js

```js
test('function returns 42 after 1 second', t => {
  const expected = 42;
  const result = waitOneSecondAndReturn42();
  t.is(expected, result);
});
```
---

# Problem: Test Challenge #2

The tests completes before the code is completed.

```js
function waitOneSecondAndReturn42() {
  return setTimeout(() => 42, 1000);
}

test('function returns 42 after 1 second', t => {
  const expected = 42;
  const result = waitOneSecondAndReturn42();
  t.is(expected, result);
});
```

---

# Solution: Test Challenge #2

Use `async` & `await` to return a value after the function completes. 

```js
test('function returns 42 after 1 second', async t => {
  const expected = 42;
  const result = await waitOneSecondAndReturn42();
  t.is(expected, result);
});
```

*Note: this may require a babel preprocessor*

---

# Difficult to Test

What can make code hard to test?

---

# Difficult to Test

- many side effects
- functions that do too much
- globals

---
# Hard To Test

Why is `redirectTo` hard to test?

```js
function redirectTo(url) {
  switch (url.charAt(0)) {
    case '#': window.location.hash = url; break;
    case '/': window.location.pathname = url; break;
    default: window.location.href = url;
  }
}
```

---

# Easier to Test

Why is `getRedirectPart` easy to test?

```js
function getRedirectPart(url) {
  switch (url.charAt(0)) {
    case '#': return 'hash';
    case '/': return 'pathname';
    default: return 'href';
  }
}

function redirectTo(url) {
	window.location[getRedirectPart(url)] = url;
}
```

---
class: middle

## Challenge

1. Write a tests for some of your previous logic code.

---

# Testing Redux

1. Write the following reducer.

/test/redux.js

```js
test('reducer returns 0 on start', t => {
  const result = reducer(0, {});
  const expected = 0;
  t.is(result, expected);
});

test('reducer defaults to state', t => {
  const action = { type: 'NULL' };
  const result = reducer(0, action);
  const expected = 0;
  t.is(result, expected);
});

test('reducer adds one to the total', t => {
  const action = { type: 'ADD_ONE' };
  const result = reducer(0, action);
  const expected = 1;
  t.is(result, expected);
});
```

---

# Limitations of Testing

Discuss with a partner what you think the following quote means.

> Program testing can be a very effective way to show the presence of bugs, but is hopelessly inadequate for showing their absence. (Edsger Dijkstra)

---
class: middle

## Challenge

1. Write tests for your reducers.

{% endhighlight %}
