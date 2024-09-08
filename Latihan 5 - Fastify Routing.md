[[_TOC_]]

# Latihan 5: Fastify Routing
Latihan ini adalah untuk menunjukkan pemahaman menggunakan **Routing** untuk **Fastify Framework**

Sila layari https://fastify.dev/docs/latest/Reference/Routes/ untuk maklumat lanjut 

Latihan ini adalah sambungan dari latihan [Latihan 4: Fastify Error Handling](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%204%20-%20Fastify%20Error%20Handling.md)

# Langkah 1.0: Tetapan Routing

* adalah

```bash
npm i @fastify/autoload
```

* Wujudkan direktori baru **routes** dan wujudkan fail baru **hello.js** di dalam direktori tersebut

* Buka fail **hello.js**, salin dan tampal kod berikut

```javascript

export default async function (app, opts = {}) {
 
  app.get('/', async (request, reply) => {
    return { hello: 'world' }
  })
  return app
}
```

* Simpan / (_**Save**_) fail **hello.js**.

* Buka fail **app.js**, padam kod sediaada, salin dan tampal kod berikut

```javascript
import fastify from 'fastify'
import hello from './routes/hello.js'

export async function build (opts = {}) {
  const app = fastify(opts)

  app.register(hello)
//   app.get('/', async (request, reply) => {
//     return { hello: 'world' }
//   })

  app.get('/error', async (request, reply) => {
    throw new Error('Ralat')
  })

  app.setErrorHandler(async (err, request, reply) => {
    request.log.error({ err })
    reply.code(err.statusCode || 500)

    return "I'm sorry, there was an error processing your request."
  })

  return app
}
```

* Simpan / (_**Save**_) fail **app.js**.

* Di **Command Prompt** atau **Terminal**, taip kod berikut untuk mulakan aplikasi **Fastify**

```bash
npm run dev
```

* Buka fail **uji.http** untuk uji aplikasi. Klik **Send Request** untuk **GET http://localhost:8090** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal**

# Langkah 2.0: Latihan Routing

* Wujudkan **endpoints route** baru **/salam** di fail baru **salam.js**  untuk beri maklumbalas seperti berikut

```json
{
  "data": "Salam Malaysia Madani!!!"
}
```

# Langkah 3.0: Penggunaan Autoload
Langkah adalah untuk menunjukkan pemahaman menggunakan **Autoload** untuk **Fastify Framework**

Sila layari https://github.com/fastify/fastify-autoload untuk maklumat lanjut

> Autoload is a plugin for Fastify that loads all plugins found in a directory and automatically configures routes matching the folder structure.

* **Install autoload plugins** dengan taip kod berikut di **Command Prompt** atau **Terminal**

```bash
npm i @fastify/autoload
```

* Buka fail **app.js**, padam kod sediaada, salin dan tampal kod berikut

```javascript
import fastify from 'fastify'
import autoload from '@fastify/autoload'
import { dirname, join } from 'path'

export async function build (opts = {}) {
  const app = fastify(opts)

  app.register(autoload, {
    dir: join(dirname(new URL(import.meta.url).pathname), 'routes')
})

  app.get('/error', async (request, reply) => {
    throw new Error('Ralat')
  })

  app.setErrorHandler(async (err, request, reply) => {
    request.log.error({ err })
    reply.code(err.statusCode || 500)

    return "I'm sorry, there was an error processing your request."
  })

  return app
}
```
* Simpan / (_**Save**_) fail **app.js**.
* Buka fail **uji.http** untuk uji aplikasi. Klik **Send Request** untuk **GET http://localhost:8090** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal**

# Langkah 3.0: Full Declaration Routing

* Di direktori **routes** wujudkan fail
```
fastify.route({
  method: 'GET',
  url: '/',
  schema: {
    querystring: {
      name: { type: 'string' },
      excitement: { type: 'integer' }
    },
    response: {
      200: {
        type: 'object',
        properties: {
          hello: { type: 'string' }
        }
      }
    }
  },
  handler: function (request, reply) {
    reply.send({ hello: 'world' })
  }
})
```
