# Nightwatch Accessibility

Nightwatch.js utility assertion for accessibility testing with aXe.

[![license][license-img]][license-url]
[![release][release-img]][release-url]
[![super linter][super-linter-img]][super-linter-url]
[![test][test-img]][test-url]
[![semantic][semantic-img]][semantic-url]

## Install

``` bash
npm install --only=production --save nightwatch-accessibility
```

## Usage

Update your nightwatch config:

``` js
{
  custom_commands_path: ["./node_modules/nightwatch-accessibility/commands"],
  custom_assertions_path: ["./node_modules/nightwatch-accessibility/assertions"]
}
```

Use in your tests:

``` js
module.exports = {
  'Test': function (browser) {
    browser
      .initAccessibility()
      .assert.accessibility('#app', {
        verbose: true,
        rules: {
          'color-contrast': { enabled: false }
        }
      })
      .end()
  }
}
```

## API

### `browser.initAccessibility()`

Injects the [`aXe`][] library into the current test page.

### `browser.assert.accessibility(context, options)`

Analyzes the defined `context` against applied `aXe` rules

| Name          | Type     | Default  | Description               |
|---------------|----------|----------|---------------------------|
| **`context`** | `String` | `'html'` | [aXe Context][] Parameter |
| **`options`** | `Object` | `null`   | [aXe Options][] Parameter |

> In addition to the standard `options`:

-   `options.verbose` set to `true` will log all successful `aXe` tests.
-   `options.timeout` configures the nightwatch timeout, default value is `500 milliseconds`

  [`aXe`]: https://www.npmjs.com/package/axe-core
  [aXe Context]: https://github.com/dequelabs/axe-core/blob/master/doc/API.md#context-parameter
  [aXe Options]: https://github.com/dequelabs/axe-core/blob/master/doc/API.md#options-parameter

----
> Author: [Ahmad Nassri](https://www.ahmadnassri.com/) &bull;
> Twitter: [@AhmadNassri](https://twitter.com/AhmadNassri)

[license-url]: LICENSE
[license-img]: https://badgen.net/github/license/ahmadnassri/node-nightwatch-accessibility

[release-url]: https://github.com/ahmadnassri/node-nightwatch-accessibility/releases
[release-img]: https://badgen.net/github/release/ahmadnassri/node-nightwatch-accessibility

[super-linter-url]: https://github.com/ahmadnassri/node-nightwatch-accessibility/actions?query=workflow%3Asuper-linter
[super-linter-img]: https://github.com/ahmadnassri/node-nightwatch-accessibility/workflows/super-linter/badge.svg

[test-url]: https://github.com/ahmadnassri/node-nightwatch-accessibility/actions?query=workflow%3Atest
[test-img]: https://github.com/ahmadnassri/node-nightwatch-accessibility/workflows/test/badge.svg

[semantic-url]: https://github.com/ahmadnassri/node-nightwatch-accessibility/actions?query=workflow%3Arelease
[semantic-img]: https://badgen.net/badge/📦/semantically%20released/blue
