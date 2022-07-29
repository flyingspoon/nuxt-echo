# @nuxtjs/laravel-echo

> Laravel Echo for Nuxt.js 2x (Modified by FlyingSpoon)

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
