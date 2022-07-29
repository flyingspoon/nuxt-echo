# @nuxtjs/laravel-echo

> Laravel Echo for Nuxt.js 2x (Modified by FlyingSpoon)

[📖 **Release Notes**](./CHANGELOG.md)

## Which Laravel Echo does this work with? (FlyingSpoon)

This has been tested with ```"laravel-echo": "^1.11.3"```, please install this
version to avoid any issues with compatibility.

## Module set-up (FlyingSpoon)
```
...
buildModules: [
	'@/modules/nuxt-echo'
]
...
```

## Example nuxt.config.js (FlyingSpoon)

```
...
echo: {
    broadcaster: 'pusher',
    CSRFendpoint: 'http://127.0.0.1:8000/api/sanctum/csrf-cookie',
    authEndpoint: 'http://127.0.0.1:8000/api/broadcasting/auth',
    wsHost: '127.0.0.1',
    wsPort: 6001,
    key: 'bDYhf22uk2GvRPIrLxh2nFdhGZFR9zmP',
    encrypted: true,
    // enableLogging: true,
    connectOnLogin: false,
    disconnectOnLogout: false,
    disableStats: true,
    forceTLS: false,
    authModule: true
    // enabledTransports: ['ws', 'wss'],
    // plugins: [ '@/plugins/echo.js' ]
}
...
```

## Requirements

If you use the broadcaster `pusher`, you need to ensure that you have `pusher-js` installed:

```bash
yarn add pusher-js # or npm install pusher-js
```

If you use the broadcaster `socket.io`, you need to ensure that you have `socket.io-client` installed:

```bash
yarn add socket.io-client # or npm install socket.io-client
```

## Setup

1. Add `@nuxtjs/laravel-echo` dependency to your project

```bash
yarn add --dev @nuxtjs/laravel-echo # or npm install --save-dev @nuxtjs/laravel-echo
```

2. Add `@nuxtjs/laravel-echo` to the `buildModules` section of `nuxt.config.js`

```js
export default {
  buildModules: [
    // Simple usage
    '@nuxtjs/laravel-echo',

    // With options
    ['@nuxtjs/laravel-echo', { /* module options */ }]
  ]
}
```

:warning: If you are using Nuxt **< v2.9** you have to install the module as a `dependency` (No `--dev` or `--save-dev` flags) and use `modules` section in `nuxt.config.js` instead of `buildModules`.

### Using top level options

```js
export default {
  buildModules: [
    '@nuxtjs/laravel-echo'
  ],
  echo: {
    /* module options */
  }
}
```

## Options

### `broadcaster`

- Type: `String`
- Default: `'null'`

You can use `'pusher'`, `'socket.io'` or `'null'`.

See https://laravel.com/docs/broadcasting#driver-prerequisites

### `plugins`

- Type: `Array`
- Default: `null`

If you have plugins that need to access `$echo`, you can use `echo.plugins` option.

> **Note:** Plugins are pushed in client mode only (`ssr: false`).

`nuxt.config.js`

```js
export default {
  buildModules: [
    '@nuxtjs/laravel-echo'
  ],
  echo: {
     plugins: [ '~/plugins/echo.js' ]
  }
}
```

`plugins/echo.js`

```js
export default function ({ $echo }) {
  // Echo is available here
  console.log($echo)
}
```

### `authModule`

- Type: `Boolean`
- Default: `false`

Integration with [Auth Module](https://github.com/nuxt-community/auth-module).

### `connectOnLogin`

- Type: `Boolean`
- Default: `false`

Connect the connector on login, if `authModule` is set `true`.

### `disconnectOnLogout`

- Type: `Boolean`
- Default: `false`

Disconnect the connector on logout, if `authModule` is set `true`.

## Usage

This module inject `$echo` to your project:

```html
<template>
  <div>
    <h1>Orders</h1>
  </div>
</template>

<script>
export default {
  mounted() {
    this.$echo.channel('orders')
      .listen('OrderShipped', (e) => {
          console.log(e.order.name);
      });
  }
}
</script>
```

## License

[MIT License](./LICENSE)

Copyright (c) Nuxt Community

<!-- Badges -->
[npm-version-src]: https://img.shields.io/npm/v/@nuxtjs/laravel-echo/latest.svg?style=flat-square
[npm-version-href]: https://npmjs.com/package/@nuxtjs/laravel-echo

[npm-downloads-src]: https://img.shields.io/npm/dt/@nuxtjs/laravel-echo.svg?style=flat-square
[npm-downloads-href]: https://npmjs.com/package/@nuxtjs/laravel-echo

[circle-ci-src]: https://img.shields.io/circleci/project/github/nuxt-community/laravel-echo.svg?style=flat-square
[circle-ci-href]: https://circleci.com/gh/nuxt-community/laravel-echo

[codecov-src]: https://img.shields.io/codecov/c/github/nuxt-community/laravel-echo.svg?style=flat-square
[codecov-href]: https://codecov.io/gh/nuxt-community/laravel-echo

[license-src]: https://img.shields.io/npm/l/@nuxtjs/laravel-echo.svg?style=flat-square
[license-href]: https://npmjs.com/package/@nuxtjs/laravel-echo
