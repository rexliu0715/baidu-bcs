[![NPM](https://nodei.co/npm/baidu-bcs.png?downloads=true)](https://nodei.co/npm/baidu-bcs/)

### baidu-bcs
* baidu bcs node.js sdk

### install
```bash
npm install baidu-bcs
```

### api
* putBucket
* listBucket
* deleteBucket
* putObject
* copyObject
* putSuperfile
* getObject
* headObject
* listObject
* deleteObject
* putAcl
* getAcl

### document

create bcs client
```js
var BCS = require('baidu-bcs');
var bcs = BCS.createClient({
  accessKey: 'your access key',
  secretKey: 'your secret key'
});

/*
 * 可选 option
 *
 * host:     default: bcs.duapp.com,
 * port:     default: 80
 * protocol: default: http:
 * timeout:  default: 300000 // 5 minutes
 * ip:       // 允许上传的ip，默认为空，即：不限制ip
 * time:     // 有效时间
 * size:     // 限制上传最大字节
 * agent:    default: agent.maxSockets = 20
 */
```

put bucket
```js
bcs.putBucket({
  bucket: '',
  acl: ''
}, function (error, result) {});
```

put bucket with acl
```js
bcs.putBucket({
  bucket: '',
  acl: ''
}, function (error, result) {});
```

list bucket
```js
bcs.listBucket(function (error, result) {});
```

delete bucket
```js
bcs.deleteBucket({
  bucket: ''
}, function (error, result) {});
```

put object with file path
```js
bcs.putObject({
  bucket: '',
  object: '',
  source: './index.js'
}, function (error, result) {});
```


put object with buffer
```js
bcs.putObject({
  bucket: '',
  object: '',
  source: new Buffer('baidu-bcs'),
  headers: {
    'Content-Type': 'text/plain'
  }
}, function (error, result) {});
```

put object with stream
```js
bcs.putObject({
  bucket: '',
  object: '',
  source: fs.createReadStream(__filename),
  headers: {
    'Content-Type': 'text/plain',
    'Content-Length': fs.statSync(__filename).size // important: the 'Content-Type' is must
  }
}, function (error, result) {});
```

put object with headers
```js
bcs.putObject({
  bucket: '',
  object: '',
  source: './index.js',
  headers: {
    'Content-Type': 'text/javascript'
  }
}, function (error, result) {});
```

copy object
```js
bcs.copyObject({
  bucket: '',
  object: '',
  sourceBucket: '',
  sourceObject: '',
  headers: {
    'Content-Type': ''
  }
}, function (error, result) {});
```

head object
```js
bcs.headObject({
  bucket: '',
  object: ''
}, function (error, result) {});
```

list object
```js
bcs.listObject({
  bucket: '',
  start: 1,
  limit: 1
}, function (error, result) {});
```

get object
```js
bcs.getObject({
  bucket: '',
  object: '',
}, function (error, result) {});
```

get object to file path
```js
bcs.getObject({
  bucket: '',
  object: '',
  dest: './xxoo.xo'
}, function (error, result) {});
```

get object to write stream
```js
var writeStream = fs.createWriteStream('./xxoo.xo')
bcs.getObject({
  bucket: '',
  object: '',
  dest: writeStream
}, function (error, result) {});
```

delete bucket
```js
bcs.deleteBucket({
  bucket: ''
}, function (error, result) {});
```

put acl
```js
bcs.putAcl({
  bucket: '',
  acl: 'private'
}, function (error, result) {});
```

get acl
```js
bcs.getAcl({
  bucket: ''
}, function (error, result) {});
```

### params note
* bucket - bucket name
* object - object name
* headers - you can set http headers by this
* sourceBucket - only for `copyObject()`
* sourceObject - only for `copyObject()`
* the `result` of callback is a object contain: `status`, `headers`, `body`

### test
coverage: 93%

### License
MIT
