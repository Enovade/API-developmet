[[_TOC_]]

# Latihan 2: Fastify Logging
Latihan ini adalah untuk menunjukkan pemahaman menggunakan **Logging** untuk **Fastify Framework**

Latihan ini adalah sambungan dari latihan [Latihan 1: Pengenalan Fastify](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%201%20-%20Pengenalan%20Fastify.md)

# Langkah 1.0: Enabling Logging
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
