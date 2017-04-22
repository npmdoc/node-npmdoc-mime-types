# npmdoc-mime-types

#### api documentation for  [mime-types (v2.1.15)](https://github.com/jshttp/mime-types#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-mime-types.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-mime-types) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-mime-types.svg)](https://travis-ci.org/npmdoc/node-npmdoc-mime-types)

#### The ultimate javascript content-type utility.

[![NPM](https://nodei.co/npm/mime-types.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/mime-types)

- [https://npmdoc.github.io/node-npmdoc-mime-types/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-mime-types/build/apidoc.html)

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
    "version": "2.1.15",
    "bin": {}
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
