# The factory pattern

> **Intent:** "Define an interface for creating an object, but let subclasses decide which class to instantiate to subclasses" -- Design Patterns: Elements of Reusable Object-Oriented Software

## Implementation

- Employee Class

```javascript
const Shopper = require("./Shopper");

class Employee extends Shopper {
  constructor(name, money = 0, employer = "") {
    super(name, money);
    this.employer = employer;
    this.employed = true;
  }

  payDay(money = 0) {
    this.money += money;
  }
}

module.exports = Employee;
```

- Person Class

```javascript
class Person {
  constructor(name = "unnamed person") {
    this.name = name;
  }

  toString() {
    return JSON.stringify(this);
  }
}

module.exports = Person;
```

- Shopper Class

```javascript
const Person = require("./Person");

class Shopper extends Person {
  constructor(name, money = 0) {
    super(name);
    this.money = money;
    this.employed = false;
  }
}

module.exports = Shopper;
```

- userFactory

```javascript
const Employee = require("./Employee");
const Shopper = require("./Shopper");

const userFactory = (name, money = 0, type, employer) => {
  if (type === "employee") {
    return new Employee(name, money, employer);
  } else {
    return new Shopper(name, money);
  }
};

module.exports = userFactory;
```

- Implementation (index.js)

```javascript
const userFactory = require("./userFactory");

const alex = userFactory("Alex Banks", 100);
const eve = userFactory("Eve Porcello", 100, "employee", "This and That");

eve.payDay(100);

console.log(alex.toString());
console.log(eve.toString());
```
