# wingspan-scoresheet

Example getting started with Vue from class

## FIXES FROM CLASS

In calculating the high score, I was using `Math.max` incorrectly.  
 `Math.max` uses a list of numbers as in
`Math.max(1,2,3)`, not an array. So, I need to "spread" the Array
into its individual items with ...
`Math.max(...totalForPlayers)`

In comparing the player total score in `isWinner`, I needed to use the `.value` of the `getHighestScore`. Since `getHighestScore` is a Vue `computed` value,
I need to refer to `getHighestScore.value` to get the value instead of the
computed object that Vue created to wrap the value so that it can do
its Vue 'magic'

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Vue (Official)](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Recommended Browser Setup

- Chromium-based browsers (Chrome, Edge, Brave, etc.):
  - [Vue.js devtools](https://chromewebstore.google.com/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
  - [Turn on Custom Object Formatter in Chrome DevTools](http://bit.ly/object-formatters)
- Firefox:
  - [Vue.js devtools](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
  - [Turn on Custom Object Formatter in Firefox DevTools](https://fxdx.dev/firefox-devtools-custom-object-formatters/)

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```
