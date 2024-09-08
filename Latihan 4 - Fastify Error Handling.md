[[_TOC_]]

# Latihan 4: Error Handling
Latihan ini adalah untuk menunjukkan pemahaman menggunakan **Error Handling** untuk **Fastify Framework**

Sila layari https://fastify.dev/docs/latest/Reference/Errors/ untuk maklumat lanjut 

Latihan ini adalah sambungan dari latihan [Latihan 3: Environment Variables](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%203%20-%20Environment%20Variables.md)

# Langkah 1.0: Tetapan Error Handling

* Buka fail **app.js**, padam kod sediada, salin dan tampal kod berikut

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

    return "Maaf!! Terdapat ralat di aplikasi anda."
  })

  return app
}
```

* **Install dotenv plugins** dengan taip kod berikut di **Command Prompt** atau **Terminal**

```bash
npm i dotenv
```
