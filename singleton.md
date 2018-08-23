# Singletons

## Singleton problem

> **Intent:** " Ensure a class only has one instance, and provide a global point of access to it." -- Design Pattern: Elements of Reusable Object-Oriented Software

## The Singletons pattern

```javascript
class Logger {
  constructor() {
    this.logs = [];
  }

  get count() {
    return this.logs.length;
  }

  log(message) {
    const timestamp = new Date().toISOString();
    this.logs.push({ message, timestamp });
    console.log(`${timestamp} - ${message}`);
  }
}

class Singleton {
  constructor() {
    if (!Singleton.instance) {
      Singleton.instance = new Logger();
    }
  }

  getInstance() {
    return Singleton.instance;
  }
}

module.exports = Singleton;
```

> Instantiate the Logger

```javascript
const Logger = require("./Logger");
const logger = new Logger().getInstance();
```

## Singletons in Node

- Logger Class

```javascript
class Logger {
  constructor() {
    this.logs = [];
  }

  get count() {
    return this.logs.length;
  }

  log(message) {
    const timestamp = new Date().toISOString();
    this.logs.push({ message, timestamp });
    console.log(`${timestamp} - ${message}`);
  }
}

module.exports = new Logger();
```

- Shopper Class

```javascript
var logger = require("./Logger");

class Shopper {
  constructor(name, money = 0) {
    this.name = name;
    this.money = money;
    logger.log(`New Shopper: ${name} has ${money} in their account.`);
  }
}

module.exports = Shopper;
```

- index.js

```javascript
var logger = require("./Logger");
var Shopper = require("./Shopper");
var Store = require("./Store");

logger.log("starting app...");

var alex = new Shopper("alex", 500);
var ski_shop = new Store("Steep and Deep Supplies", [
  {
    item: "Downhill Skis",
    qty: 5,
    price: 750
  },
  {
    item: "Knit Hat",
    qty: 20,
    price: 5
  }
]);

logger.log("finished config...");

console.log(`${logger.count} logs total`);
logger.logs.map(log => console.log(`   ${log.message}`));
```
