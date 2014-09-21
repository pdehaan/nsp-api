nsp-api
================================

`nsp-api` is a simple node wrapper for the Node Security Project API.

## Usage

```
// require it as a normal node.js module
var nspAPI = require('nsp-api');

// validate a module against Node Security Project database
nspAPI.validateModule(module, version, function (err, results){..});

// validate a full shrinkwrap against Node Security Project database
nspAPI.validateShrinkwrap(shrinkwrap, function (err, results){..});
```

## Example

```
var nspAPI = require('nsp-api');

nspAPI.validateModule('tunnel-agent', '0.4.0', function(err, results) {
    console.log(results);
    // undefined // (no vulnerabilities that we know, yet)
});

nspAPI.validateModule('yar', '0.1.0', function(err, results) {
    console.log(results);
    // [{
    //    title: 'Yar Denial-of-Service',
    //    author: 'Reid Burke',
    //    module_name: 'yar',
    //    publish_date: 'Mon Jun 16 2014 12:29:10 GMT-0700 (PDT)',
    //    cves: [ [Object] ],
    //    vulnerable_versions: '<2.2.0',
    //    patched_versions: '>=2.2.0',
    //    url: 'yar-DoS'
    // }]
});

```
