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

* Wujudkan direktori baru **routes** dan wujudkan fail baru **routes.js** di dalam direktori tersebut

* Buka fail **routes.js**, salin dan tampal kod berikut

```javascript
import fastify from 'fastify'

export async function build (opts = {}) {
  const app = fastify(opts)

  app.get('/', async (request, reply) => {
    return { hello: 'world' }
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

* Buka fail **app.js**, padam kod sediaada, salin dan tampal kod berikut

```

```

* Buka fail **server.js**, ubah kod berikut

```
import { build } from './app.js'
```
kepada

```
import { build } from './routes/app.js'
```

* Simpan / (_**Save**_) fail **server.js**.

* Di **Command Prompt** atau **Terminal**, taip kod berikut untuk mulakan aplikasi **Fastify**

```bash
npm run dev
```

* Buka fail **uji.http** untuk uji aplikasi

# Langkah 2.0: Full Declaration Routing

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
