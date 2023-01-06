#  holo-mario-kart-pickem

Predictions selector tool for the hololive New Year Cup Mario Kart tournament. Access site at https://alam8.github.io/holo-mario-kart-pickem/.

Built using [Vue 3](https://vuejs.org/), [Bootstrap](https://getbootstrap.com/)/[BootstrapVue 3](https://cdmoro.github.io/bootstrap-vue-3/), [Vue Horizontal](https://vue-horizontal.fuxing.dev/), [Vuetify](https://vuetifyjs.com/en/), [dom-to-image-more](https://github.com/1904labs/dom-to-image-more), and [FileSaver.js](https://github.com/eligrey/FileSaver.js). Icons sourced from [hololive Talents page](https://hololive.hololivepro.com/en/talents).

## Todo:
- [x] Store selected members in array in parent component
- [x] Separate rounds using tab component
- [x] Limit selections per group
- [x] Disable/enable tabs based on selections
- [ ] Download icon images instead of linking to site?

## Backlog for next year(?):
- [ ] Rewrite in TypeScript
- [ ] Design scoring system and hook up to backend for online leaderboard

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

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
