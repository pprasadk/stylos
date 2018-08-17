<h1 align="center">
	<img height="150" src="https://raw.github.com/kamranahmedse/stylos/master/logo.svg?sanitize=true" alt="Stylos - Generate and inject CSS utilities to your application" />
	<br> Stylos
</h1>
<p align="center">
	<a href="https://travis-ci.org/kamranahmedse/stylos">
		<img src="https://img.shields.io/travis/kamranahmedse/stylos/master.svg?style=flat-square" alt="Build Status">
	</a>
	<a href="https://github.com/kamranahmedse/stylos">
		<img src="https://img.shields.io/codecov/c/github/kamranahmedse/stylos.svg?style=flat-square" alt="Codecov">
	</a>
	<a href="#">
		<img src="https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square" alt="Software License">
	</a>
</p>

<p align="center">Webpack plugin that automatically generates and injects CSS utilities to your application.</p>

## What is it?
Inspired by [bootstrap's utility classes](https://getbootstrap.com/docs/4.1/utilities/sizing/), stylos is a Webpack plugin that automatically generates and injects CSS utilities into your application. All you have to do is specify utility classes on DOM elements; webpack will identify and generate the properties with relevant values and inject them to your application. 

![](https://i.imgur.com/cF2pssW.png)

You might have guessed from the example above; all you have to do is specify the classes having formula key, value and then optionally the unit i.e.

```bash
[formula][value][unit] # If you donot provide the unit, `px` will be used.
```

Stylos will understand it and generate the CSS for you. There is a variety of options available. Here is the the list of known property formulas that you can use in your DOM classes.

| Formula | CSS Property     | Example Usage                                    |
|---------|------------------|--------------------------------------------------|
| `p`     | `padding`        | `p10` will translate to `padding: 10px`          |
| `pt`    | `padding-top`    | `pt20` will translate to `padding-top: 20px;`    |
| `pb`    | `padding-bottom` | `pb10` will translate to `padding-bottom: 10px;` |
| `pr`    | `padding-right`  | `pr20` will translate to `padding-right: 20px;`  |
| `pl`    | `padding-left`   | `pl23` will translate to `padding-left: 23px;`   |
| `m`     | `margin`         | `m20` will translate to `margin: 20px`           |
| `mt`    | `margin-top`     | `mt20` will translate to `margin-top: 20px;`     |
| `mb`    | `margin-bottom`  | `mb20` will translate to `margin-bottom: 20px;`  |
| `ml`    | `margin-left`    | `ml50` will translate to `margin-left: 50px;`    |
| `mr`    | `margin-right`   | `mr30` will translate to `margin-right: 30px;`   |
| `w`     | `width`          | `w200` will translate to `width: 200px`          |
| `h`     | `height`         | `h60` will translate to `height: 60px;`          |
| `br`    | `border-radius`  | `br5` will translate to `border-radius: 5px;`    |
| `fs`    | `font-size`      | `fs15` will translate to `font-size: 15px`       |
| `fw`    | `font-weight`    | `fw400` will translate to `font-weight: 400px`   |
| `lh`    | `line-height`    | `lh20em` will translate to `line-height: 20em`   |
| `t`     | `top`            | `t6` will translate to `top: 6px;`               |
| `l`     | `left`           | `l30` will translate to `left: 30px`             |
| `b`     | `bottom`         | `b20em` will translate to `bottom: 20em;`        |
| `r`     | `right`          | `r20em` will translate to `right: 20em;`         |

For the units, all the default CSS units are supported. You can specify them after the value and relevant CSS unit will be used

- Units including `px, pt, em, p, vh, vw, vmin, ex, cm, in, mm, pc` will translate to the same unit in CSS
- If you don't provide any unit `px` will be used
- If you need `%` specify it as `p` e.g. `w50p` will get translated to `width: 50%`
- If no unit is needed, specify `n` e.g. `fw600n` will translate to `font-weight: 600`

## How to use?

Install the plugin using npm or yarn

```bash
npm install stylos --save-dev
yarn add stylos --dev
```
Add the loader to `module.rules` in your webpack configuration
```javascript
const Stylos = require('stylos');

// ...
module: {
  // Add the loader in the loader's list
  // it can handle HTML as well as JSX files
  rules: [
    // ...
    {
      test: /\.js$/,
      exclude: /node_modules/,
      use: Stylos.Loader
    }
  ]
},
// ...
plugins: [
  // Add the plugin right after html-webpack-plugin
  // new HtmlWebpackPlugin(..),  // <-- You must have it installed and set up
  new Stylos.Plugin(),
]
// ...
```

## License
MIT &copy; [Kamran Ahmed](http://kamranahmed.info)
