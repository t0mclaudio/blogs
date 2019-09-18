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
This is useful for creating modules with local protected variables, only specific methods of the modules are exposed.
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

**Singleton**
This is used where only one instance can be instantiated. e.g. Database
```js
  const Database = (function(){
    var connection;
    function connect() {
      return ConnectToDatabase();
    }
    return {
      connect: function() {
        if(!connection) {
          connection = connect();
        }
        return connection;
      }
    }
  })

```
