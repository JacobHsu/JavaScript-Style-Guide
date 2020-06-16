# Properties

## dot notation

<a name="properties--dot"></a><a name="12.1"></a>
  - [12.1](#properties--dot) Use dot notation when accessing properties. eslint: [`dot-notation`](https://eslint.org/docs/rules/dot-notation.html)

    ```javascript
    const luke = {
      jedi: true,
      age: 28,
    };

    // bad
    const isJedi = luke['jedi'];

    // good
    const isJedi = luke.jedi;
    ```

## bracket notation

  <a name="properties--bracket"></a><a name="12.2"></a>
  - [12.2](#properties--bracket) Use bracket notation `[]` when accessing properties with a variable.

    ```javascript
    const luke = {
      jedi: true,
      age: 28,
    };

    function getProp(prop) {
      return luke[prop];
    }

    const isJedi = getProp('jedi');
    ```

## exponentiation operator

  <a name="es2016-properties--exponentiation-operator"></a>
  - [12.3](#es2016-properties--exponentiation-operator) Use exponentiation operator `**` when calculating exponentiations. eslint: [`no-restricted-properties`](https://eslint.org/docs/rules/no-restricted-properties).

    ```javascript
    // bad
    const binary = Math.pow(2, 10);

    // good
    const binary = 2 ** 10;
    ```