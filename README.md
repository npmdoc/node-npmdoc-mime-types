# api documentation for  [mime-types (v2.1.15)](https://github.com/jshttp/mime-types#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-mime-types.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-mime-types) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-mime-types.svg)](https://travis-ci.org/npmdoc/node-npmdoc-mime-types)
#### The ultimate javascript content-type utility.

[![NPM](https://nodei.co/npm/mime-types.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/mime-types)

[![apidoc](https://npmdoc.github.io/node-npmdoc-mime-types/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-mime-types/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-mime-types/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-mime-types/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "bugs": {
        "url": "https://github.com/jshttp/mime-types/issues"
    },
    "contributors": [
        {
            "name": "Douglas Christopher Wilson"
        },
        {
            "name": "Jeremiah Senkpiel",
            "url": "https://searchbeam.jit.su"
        },
        {
            "name": "Jonathan Ong",
            "url": "http://jongleberry.com"
        }
    ],
    "dependencies": {
        "mime-db": "~1.27.0"
    },
    "description": "The ultimate javascript content-type utility.",
    "devDependencies": {
        "eslint": "3.18.0",
        "eslint-config-standard": "7.1.0",
        "eslint-plugin-promise": "3.5.0",
        "eslint-plugin-standard": "2.1.1",
        "istanbul": "0.4.5",
        "mocha": "1.21.5"
    },
    "directories": {},
    "dist": {
        "shasum": "a4ebf5064094569237b8cf70046776d09fc92aed",
        "tarball": "https://registry.npmjs.org/mime-types/-/mime-types-2.1.15.tgz"
    },
    "engines": {
        "node": ">= 0.6"
    },
    "files": [
        "HISTORY.md",
        "LICENSE",
        "index.js"
    ],
    "gitHead": "c44863eb0463ee16f3eb04576591cc4c4d6b214c",
    "homepage": "https://github.com/jshttp/mime-types#readme",
    "keywords": [
        "mime",
        "types"
    ],
    "license": "MIT",
    "maintainers": [
        {
            "name": "dougwilson"
        },
        {
            "name": "fishrock123"
        },
        {
            "name": "jongleberry"
        }
    ],
    "name": "mime-types",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+https://github.com/jshttp/mime-types.git"
    },
    "scripts": {
        "lint": "eslint .",
        "test": "mocha --reporter spec test/test.js",
        "test-cov": "istanbul cover node_modules/mocha/bin/_mocha -- --reporter dot test/test.js",
        "test-travis": "istanbul cover node_modules/mocha/bin/_mocha --report lcovonly -- --reporter dot test/test.js"
    },
    "version": "2.1.15"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module mime-types](#apidoc.module.mime-types)
1.  [function <span class="apidocSignatureSpan">mime-types.</span>charset (type)](#apidoc.element.mime-types.charset)
1.  [function <span class="apidocSignatureSpan">mime-types.</span>contentType (str)](#apidoc.element.mime-types.contentType)
1.  [function <span class="apidocSignatureSpan">mime-types.</span>extension (type)](#apidoc.element.mime-types.extension)
1.  [function <span class="apidocSignatureSpan">mime-types.</span>lookup (path)](#apidoc.element.mime-types.lookup)
1.  object <span class="apidocSignatureSpan">mime-types.</span>charsets
1.  object <span class="apidocSignatureSpan">mime-types.</span>extensions
1.  object <span class="apidocSignatureSpan">mime-types.</span>types

#### [module mime-types.charsets](#apidoc.module.mime-types.charsets)
1.  [function <span class="apidocSignatureSpan">mime-types.charsets.</span>lookup (type)](#apidoc.element.mime-types.charsets.lookup)



# <a name="apidoc.module.mime-types"></a>[module mime-types](#apidoc.module.mime-types)

#### <a name="apidoc.element.mime-types.charset"></a>[function <span class="apidocSignatureSpan">mime-types.</span>charset (type)](#apidoc.element.mime-types.charset)
- description and source-code
```javascript
function charset(type) {
  if (!type || typeof type !== 'string') {
    return false
  }

  // TODO: use media-typer
  var match = extractTypeRegExp.exec(type)
  var mime = match && db[match[1].toLowerCase()]

  if (mime && mime.charset) {
    return mime.charset
  }

  // default text/* to utf-8
  if (match && textTypeRegExp.test(match[1])) {
    return 'UTF-8'
  }

  return false
}
```
- example usage
```shell
...

Get the default extension for a content-type.

'''js
mime.extension('application/octet-stream') // 'bin'
'''

### mime.charset(type)

Lookup the implied default charset of a content-type.

'''js
mime.charset('text/x-markdown') // 'UTF-8'
'''
...
```

#### <a name="apidoc.element.mime-types.contentType"></a>[function <span class="apidocSignatureSpan">mime-types.</span>contentType (str)](#apidoc.element.mime-types.contentType)
- description and source-code
```javascript
function contentType(str) {
  // TODO: should this even be in this module?
  if (!str || typeof str !== 'string') {
    return false
  }

  var mime = str.indexOf('/') === -1
    ? exports.lookup(str)
    : str

  if (!mime) {
    return false
  }

  // TODO: use content-type or other module
  if (mime.indexOf('charset') === -1) {
    var charset = exports.charset(mime)
    if (charset) mime += '; charset=' + charset.toLowerCase()
  }

  return mime
}
```
- example usage
```shell
...
mime.lookup('file.html')        // 'text/html'
mime.lookup('folder/file.js')   // 'application/javascript'
mime.lookup('folder/.htaccess') // false

mime.lookup('cats') // false
'''

### mime.contentType(type)

Create a full content-type header given a content-type or extension.

'''js
mime.contentType('markdown')  // 'text/x-markdown; charset=utf-8'
mime.contentType('file.json') // 'application/json; charset=utf-8'
...
```

#### <a name="apidoc.element.mime-types.extension"></a>[function <span class="apidocSignatureSpan">mime-types.</span>extension (type)](#apidoc.element.mime-types.extension)
- description and source-code
```javascript
function extension(type) {
  if (!type || typeof type !== 'string') {
    return false
  }

  // TODO: use media-typer
  var match = extractTypeRegExp.exec(type)

  // get extensions
  var exts = match && exports.extensions[match[1].toLowerCase()]

  if (!exts || !exts.length) {
    return false
  }

  return exts[0]
}
```
- example usage
```shell
...
mime.contentType('markdown')  // 'text/x-markdown; charset=utf-8'
mime.contentType('file.json') // 'application/json; charset=utf-8'

// from a full path
mime.contentType(path.extname('/path/to/file.json')) // 'application/json; charset=utf-8'
'''

### mime.extension(type)

Get the default extension for a content-type.

'''js
mime.extension('application/octet-stream') // 'bin'
'''
...
```

#### <a name="apidoc.element.mime-types.lookup"></a>[function <span class="apidocSignatureSpan">mime-types.</span>lookup (path)](#apidoc.element.mime-types.lookup)
- description and source-code
```javascript
function lookup(path) {
  if (!path || typeof path !== 'string') {
    return false
  }

  // get the extension ("ext" or ".ext" or full path)
  var extension = extname('x.' + path)
    .toLowerCase()
    .substr(1)

  if (!extension) {
    return false
  }

  return exports.types[extension] || false
}
```
- example usage
```shell
...

The ultimate javascript content-type utility.

Similar to [the 'mime' module](https://www.npmjs.com/package/mime), except:

- __No fallbacks.__ Instead of naively returning the first available type,
  'mime-types' simply returns 'false', so do
  'var type = mime.lookup('unrecognized') || 'application/octet-stream''.
- No 'new Mime()' business, so you could do 'var lookup = require('mime-types').lookup'.
- No '.define()' functionality
- Bug fixes for '.lookup(path)'

Otherwise, the API is compatible.

## Install
...
```



# <a name="apidoc.module.mime-types.charsets"></a>[module mime-types.charsets](#apidoc.module.mime-types.charsets)

#### <a name="apidoc.element.mime-types.charsets.lookup"></a>[function <span class="apidocSignatureSpan">mime-types.charsets.</span>lookup (type)](#apidoc.element.mime-types.charsets.lookup)
- description and source-code
```javascript
function charset(type) {
  if (!type || typeof type !== 'string') {
    return false
  }

  // TODO: use media-typer
  var match = extractTypeRegExp.exec(type)
  var mime = match && db[match[1].toLowerCase()]

  if (mime && mime.charset) {
    return mime.charset
  }

  // default text/* to utf-8
  if (match && textTypeRegExp.test(match[1])) {
    return 'UTF-8'
  }

  return false
}
```
- example usage
```shell
...

The ultimate javascript content-type utility.

Similar to [the 'mime' module](https://www.npmjs.com/package/mime), except:

- __No fallbacks.__ Instead of naively returning the first available type,
  'mime-types' simply returns 'false', so do
  'var type = mime.lookup('unrecognized') || 'application/octet-stream''.
- No 'new Mime()' business, so you could do 'var lookup = require('mime-types').lookup'.
- No '.define()' functionality
- Bug fixes for '.lookup(path)'

Otherwise, the API is compatible.

## Install
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
