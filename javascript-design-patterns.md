# Javascript design notes 

**Scoping**
This pattern is used to set local scope in a module

```js
(function PaymentProcessor() {
  ...
})
```

**Function Declaration**
``` js
  function CreditCard() {
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
const Transaction = ( () => {
  let _custname = null;
  let _createCustName = (n) => {
    _custname = n
  }
  
  return {
    enterName: (n) => {
      _createCustName(n)
    }
  }
})()

var NewTransaction = Transaction();
NewTransaction.enterName("Jonny Cash");
```
