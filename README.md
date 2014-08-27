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

var rob = new AutosaveObject(null, {
  name: 'Rob',
  age: 30
});

rob.set('age', 31); // This will write the object to redis
rob.get('name'); // returns 'Rob'


AutosaveObject.fetch().then(function (result) {
  // result will be a list containing an instance equal to rob above
});
AutosaveObject.fetch(rob.key).then(function (result) {
  // result will be an instance equal to rob above
});
```

#### Want more info?
Read the [tests](https://github.com/relekang/node-rob/blob/master/test/index.bs) or the [source](https://github.com/relekang/node-rob/blob/master/index.bs). More documentation is coming later..

--------
MIT © Rolf Erik Lekang 
