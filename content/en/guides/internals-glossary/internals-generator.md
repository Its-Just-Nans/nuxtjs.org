---
title: 'The Generator Class'
description: Nuxt Generator Class
menu: Generator
category: internals-glossary
position: 8
---

- Source: **[generator/generator.js](https://github.com/nuxt/nuxt.js/blob/dev/packages/generator/src/generator.js)**

## Use

```js
const { Generator } = require('nuxt');

const generate = async () => {
  const nuxt = new Nuxt();
  await new Generator(nuxt).generate();
}

generate();
```

Or you can give also a builder in paramters, it will be used if `nuxt.options.build` is set to `true` :

```js
const { Generator, Builder } = require('nuxt');

const generate = async () => {
  const nuxt = new Nuxt();
  const nuxtBuilder = await new Builder(nuxt);
  await new Generator(nuxt, nuxtBuilder).generate();
}

generate();
```

## Hooks

`generate:` hooks:

| Hook                    | Arguments                    | When                                                                                                                                          |
| ----------------------- | ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| `generate:before`       | (generator, generateOptions) | Hook on before generation                                                                                                                     |
| `generate:distRemoved`  | (generator)                  | Hook on destination folder cleaned                                                                                                            |
| `generate:distCopied`   | (generator)                  | Hook on copy static and built files                                                                                                           |
| `generate:route`        | ({ route, setPayload })      | Hook before generating the page, useful for dynamic payload, see [#7422](https://github.com/nuxt/nuxt.js/pull/7422), available for Nuxt 2.13+ |
| `generate:page`         | ({ route, path, html })      | Hook to let user update the path & html after generation                                                                                      |
| `generate:routeCreated` | ({ route, path, errors })    | Hook on saving generated page success                                                                                                         |
| `generate:extendRoutes` | (routes)                     | Hook to let user update the routes to generate                                                                                                |
| `generate:routeFailed`  | ({ route, errors })          | Hook on saving generated page failure                                                                                                         |
| `generate:done`         | (generator, errors)          | Hook on generation finished                                                                                                                   |
