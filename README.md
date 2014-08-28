# node-rob
[![Build Status](https://travis-ci.org/relekang/node-rob.svg?branch=master)](https://travis-ci.org/relekang/node-rob)
[![Coverage Status](https://coveralls.io/repos/relekang/node-rob/badge.png)](https://coveralls.io/r/relekang/node-rob)

Autosaving objects in redis

## Installation
```
npm install --save rob
```

## Usage

```javascript
var AutosaveObject = require('rob').AutosaveObject;
var Person = AutosaveObject.extend({
  fullName: function () {
    return this.firstName + this.lastName;
  }
  keyGenerator: function () {
    // Optional custom key generator
    return this.firstName;
  }
})
var albus = new Person(null, {
  firstName: 'Albus Percival Wulfric Brian',
  lastName: 'Dumbledore'
});

albus.set('age', 116); // This will write the object to redis
albus.get('lastName'); // returns 'Dumbledore'
albus.fullName(); // returns 'Albus Percival Wulfric Brian Dumbledore'

Person.fetch().then(function (result) {
  // result will be a list containing an instance equal to rob above
});
Person.fetch(albus.key).then(function (result) {
  // result will be an instance equal to rob above
});
```

#### Want more info?
Read the [tests](https://github.com/relekang/node-rob/blob/master/test/index.bs) or the [source](https://github.com/relekang/node-rob/blob/master/index.bs). More documentation is coming later..

--------
MIT © Rolf Erik Lekang
