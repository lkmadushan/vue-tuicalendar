# Vue TOAST UI Calendar

[![npm](https://img.shields.io/npm/v/@lkmadushan/vue-tuicalendar.svg)](https://www.npmjs.com/package/@lkmadushan/vue-tuicalendar) [![vue2](https://img.shields.io/badge/vue-2.x-brightgreen.svg)](https://vuejs.org/)

> A Vue.js wrapper for [TOAST UI Calendar](http://ui.toast.com/tui-calendar)

## Installation

```bash
npm install --save tui-calendar @lkmadushan/vue-tuicalendar
```

## Usage

### Example 

Try out this [Code Sandbox](https://codesandbox.io/s/0wm308qol)

### Bundler (Webpack, Rollup)

```js
import Vue from 'vue'
import VueTuicalendar from '@lkmadushan/vue-tuicalendar'
// You need a specific loader for CSS files like https://github.com/webpack/css-loader
import 'tui-calendar/dist/tui-calendar.min.css'

Vue.use(VueTuicalendar)

// or

import { VueTuicalendar } from '@lkmadushan/vue-tuicalendar'
```

```html
<template>
  <vue-tuicalendar
    ref="calendar"
    :options="options"
    :schedules="schedules"
    @after-render-schedule="handler"
    @before-render-schedule="handler"
    @click-schedule="handler"
  >
  </vue-tuicalendar>
</template>

...
<script>
...
  data() {
    return {
      schedules: [
        {
          id: "1",
          calendarId: "1",
          title: "A schedule",
          category: "time",
          dueDateClass: "",
          start: "2018-05-22T22:30:00+09:00",
          end: "2018-05-23T02:30:00+09:00"
        },
        {
          id: "2",
          calendarId: "1",
          title: "Another schedule",
          category: "time",
          dueDateClass: "",
          start: "2018-05-23T17:30:00+09:00",
          end: "2018-05-24T17:31:00+09:00",
          isReadOnly: true
        }
      ]
    }
  }
  
  methods: {
    mounted() {
      this.$refs.calendar.fireMethod('clear');
      this.$refs.calendar.fireMethod('getElement');
      this.$refs.calendar.fireMethod('changeView', 'month', true);
      
      this.$refs.calendar.registerEvent('beforeDeleteSchedule', (event) {
        // do stuff here
      })
    }
  }
...
</script>
```

More options can be found at https://nhnent.github.io/tui.calendar/latest/Calendar.html

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
