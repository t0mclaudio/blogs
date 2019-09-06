# Common Javascript Design Patterns

What first are immediately invoked function expressions(IIFE)?
  
A design pattern where we create a wrapper for a module so that its variables are local and protected inside that scope and does not spill outside its environment. It is usually assigned to a variable, and when the vairable is called it immediately invokes the instantiation of the function.
  
  e.g. 
  ```js
    const expression = (() => {
     let _variable = null;
      return {}
    })(); // <- instantiates when called
  ```
  
How are functions expressions and functions declarations written differently?

Function Declaration
``` js
  function test() {
    //code here
  }

```

Function Expression
```js
  const test = () => { 
    //code here
  }
```

## Module Pattern

```js
const Product = ( () => {
  let _name = "Name"
  let _addName = (n) => {
    _name = n
  }
  
  return {
    assignName: (n) => {
      _addName(n)
    }
  }
})()

var NewProduct = Product()
NewProduct.assignName("Iphone 7");
```
