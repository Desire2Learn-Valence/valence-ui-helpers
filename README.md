# [DEPRECATED] vui-helpers

This project is deprecated! We strongly recommend using other modules to perform the gulp activities packaged here.

* Validation with with [Lint](https://www.npmjs.org/package/gulp-csslint)
* Transpiling with [Less](https://www.npmjs.org/package/gulp-less)
* Auto-Prifixing with [autoprefixer](https://www.npmjs.org/package/autoprefixer)
* Valence UI Testing with [Karma JSON Log Reporter](https://www.npmjs.com/package/vui-karma-json-log-reporter), [Karma JSON Log Configurer](https://www.npmjs.com/package/vui-karma-jasmine-tester), and [Jasmine DOM Matchers](https://www.npmjs.com/package/vui-jasmine-dom-matchers).

_Previous README reproduced below_

# vui-helpers

[![NPM version][npm-image]][npm-url]
[![Build status][ci-image]][ci-url]

##Usage

Install as a development dependency:

```shell
npm install --save-dev vui-helpers
```

Then add it to your `gulpfile.js`:

```javascript
var vuiHelpers = require('vui-helpers');
```

##API

###clean

Deletes directories or files.

```javascript
gulp.task( 'clean', function() {
  return vuiHelpers.clean( [ 'dir1', 'dir2' ] );
} );
```

The only parameter is an array of directories/files to delete.

###makeCss

Performs a [lint](https://www.npmjs.org/package/gulp-csslint) of the CSS files
to validate syntax and CSS best practices, does a
[LESS compilation](https://www.npmjs.org/package/gulp-less) of any LESS files,
and finally [auto-prefixes](https://www.npmjs.org/package/autoprefixer) the CSS
to add vendor-specific prefixes based on our currently supported browsers.

```javascript
var vuiHelpers = require('vui-helpers');
gulp.task( 'css', function() {
  return vuiHelpers.makeCss( 'source/*', 'dist' );
} );
```

The first parameter is a glob which defines your CSS input files, followed by
an output directory.

###makeLess

Copies LESS files from source to target.

```javascript
var vuiHelpers = require('vui-helpers');
gulp.task( 'less', function() {
  return vui.makeLess( 'src/**/*.less', 'dist/' );
} );
```

The first parameter is a glob which defines the LESS input files, followed by
an output location.

###test

Helper for testing with [Karma](https://www.npmjs.org/package/gulp-karma).

```javascript
gulp.task( 'test', function () {
  return vui.test( {
    files: [
      'my-component.js',
      'my-component.css',
      'test/unit/**/*Spec.js'
    ],
    preprocessors: {
      'my-component.js': ['coverage']
    }
  } );
} );
```

The test helper configures the Karma test runner to use PhantomJS, coverage
reporters, and Jasmine. It also includes custom Jasmine matchers that may be
used in your specs. A config object must be provided to the test helper to
specify the files/patterns for the test. Other Karma config properties may be
provided, for instance to include files for coverage via the preprocessor
property.

## Contributiing

### Code Style

This repository is configured with [EditorConfig](http://editorconfig.org) rules and contributions should make use of them. See the [VUI Best Practices & Style Guide](https://github.com/Brightspace/valence-ui-docs/wiki/Best-Practices-&-Style-Guide) for more information.

[npm-url]: https://npmjs.org/package/vui-helpers
[npm-image]: https://img.shields.io/npm/v/vui-helpers.svg
[ci-image]: https://travis-ci.org/Brightspace/valence-ui-helpers.svg?branch=master
[ci-url]: https://travis-ci.org/Brightspace/valence-ui-helpers
