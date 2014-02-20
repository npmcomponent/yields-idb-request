*This repository is a mirror of the [component](http://component.io) module [yields/idb-request](http://github.com/yields/idb-request). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/yields-idb-request`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*

# idb-request

  Tiny IDBRequest wrapper that allows node style callbacks

## Installation

  Install with [component(1)](http://component.io):

    $ component install yields/idb-request

## Example

```js
var request = require('request');
var db = window.indexedDB;

var req = db.open('baz', 2);
request(req, function(err, e){
  var db = e.target.result;
  req = db.open('baz', 1);

  request(req, function(err, e){
    assert(err);
    assert(err.stack);
    assert('Error' == err.constructor.name);
    assert('Event' == err.e.constructor.name);
    assert('DOMError' == err.error.constructor.name);
    assert(err.message == err.error.message);
    log(err.message); // => "The requested version (1) is less than the existing version (2)."
  });
});
```

## License

  MIT
