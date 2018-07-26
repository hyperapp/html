# @hyperapp/html

[![Tests](https://img.shields.io/travis/hyperapp/html/master.svg)](https://travis-ci.org/hyperapp/html)
[![Coverage](https://img.shields.io/codecov/c/github/hyperapp/html/master.svg)](https://codecov.io/gh/hyperapp/html)
[![npm](https://img.shields.io/npm/v/@hyperapp/html.svg)](https://www.npmjs.org/package/@hyperapp/html)
[![Slack](https://hyperappjs.herokuapp.com/badge.svg)](https://hyperappjs.herokuapp.com "Join us")

Html helper functions for [Hyperapp](https://github.com/hyperapp/hyperapp). Use @hyperapp/html as an alternative to JSX or the <samp>hyperapp.h</samp> function.

## Installation

<pre>
npm i <a href=https://www.npmjs.com/package/@hyperapp/html>@hyperapp/html</a>
</pre>

Don't want to set up a build environment? Download @hyperapp/html from [unpkg.com/@hyperapp/html](https://unpkg.com/@hyperapp/html) and it will be globally available through the <samp>window.hyperappHtml</samp> object.

## Usage

Here is a counter that can be incremented or decremented. Go ahead and [try it online](https://codepen.io/jorgebucaran/pen/MrBgMy?editors=0010).

```jsx
import { h, app } from "hyperapp"
import { div, h1, button } from "@hyperapp/html"

const state = {
  count: 0
}

const actions = {
  down: () => state => ({ count: state.count - 1 }),
  up: () => state => ({ count: state.count + 1 })
}

const view = (state, actions) =>
  div([
    h1(state.count),
    button({ onclick: actions.down }, "-"),
    button({ onclick: actions.up }, "+")
  ])

app(state, actions, view, document.body)
```

See [/vars.json](/vars.json) for the list of available Html tags you can use in your program.


## SVG

Svg elements can also be created importing an extra module from `@hyperapp/html/svg`.

```jsx
import { app } from "hyperapp"
import { svg, circle, defs, linearGradient, stop } from "@hyperapp/html/svg"

const view = () =>
  svg({ x: 0, y: 0, width: 600, height: 400, viewBox: "0 0 600 400" }, [
    circle({ cx: 300, cy: 200, r: 60, fill: "url(#MyGradient)" }),
    defs({}, [
      linearGradient({ id: "MyGradient" }, [
        stop({ offset: "5%", "stop-color": "#f60" }),
        stop({ offset: "95%", "stop-color": "#ff6" })
      ])
    ])
  ])

app({}, {}, view, document.body)
```

Most non-deprecated svg elements are supported, check [/vars.json](/vars.json) for the list of available svg tags.

## License

@hyperapp/html is MIT licensed. See [LICENSE](LICENSE.md).
