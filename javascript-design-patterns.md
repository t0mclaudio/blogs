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
**Factory**

This is used to create object, abstracting user from the implementation.

```js
 const TourPackage = (function() {
  let tourpackage;
  return {
    create: function(name, days) {
      if (days > 1) {
        tourpackage = MultiDay(name, days);
      } else {
        tourpackage = DayTour(name, days);
      }
      return tourpackage;
    }
  }
 })();
 
 MultiDay = function(name, days) {
  return { 
    name: name,
    days: days,
    type: "multiday"
  }
 }
 
 DayTour = function(name, days) {
  return {
    name: name,
    days: days,
    type: "daytour"
  }
 }
 
 T1 = TourPackage.create("Tour 1", 3);
 T2 = TourPackage.create("Tour 2", 1);
```

**Prototype**

This is used to clone an object

```js
function SmartPhonePrototype(product) {
  let _product = product
  
  return {
    clone: function() {
      let newProduct = new SmartPhone();
      newProduct.name = _product.name;
      newProduct.type = _product.type;
      
      return newProduct;
    }
  }
}

function SmartPhone() {
  let type = "Smart Phone";
  let name;
  return {
    type: type,
    setName: function(name) {
      name = name;
      console.log("New " + name + type + " created.");
    }
  }
}

var smartphone = new SmartPhone();
var prototype = new SmartPhonePrototype(smartphone);

var newPhone = prototype.clone();
newPhone.setName("Iphone 11");
```
