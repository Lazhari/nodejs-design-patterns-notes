# The prototype pattern

> **Intent:** "Specify the kind of object to create using prototypical instance, and create new objects by copying this prototypes" -- Design Patterns: Elements of Reusable Object-Oriented Software

```javascript
// Shopper.js
class Shopper {
  constructor(name = "unnamed person") {
    this._name = name;
    this._shoppingList = [];
  }

  set name(value) {
    this._name = value;
  }

  get name() {
    return this._name;
  }

  get shoppingList() {
    return this._shoppingList.join(", ");
  }

  addItemToList(item) {
    this._shoppingList.push(item);
  }

  clone() {
    const proto = Object.getPrototypeOf(this);
    const cloned = Object.create(proto);

    cloned._name = this._name;
    cloned._shoppingList = [...this._shoppingList];

    return cloned;
  }
}

module.exports = Shopper;
```

```javascript
//scout_prototype.js

const Shopper = require("./Shopper");

const scout = new Shopper();
scout.addItemToList("camping knife");
scout.addItemToList("tent");
scout.addItemToList("backpack");
scout.addItemToList("map");

module.exports = scout;
```

```javascript
//index.js
const scout_prototype = require("./scout_prototype");

const alex = scout_prototype.clone();
alex.name = "Alex Banks";
alex.addItemToList("slingshot");

const eve = scout_prototype.clone();
eve.name = "Eve Porcello";
eve.addItemToList("reading light");

console.log(`${alex.name}: ${alex.shoppingList}`);
console.log(`${eve.name}: ${eve.shoppingList}`);
```
