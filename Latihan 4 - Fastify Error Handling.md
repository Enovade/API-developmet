# Latihan 4: Error Handling
Latihan ini adalah untuk menunjukkan pemahaman menggunakan **Error Handling** untuk **Fastify Framework**

Sila layari https://fastify.dev/docs/latest/Reference/Errors/ untuk maklumat lanjut 

Latihan ini adalah sambungan dari latihan [Latihan 3: Environment Variables](https://github.com/Enovade/API-developmet/blob/master/Latihan%203%20-%20Environment%20Variables.md)

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

* Simpan / (_**Save**_) fail **app.js**.

* Di **Command Prompt** atau **Terminal**, taip kod berikut untuk mulakan aplikasi **Fastify**

```bash
npm run dev
```

* Buka **uji.http**, padam kod sediada, salin dan tampal kod berikut

```
GET http://localhost:8090

###
GET http://localhost:8090/error

###
GET http://localhost:8090/error

```

* Simpan / (_**Save**_) fail **uji.http**. Klik **Send Request** untuk **GET http://localhost:8090/error** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal**

