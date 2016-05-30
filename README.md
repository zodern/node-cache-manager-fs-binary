# node-cache-manager-fs-binary

Node Cache Manager store for Filesystem with binary data
========================================================

The Filesystem store for the [node-cache-manager](https://github.com/BryanDonovan/node-cache-manager) module, storing binary data as separate files, returning them as readable streams.

Installation
------------

```sh
npm install cache-manager-fs-binary --save
```

Usage examples
--------------

Here are examples that demonstrate how to implement the Filesystem cache store.


## Features

* limit maximum size on disk
* refill cache on startup (in case of application restart)

## Single store

```javascript
// node cachemanager
var cacheManager = require('cache-manager');
// storage for the cachemanager
var fsStore = require('cache-manager-fs-binary');
// initialize caching on disk
var diskCache = cacheManager.caching({store: fsStore, options: {ttl: 60*60 /* seconds */, maxsize: 1000*1000*1000 /* max size in bytes on disk */, path:'diskcache', preventfill:true}});
```

### Options

options for store initialization

```javascript

options.ttl = 60; // time to life in seconds
options.path = 'cache/'; // path for cached files
options.preventfill = false; // prevent filling of the cache with the files from the cache-directory
options.fillcallback = null; // callback fired after the initial cache filling is completed
options.zip = false; // if true the cached files will be zipped to save diskspace
options.reviveBuffers = true; // if true buffers are returned from cache as buffers, not objects
options.binaryAsStream = true; // if true, data in the binary key are returned as StreamReadable of the binary file with autoclose. You have to do the work for closing the files if you do not read them.

```
## Installation

    npm install cache-manager-fs-binary
	
## Tests

To run tests:

npm test

## Code Coverage

To run Coverage:

npm run coverage

## License

cache-manager-fs-binary is licensed under the MIT license.

Based on https://github.com/hotelde/node-cache-manager-fs
