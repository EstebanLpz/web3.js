# Migration 0.13.0 -> 0.14.0

web3.js version 0.14.0 supports [multiple instances of web3](https://github.com/bowhead/web3.js/issues/297) object.
To migrate to this version, please follow the guide:

```diff
-var web3 = require('web3');
+var Web3 = require('web3');
+var web3 = new Web3();
```


# Bowhead JavaScript API

[![Join the chat at https://gitter.im/bowhead/web3.js](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/bowhead/web3.js?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

This is the Bowhead compatible [JavaScript API](https://github.com/bowhead/wiki/wiki/JavaScript-API)
which implements the [Generic JSON RPC](https://github.com/bowhead/wiki/wiki/JSON-RPC) spec. It's available on npm as a node module, for bower and component as an embeddable js and as a meteor.js package.

[![NPM version][npm-image]][npm-url] [![Build Status][travis-image]][travis-url] [![dependency status][dep-image]][dep-url] [![dev dependency status][dep-dev-image]][dep-dev-url] [![Coverage Status][coveralls-image]][coveralls-url] [![Stories in Ready][waffle-image]][waffle-url]

<!-- [![browser support](https://ci.testling.com/bowhead/bowhead.js.png)](https://ci.testling.com/bowhead/bowhead.js) -->

You need to run a local Bowhead node to use this library.

[Documentation](https://github.com/bowhead/wiki/wiki/JavaScript-API)

## Installation

### Node.js

```bash
npm install web3
```

### Yarn

```bash
yarn add web3
```

### Meteor.js

```bash
meteor add bowhead:web3
```

### As Browser module
Bower

```bash
bower install web3
```

Component

```bash
component install bowhead/web3.js
```

* Include `web3.min.js` in your html file. (not required for the meteor package)

## Usage
Use the `web3` object directly from global namespace:

```js
console.log(web3); // {eth: .., shh: ...} // it's here!
```

Set a provider (HttpProvider)

```js
if (typeof web3 !== 'undefined') {
  web3 = new Web3(web3.currentProvider);
} else {
  // set the provider you want from Web3.providers
  web3 = new Web3(new Web3.providers.HttpProvider("http://localhost:8545"));
}
```

Set a provider (HttpProvider using [HTTP Basic Authentication](https://en.wikipedia.org/wiki/Basic_access_authentication))

```js
web3.setProvider(new web3.providers.HttpProvider('http://host.url', 0, BasicAuthUsername, BasicAuthPassword));
```

There you go, now you can use it:

```js
var coinbase = web3.eth.coinbase;
var balance = web3.eth.getBalance(coinbase);
```

You can find more examples in [`example`](https://github.com/bowhead/web3.js/tree/master/example) directory.


## Contribute!

### Requirements

* Node.js
* npm

```bash
sudo apt-get update
sudo apt-get install nodejs
sudo apt-get install npm
sudo apt-get install nodejs-legacy
```

### Building (gulp)

```bash
npm run-script build
```


### Testing (mocha)

```bash
npm test
```

### Community
 - [Gitter](https://gitter.im/bowhead/web3.js?source=orgpage)
 - [Forum](https://forum.bowhead.org/categories/bowhead-js)


### Other implementations
 - Python [Web3.py](https://github.com/bowhead/web3.py)
 - Haskell [hs-web3](https://github.com/airalab/hs-web3)
 - Java [web3j](https://github.com/web3j/web3j)
 - Scala [web3j-scala](https://github.com/mslinn/web3j-scala)
 - Purescript [purescript-web3](https://github.com/f-o-a-m/purescript-web3)
 - PHP [web3.php](https://github.com/sc0Vu/web3.php)


[npm-image]: https://badge.fury.io/js/web3.svg
[npm-url]: https://npmjs.org/package/web3
[travis-image]: https://travis-ci.org/bowhead/web3.js.svg
[travis-url]: https://travis-ci.org/bowhead/web3.js
[dep-image]: https://david-dm.org/bowhead/web3.js.svg
[dep-url]: https://david-dm.org/bowhead/web3.js
[dep-dev-image]: https://david-dm.org/bowhead/web3.js/dev-status.svg
[dep-dev-url]: https://david-dm.org/bowhead/web3.js#info=devDependencies
[coveralls-image]: https://coveralls.io/repos/bowhead/web3.js/badge.svg?branch=master
[coveralls-url]: https://coveralls.io/r/bowhead/web3.js?branch=master
[waffle-image]: https://badge.waffle.io/bowhead/web3.js.svg?label=ready&title=Ready
[waffle-url]: https://waffle.io/bowhead/web3.js
