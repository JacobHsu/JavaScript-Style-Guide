# Types

## Primitives

* [1.1](types.md#types--primitives) **Primitives**: When you access a primitive type you work directly on its value.

  * `string`
  * `number`
  * `boolean`
  * `null`
  * `undefined`
  * `symbol`
  * `bigint`

  ```javascript
  const foo = 1;
  let bar = foo;

  bar = 9;

  console.log(foo, bar); // => 1, 9
  ```

## Complex

* [1.2](types.md#types--complex) **Complex**: When you access a complex type you work on a reference to its value.

  * `object`
  * `array`
  * `function`

  ```javascript
  const foo = [1, 2];
  const bar = foo;

  bar[0] = 9;

  console.log(foo[0], bar[0]); // => 9, 9
  ```

[**⬆ back to top**](types.md)

{% hint style="info" %}
📖 Hints and Callouts  
[**https://docs.gitbook.com/editing-content/markdown**](https://docs.gitbook.com/editing-content/markdown)\*\*\*\*
{% endhint %}

