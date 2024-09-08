[[_TOC_]]

# Latihan 2: Fastify Logging
Latihan ini adalah untuk menunjukkan pemahaman menggunakan **Logging** menggunakan **Pino** untuk **Fastify Framework**

Sila layari https://getpino.io/ untuk maklumat lanjut

Latihan ini adalah sambungan dari latihan [Latihan 1: Pengenalan Fastify](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%201%20-%20Pengenalan%20Fastify.md)

# Langkah 1.0: Enabling Fastify Logging
Langkah ini adalah untuk menggunakan **logging** untuk **Fastify Framework**

* Buka fail **app.js**, padam kod sediada, salin dan tampal kod berikut

```javascript
import Fastify from 'fastify'

const app = Fastify(
    { logger: true }
)

app.get('/', async (request, reply) => {
  return { hello: 'world' }
})

/**
 * Run the server!
 */
const start = async () => {
    try {
        await app.listen({ port: 8080 })
    } catch (err) {
        app.log.error(err)
        process.exit(1)
    }
}
start()
```

* Simpan / (_**Save**_) fail **app.js**.

* Di **Command Prompt** atau **Terminal**, taip kod berikut untuk mulakan aplikasi menggunakan **Fastify** untuk paparkan maklumat **Log** seperti contoh paparan berikut

```bash
npm run dev
```

* berikut adalah contoh paparan jika berjaya
```bash
> latihan-1@1.0.0 dev
> node app.js

{"level":30,"time":1725796825304,"pid":57240,"hostname":"hanafiah-2.local","msg":"Server listening at http://[::1]:8080"}
{"level":30,"time":1725796825305,"pid":57240,"hostname":"hanafiah-2.local","msg":"Server listening at http://127.0.0.1:8080"}
```

# Langkah 2.0: Tetapan Fastify Logging

## Langkah 2.1: Pino-pretty

* **Install Pino-pretty plugins** dengan taip kod berikut di **Command Prompt** atau **Terminal**

```bash
npm i pino-pretty
```

* Buka fail **app.js**, padam kod sediada, salin dan tampal kod berikut

```javascript
import Fastify from 'fastify'

const opts = {
  logger: true
}
  
  // We want to use pino-pretty only if there is a human watching this,
  // otherwise we log as newline-delimited JSON.
if (process.stdout.isTTY) {
  opts.logger = { 
    transport: 
        { 
            target: 'pino-pretty' 
        } 
  }
}
  
const app = Fastify(opts)

app.get('/', async (request, reply) => {
  return { hello: 'world' }
})

/**
 * Run the server!
 */
const start = async () => {
    try {
        await app.listen({ port: 8080 })
    } catch (err) {
        app.log.error(err)
        process.exit(1)
    }
}
start()
```

* Simpan / (_**Save**_) fail **app.js**.

* Di **Command Prompt** atau **Terminal**, taip kod berikut untuk mulakan aplikasi menggunakan **Fastify** untuk paparkan maklumat **Log** seperti contoh paparan berikut

```bash
npm run dev
```

* Berikut adalah contoh paparan jika berjaya

```
> latihan-1@1.0.0 dev
> node app.js

[20:23:20.358] INFO (58645): Server listening at http://[::1]:8080
[20:23:20.359] INFO (58645): Server listening at http://127.0.0.1:8080
```
