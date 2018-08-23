# Overview

## What are design patterns?

> Reusable, reliable solutions to problems that we face every day in software development.

Design patterns are named:

- Cataloged solutions
- Reusable in many different situations
- Well documented
- language for collaboration
- Improve architecture

Using design patterns gives you techniques to :

- Write better code
- Become a better programmer
- Make more money

## Gang of Four: Design patterns

> Design patterns: Elements of Reusable Object-Oriented Software Published 1994.

Authors:

- Erich Gamma
- Richard Helm
- Ralph Johnson
- John Vlissides

> " Each pattern describes a problem which occurs over and over again in out environment, and then describes the core of the solution to that problem, in such a way that you can use this solution a million times over, without ever doing it the same way twice"
> ** -- Christopher Alexander: A Pattern Language: Towns, Buildings, Construction**

### Design Pattern Essentials

Each design pattern most have:

- Name
- Problem
- Solution
- Consequences

### Design Patterns Categories

#### Creational

- Abstract Factory
- Builder
- Factory Method
- Prototype

#### Structural

- Adapter
- Bridge
- Composite
- Decorator
- Facade
- Flyweight
- Proxy

#### Behavioral

- Chain of Responsibility
- Command
- Interpreter
- Iterator
- Mediator
- Memento
- Observer
- State
- Strategy
- Template Method
- Visitor

#### Other Patterns

- Module
- Revealing Module
- Revealing Constructor
- Callback
- Middleware
- Reactor
- Blockchain
- Scheduler
- Published Subscriber

## Anti-Patterns

> Bad solutions that cause problems. (Code smells)

### Anti-Patterns in JavaScript

- Modifying the prototype on an instance

```javascript
person.__proto__.address = {};
```

- Syncing execution after initialization

```javascript
listen() {
    fs.readFileSync(...)
}
```

- Callback chaos

```javascript
readFile(..., () => {
    parseDate(..., () => {
        writeFile(..., () => {

        });
    });
});
```
