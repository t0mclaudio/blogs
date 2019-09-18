# Javascript design notes 

**Scoping**
This pattern is used to set local scope in a module

```js
( function PaymentProcessor() {
  ...
  })
```

**Function Declaration**
``` js
  function test() {
    //code here
  }
```

**Function Expression**
``` js
  const CashRegister = () => { 
    //code here
  }
```

**Immediately invoked function expression**
This pattern invokes the function expression immediately

```js
  const CashRegister = function() {
    ...
  }() <- instantiates when called
```

## Design Patterns

### Creational design patterns
**Module Pattern**
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
