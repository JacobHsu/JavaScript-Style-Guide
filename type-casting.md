# Type Casting & Coercion

  <a name="coercion--explicit"></a><a name="21.1"></a>
  - [22.1](#coercion--explicit) Perform type coercion at the beginning of the statement.

## Strings

  <a name="coercion--strings"></a><a name="21.2"></a>
  - [22.2](#coercion--strings) Strings: eslint: [`no-new-wrappers`](https://eslint.org/docs/rules/no-new-wrappers)

    ```javascript
    // => this.reviewScore = 9;

    // bad
    const totalScore = new String(this.reviewScore); // typeof totalScore is "object" not "string"

    // bad
    const totalScore = this.reviewScore + ''; // invokes this.reviewScore.valueOf()

    // bad
    const totalScore = this.reviewScore.toString(); // isn’t guaranteed to return a string

    // good
    const totalScore = String(this.reviewScore);
    ```

## Number

  <a name="coercion--numbers"></a><a name="21.3"></a>
  - [22.3](#coercion--numbers) Numbers: Use `Number` for type casting and `parseInt` always with a radix for parsing strings. eslint: [`radix`](https://eslint.org/docs/rules/radix) [`no-new-wrappers`](https://eslint.org/docs/rules/no-new-wrappers)

    ```javascript
    const inputValue = '4';

    // bad
    const val = new Number(inputValue);

    // bad
    const val = +inputValue;

    // bad
    const val = inputValue >> 0;

    // bad
    const val = parseInt(inputValue);

    // good
    const val = Number(inputValue);

    // good
    const val = parseInt(inputValue, 10);
    ```

  <a name="coercion--comment-deviations"></a><a name="21.4"></a>
  - [22.4](#coercion--comment-deviations) If for whatever reason you are doing something wild and `parseInt` is your bottleneck and need to use Bitshift for [performance reasons](https://jsperf.com/coercion-vs-casting/3), leave a comment explaining why and what you’re doing.

    ```javascript
    // good
    /**
     * parseInt was the reason my code was slow.
     * Bitshifting the String to coerce it to a
     * Number made it a lot faster.
     */
    const val = inputValue >> 0;
    ```

## bitshift

  <a name="coercion--bitwise"></a><a name="21.5"></a>
  - [22.5](#coercion--bitwise) **Note:** Be careful when using bitshift operations. Numbers are represented as [64-bit values](https://es5.github.io/#x4.3.19), but bitshift operations always return a 32-bit integer ([source](https://es5.github.io/#x11.7)). Bitshift can lead to unexpected behavior for integer values larger than 32 bits. [Discussion](https://github.com/airbnb/javascript/issues/109). Largest signed 32-bit Int is 2,147,483,647:

    ```javascript
    2147483647 >> 0; // => 2147483647
    2147483648 >> 0; // => -2147483648
    2147483649 >> 0; // => -2147483647
    ```

## Booleans

  <a name="coercion--booleans"></a><a name="21.6"></a>
  - [22.6](#coercion--booleans) Booleans: eslint: [`no-new-wrappers`](https://eslint.org/docs/rules/no-new-wrappers)

    ```javascript
    const age = 0;

    // bad
    const hasAge = new Boolean(age);

    // good
    const hasAge = Boolean(age);

    // best
    const hasAge = !!age;
    ```
