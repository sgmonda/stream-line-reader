# stream-line-reader
An extremely efficient asynchronous line-reader for Node.js streams.

¿Have you ever tried to read a **huge remote file** line by line without having to download it? Then you'll love this module.
Just create an asynchronous line handler and let `stream-line-reader` do the work. You'll be able to process huge remote files with no memory issues.

Of course this is useful for any stream, not just remote files.

## Installation

```
npm install stream-line-reader
```

## Quick example

```javascript
var slr = require('stream-line-reader');
var reader = slr('https://s3.amazonaws.com/mediasmart-audiences/matrix-testing/mediasmart/8djtgid9yhypggydma5xfehhm.txt');

reader.on('line', function (line, callback) {
    console.log('Processing line:', line);
    setTimeout(function () { // This should be your async task
        console.log('Line processed');
        callback();
    }, 1000 * Math.random());
});

reader.on('end', function (error) {
  console.log('Finished');
});
```
