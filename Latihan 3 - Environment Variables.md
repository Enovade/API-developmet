[[_TOC_]]

# Latihan 3: Environment Variables
Latihan ini adalah untuk menunjukkan pemahaman menggunakan **Environment Variables** untuk **Fastify Framework**

Sila layari https://github.com/motdotla/dotenv untuk maklumat lanjut

Latihan ini adalah sambungan dari latihan [Latihan 2: Fastify Logging](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%202%20-%20Fastify%20Logging.md)

# Langkah 1.0: Tetapan Environment Variables

* **Install dotenv plugins** dengan taip kod berikut di **Command Prompt** atau **Terminal**

```bash
npm i dotenv
```

* Wujudkan fail **server.js**, padam kod sediada, salin dan tampal kod berikut

```javascript
import { build } from './app.js'
import dotenv from 'dotenv'

dotenv.config()

const opts = {
  logger: {
    level: 'info'
  }
}

// We want to use pino-pretty only if there is a human watching this,
// otherwise we log as newline-delimited JSON.
if (process.stdout.isTTY) {
  opts.logger.transport = { target: 'pino-pretty' }
}

const port = process.env.PORT || 8080
const host = process.env.HOST || '127.0.0.1'

const app = await build(opts)
await app.listen({ port, host })

```

* Simpan / (_**Save**_) fail **server.js**.

* Buka fail **app.js** padam kod sediada, salin dan tampal kod berikut

```javascript
import fastify from 'fastify'

export async function build (opts = {}) {
  const app = fastify(opts)

  app.get('/', async (request, reply) => {
    return { hello: 'world' }
  })
  return app
}

```

* Simpan / (_**Save**_) fail **app.js**.

* Di **Command Prompt** atau **Terminal**, taip kod berikut untuk mulakan aplikasi **Fastify**

```bash
npm run dev
```

* Buka fail **package.json** tukar kod "script"

```json
"scripts": {
  "dev": "node app.js"
},
```

* kepada kod berikut

```json
"scripts": {
  "dev": "node server.js"
},
```

* Simpan / (_**Save**_) fail **package.json**.

* Wujudkan fail *.env**, salin dan tampal kod berikut

```
PORT=8090
HOST=127.0.0.1
```

* Simpan / (_**Save**_) fail **.env**.

# Langkah 2.0: Exit Application gracefully

Langkah ini adalah untuk menggunakan **close-with-grace plugins** untuk 

* **Install close-with-grace plugins** dengan taip kod berikut di **Command Prompt** atau **Terminal**

```bash
npm i close-with-grace
```

* Buka fail **server.js**, padam kod sediada, salin dan tampal kod berikut

```javascript
import { build } from './app.js'
import closeWithGrace from 'close-with-grace'
import dotenv from 'dotenv'

dotenv.config()

const opts = {
  logger: {
    level: 'info'
  }
}

// We want to use pino-pretty only if there is a human watching this,
// otherwise we log as newline-delimited JSON.
if (process.stdout.isTTY) {
  opts.logger.transport = { target: 'pino-pretty' }
}

const port = process.env.PORT || 8080
const host = process.env.HOST || '127.0.0.1'

const app = await build(opts)
await app.listen({ port, host })

closeWithGrace(async ({ signal, err }) => {
    if (err) {
      app.log.error({ err }, 'server closing with error')
    } else {
      app.log.info(`${signal} received, server closing`)
    }
    await app.close()
  })
```

* Simpan / (_**Save**_) fail **server.js**.

* Di **Command Prompt** atau **Terminal**, taip kod berikut untuk mulakan aplikasi **Fastify**

```bash
npm run dev
```
* Tekan kekunci **Ctrl-C** untuk uji **gracefull shutdown**
