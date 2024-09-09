[[_TOC_]]

# Latihan 6: Fastify Validation and Serialization
Latihan ini adalah untuk menunjukkan pemahaman menggunakan **Validation and Serialization** untuk **Fastify Framework**

Sila layari https://fastify.dev/docs/latest/Reference/Validation-and-Serialization/ untuk maklumat lanjut 

Latihan ini adalah sambungan dari latihan [Latihan 5: Fastify Routing](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%205%20-%20Fastify%20Routing.md)

# Langkah 1.0: Validation
## Langkah 1.1: GET Validation

* Buka fail **salam.js**, padam kod sediada, salin dan tampal kod berikut

```javascript
export default async function (app, opts = {}) {
 
    app.route({
      method: 'GET',
      url: '/salam',
      schema: {
        querystring: {
          type: 'object',
          properties: {
            mesej: {
              type: 'string'
            },
          },
        }
      },
      handler: function (request, reply) {
        reply.send({ data: request.query.mesej })
      }
    })
    return app
  }
  
```

* Simpan / (_**Save**_) fail **salam.js**.

* Di **Command Prompt** atau **Terminal**, taip kod berikut untuk mulakan aplikasi **Fastify**

```bash
npm run dev
```

* Buka fail **uji.http** untuk uji aplikasi. Klik **Send Request** untuk **GET http://localhost:8090/salam?mesej=Salam%20Malaysia%Madani** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal**


## Langkah 1.2: POST Validation

* Buka fail **salam.js**, padam kod sediada, salin dan tampal kod berikut

```javascript
export default async function (app, opts = {}) {
 
    app.route({
      method: 'GET',
      url: '/salam',
      schema: {
        querystring: {
          type: 'object',
          properties: {
            mesej: {
              type: 'string'
            },
          },
        }
      },
      handler: function (request, reply) {
        reply.send({ data: request.query.mesej })
      }
    })
    app.route({
        method: 'POST',
        url: '/salam',
        schema: {
          body: {
            type: 'object',
            required: ['nama', 'emel'],
            properties: {
              nama: {
                type: 'string'
              },
              emel: {
                type: 'string'
              },
            },
          }
        },
        handler: function (request, reply) {
          const mymesej = request.body.nama + '' + request.body.emel
          console.log(request.body)
          reply.send({ data: mymesej })
        }
      })
    return app
  }
  
```

* Simpan / (_**Save**_) fail **salam.js**.

* Di **Command Prompt** atau **Terminal**, taip kod berikut untuk mulakan aplikasi **Fastify**

```bash
npm run dev
```

* Buka fail **uji.http** untuk uji aplikasi. Tambah kod berikut di akhir fail

```
###
POST http://localhost:8090/salam
Content-Type: application/json

{
    "nama": "Hanafiah",
    "emel": "hanafiah@cloud-connect.asia"
}
```

* Klik **Send Request** untuk **POST http://localhost:8090/salam** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal**

* Uji aplikasi dengan ubah **nama** ke **name** dan **emel** ke **email** dan lihat makumbalas di i VSCode dan **Command Prompt** atau **Terminal**
