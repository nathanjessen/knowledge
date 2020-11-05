---
layout: default
title: NPM
---

## Useful Commands

| Command | Description |
| ------- | ----------- |
| `npm home $package` | Open a package's homepage |
| `npm repo $package` | Open a package's GitHub repo |
| `npm outdated` | Check for outdated dependencies |
| `npm prune` | Check for packages not declared in package.json and uninstall them |
| `npm shrinkwrap` | Lock down dependency versions |
| `npm config set save-prefix="~"` | Change default save prefix for all projects |
| `-s` | Flag to silence output from npm on tasks |

## Version Bumping

| Command | Description |
| ------- | ----------- |
| `npm version patch` | Increment patch number of version number |
| `npm version minor` | Increment minor number of version number |
| `npm version major` | Increment major number of version number |
| `npm version patch --git-tag-version=false` | Update patch number but prevent new tag from being created from the commit |

These increment the version number in package.json, makes a git commit, and tags the commit. Update version with the above commands then `git push` and `npm publish`.

**Optional Flags**
| Command | Description |
| ------- | ----------- |
| `npm version patch --git-tag-version=false` | Update version number but prevent new tag from being created from the commit |
| `npm version patch -m "Bumpted to %s"` | Configure the commit message |

## npm Syntax

| Character | Description |
| --------- | ----------- |
| `&&` | Chain tasks |
| `&` | Run tasks simultaneously |
| `<` | Inputting contents of a file to a command |
| `>` | Redirect output of a command and dumping it to a file |
| `|` | Redirect output of a command and sending it to another command |

Use [rimraf](https://www.npmjs.org/package/rimraf) instead of relying on built in commands like `rm` since these can be reliant on the operating system.

## Useful Scripts

### Watch

**Built-in watch flags**

```
"devDependencies": {
  "mocha": "latest",
  "stylus": "latest"
},
"scripts": {
  "test": "mocha test/",
  "test:watch": "npm run test -- -w",

  "css": "stylus assets/styles/main.styl > dist/main.css",
  "css:watch": "npm run css -- -w"
}
```

**Using tools**

```
"devDependencies": {
  "stylus": "latest",
  "jade": "latest",
  "browserify": "latest",
  "watch": "latest",
},
"scripts": {
  "build:js": "browserify assets/scripts/main.js > dist/main.js",
  "build:css": "stylus assets/styles/main.styl > dist/main.css",
  "build:html": "jade assets/html/index.jade > dist/index.html",
  "build": "npm run build:js && npm run build:css && npm run build:html",
  "build:watch": "watch 'npm run build' .",
}
```

- [watch](https://www.npmjs.com/package/watch)
- [onchange](https://www.npmjs.com/package/onchange)
- [dirwatch](https://www.npmjs.com/package/dirwatch)
- [nodemon](https://github.com/remy/nodemon)

### Parallelshell to keep multiple processes running at one time

```
"devDependencies": {
  "stylus": "latest",
  "jade": "latest",
  "browserify": "latest",
  "watch": "latest",
  "parallelshell": "latest"
},
"scripts": {
  "build:js": "browserify assets/scripts/main.js > dist/main.js",
  "watch:js": "watch 'npm run build:js' assets/scripts/",
  "build:css": "stylus assets/styles/main.styl > dist/main.css",
  "watch:css": "watch 'npm run build:css' assets/styles/",
  "build:html": "jade index.jade > dist/index.html",
  "watch:html": "watch 'npm run build:html' assets/html",
  "build": "npm run build:js && npm run build:css && npm run build:html",
  "build:watch": "parallelshell 'npm run watch:js' 'npm run watch:css' 'npm run watch:html'",
}
```

## Running tasks that doesn't have a binary

```js
// scripts/favicon.js
var favicons = require('favicons');
var path = require('path');
favicons({
    source: path.resolve('../assets/images/logo.png'),
    dest: path.resolve('../dist/'),
});
```

```
"devDependencies": {
  "favicons": "latest",
},
"scripts": {
  "build:favicon": "node scripts/favicon.js",
}
```

## Resources

- [How to Use npm as a Build Tool](https://www.keithcirkel.co.uk/how-to-use-npm-as-a-build-tool/)
- [npm-scripts-example](https://github.com/keithamus/npm-scripts-example)
- [npm-scripts](https://docs.npmjs.com/misc/scripts)
- [npm-build-boilerplate](https://github.com/damonbauer/npm-build-boilerplate)
