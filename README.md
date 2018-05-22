# VueTuicalendar

[![npm](https://img.shields.io/npm/v/vue-tuicalendar.svg)](https://www.npmjs.com/package/vue-tuicalendar) [![vue2](https://img.shields.io/badge/vue-2.x-brightgreen.svg)](https://vuejs.org/)

> A Vue.js wrapper for TOAST UI Calendar

## Installation

```bash
npm install --save @lkmadushan/vue-tuicalendar
```

## Usage

### Bundler (Webpack, Rollup)

```js
import Vue from 'vue'
import VueTuicalendar from '@lkmadushan/vue-tuicalendar'
// You need a specific loader for CSS files like https://github.com/webpack/css-loader
import 'tui-calendar/dist/tui-calendar.min.css'

Vue.use(VueTuicalendar)

// or

import Vue from 'vue'
import { VueTuicalendar } from '@lkmadushan/vue-tuicalendar'
// You need a specific loader for CSS files like https://github.com/webpack/css-loader
import 'tui-calendar/dist/tui-calendar.min.css'
```

### Browser

```html
<!-- Include after Vue -->
<!-- Local files -->
<script src="vue-tuicalendar/dist/@lkmadushan/vue-tuicalendar.js"></script>

<!-- From CDN -->
<script src="https://unpkg.com/@lkmadushan/vue-tuicalendar"></script>
```

## Development

### Launch visual tests

```bash
npm run dev
```

### Launch Karma with coverage

```bash
npm run dev:coverage
```

### Build

Bundle the js and css of to the `dist` folder:

```bash
npm run build
```


## Publishing

The `prepublish` hook will ensure dist files are created before publishing. This
way you don't need to commit them in your repository.

```bash
# Bump the version first
# It'll also commit it and create a tag
npm version
# Push the bumped package and tags
git push --follow-tags
# Ship it 🚀
npm publish
```

## License

[MIT](http://opensource.org/licenses/MIT)
