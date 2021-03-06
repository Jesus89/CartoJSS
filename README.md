# CartoJSS

[![Build Status](https://travis-ci.org/CartoDB/CartoJSS.svg?branch=master)](https://travis-ci.org/CartoDB/CartoJSS)
[![js-semistandard-style](https://img.shields.io/badge/code%20style-semistandard-brightgreen.svg?style=flat-square)](https://github.com/Flet/semistandard)

[![NPM](https://nodei.co/npm/cartojss.png?)](https://nodei.co/npm/cartojss)

Generate [CartoCSS](https://carto.com/docs/carto-engine/cartocss) and [Turbocarto ramps](https://github.com/CartoDB/turbo-carto) from a JavaScript object

## Install

```
$ npm install cartojss
```

## Usage
```javascript
var cartojss = require('cartojss');

var style = {
  '@small': 3,
  '@large': 6,
  '#layer': {
    'marker-width': '@small',
    'marker-allow-overlap': true,
    '[zoom = 4]': {
      'marker-width': '@large'
    }
  },
  '#selector': {
    'line-dasharray': [1, 4, 2],
    'marker-width': 'ramp([price], (10, 20, 30), jenks())'
  },
  '#world': {
    'text-name': '"[NAME]"',
    'text-size': 11,
    'text-face-name': ['"Georgia Regular"', '"Arial Italic"']
  }
}

cartojss.serialize(style, { pretty: true });
```

```
@small: 3;
@large: 6;
#layer {
  marker-width: @small;
  marker-allow-overlap: true;
  [zoom = 4] {
    marker-width: @large;
  }
}
#selector {
  line-dasharray: 1, 4, 2;
  marker-width: ramp([price], (10, 20, 30), jenks());
}
#world {
  text-name: "[NAME]";
  text-size: 11;
  text-face-name: "Georgia Regular", "Arial Italic";
}
```

## Options

#### pretty
Type: `Boolean`<br>
Default: `false`

Serialize pretty CartoCSS

## Development

```
yarn
yarn test
```

### Publish

```
npm version patch|minor|major
npm publish
```

## Browsers support <sub><sup><sub><sub>made by <a href="https://godban.github.io">godban</a></sub></sub></sup></sub>

| [<img src="https://raw.githubusercontent.com/godban/browsers-support-badges/master/src/images/edge.png" alt="IE / Edge" width="16px" height="16px" />](http://godban.github.io/browsers-support-badges/)</br>IE / Edge | [<img src="https://raw.githubusercontent.com/godban/browsers-support-badges/master/src/images/firefox.png" alt="Firefox" width="16px" height="16px" />](http://godban.github.io/browsers-support-badges/)</br>Firefox | [<img src="https://raw.githubusercontent.com/godban/browsers-support-badges/master/src/images/chrome.png" alt="Chrome" width="16px" height="16px" />](http://godban.github.io/browsers-support-badges/)</br>Chrome | [<img src="https://raw.githubusercontent.com/godban/browsers-support-badges/master/src/images/safari.png" alt="Safari" width="16px" height="16px" />](http://godban.github.io/browsers-support-badges/)</br>Safari |
| --------- | --------- | --------- | --------- |
| IE11, Edge| last 3 versions| last 3 versions| last 3 versions
