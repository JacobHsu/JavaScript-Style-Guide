# Iterators and Generators

## higher-order functions instead of loops

  <a name="iterators--nope"></a><a name="11.1"></a>
  - [11.1](#iterators--nope) Don’t use iterators. Prefer JavaScript’s higher-order functions instead of loops like `for-in` or `for-of`. eslint: [`no-iterator`](https://eslint.org/docs/rules/no-iterator.html) [`no-restricted-syntax`](https://eslint.org/docs/rules/no-restricted-syntax)

    > Why? This enforces our immutable rule. Dealing with pure functions that return values is easier to reason about than side effects.

    > Use `map()` / `every()` / `filter()` / `find()` / `findIndex()` / `reduce()` / `some()` / ... to iterate over arrays, and `Object.keys()` / `Object.values()` / `Object.entries()` to produce arrays so you can iterate over objects.

    ```javascript
    const numbers = [1, 2, 3, 4, 5];

    // bad
    let sum = 0;
    for (let num of numbers) {
      sum += num;
    }
    sum === 15;

    // good
    let sum = 0;
    numbers.forEach((num) => {
      sum += num;
    });
    sum === 15;

    // best (use the functional force)
    const sum = numbers.reduce((total, num) => total + num, 0);
    sum === 15;

    // bad
    const increasedByOne = [];
    for (let i = 0; i < numbers.length; i++) {
      increasedByOne.push(numbers[i] + 1);
    }

    // good
    const increasedByOne = [];
    numbers.forEach((num) => {
      increasedByOne.push(num + 1);
    });

    // best (keeping it functional)
    const increasedByOne = numbers.map((num) => num + 1);
    ```

  <a name="generators--nope"></a><a name="11.2"></a>
  - [11.2](#generators--nope) Don’t use generators for now.

    > Why? They don’t transpile well to ES5.

## function* ()

  <a name="generators--spacing"></a>
  - [11.3](#generators--spacing) If you must use generators, or if you disregard [our advice](#generators--nope), make sure their function signature is spaced properly. eslint: [`generator-star-spacing`](https://eslint.org/docs/rules/generator-star-spacing)

    > Why? `function` and `*` are part of the same conceptual keyword - `*` is not a modifier for `function`, `function*` is a unique construct, different from `function`.

    ```javascript
    // bad
    function * foo() {
      // ...
    }

    // bad
    const bar = function * () {
      // ...
    };

    // bad
    const baz = function *() {
      // ...
    };

    // bad
    const quux = function*() {
      // ...
    };

    // bad
    function*foo() {
      // ...
    }

    // bad
    function *foo() {
      // ...
    }

    // very bad
    function
    *
    foo() {
      // ...
    }

    // very bad
    const wat = function
    *
    () {
      // ...
    };

    // good
    function* foo() {
      // ...
    }

    // good
    const foo = function* () {
      // ...
    };
    ```