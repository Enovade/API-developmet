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

* Buka fail **uji.http** untuk uji aplikasi. Salin dan tampal kod berikut di akhir fail

```
###
GET http://localhost:8090/salam?mesej=Salam%20Malaysia%Madani

```

* Klik **Send Request** untuk **GET http://localhost:8090/salam?mesej=Salam%20Malaysia%Madani** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal**


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
          const mymesej = request.body.nama + ' - ' + request.body.emel
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

## Langkah 1.3 - Latihan PUT Validation

* Ubah kod di fail **salam.js** untuk mengemaskini maklumat dengan menggunakan **PUT Request**. Gunakan **params** dan **body** untuk **schema validation** dan **{ data: "Maklumat berjaya dikemaskini" }** untuk maklumbalas.

* Buka fail **uji.http** untuk uji aplikasi. Tambah kod berikut di akhir fail

```
###
PUT http://localhost:8090/salam/1001
Content-Type: application/json

{
    "nama": "Ujian",
    "emel": "a@a.com"
}
```

* Klik **Send Request** untuk **PUT http://localhost:8090/salam/1001** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal**

* Berikut adalah contoh kod

```javascript

app.route({
      method: 'PUT',
      url: '/salam/:id',
      schema: {
        params: {
          type: 'object',
          required: ['id'],
          properties: {
            id: {
              type: 'integer'
            },
          },
        },
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
        console.log(request.body)
        console.log(request.params)
        reply.send({data: "Maklumat berjaya dikemaskini" })
      }
    })
```

## Langkah 1.4 - Latihan DELETE Validation

* Ubah kod di fail **salam.js** untuk menghapuskan maklumat dengan menggunakan **DELETE Request**. Gunakan **params** untuk **schema validation** dan **{ data: "Maklumat berjaya dihapuskan" }** untuk maklumbalas.

* Buka fail **uji.http** untuk uji aplikasi. Tambah kod berikut di akhir fail

```
###
DELETE http://localhost:8090/salam/1001

```

* Klik **Send Request** untuk **DELETE http://localhost:8090/salam/1001** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal**

* Berikut adalah contoh kod

```javascript

app.route({
      method: 'DELETE',
      url: '/salam/:id',
      schema: {
        params: {
          type: 'object',
          required: ['id'],
          properties: {
            id: {
              type: 'integer'
            }
          },
        },
      },
      handler: function (request, reply) {
        console.log(request.params)
        reply.send({data: "Maklumat berjaya dihapuskan" })
      }
    })
```


# Langkah 2.0: Serialization
## Langkah 2.1: GET Serialization

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
          required: ['mesej']
        },
        response: {
          200: {
            type: 'object',
            properties: {
              data: { 
                type: 'string' 
              }
            },
            required: ['data']
          }
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

* Klik **Send Request** untuk **GET http://localhost:8090/salam?maklumat=Salam%20Malaysia%Madani** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal** 

## Langkah 2.2 - Latihan POST Serialization

* Ubah kod di fail **salam.js** untuk **Schema Response POST Serialization** dengan **{ data: "Maklumat berjaya diwujudkan" }** sebagai maklumbalas.

* Buka fail **uji.http** untuk uji aplikasi. Klik **Send Request** untuk **POST http://localhost:8090/salam** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal**

* Berikut adalah contoh kod

```javascript
export default async function (app, opts = {}) {
 
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
          },
          response: {
            200: {
              type: 'object',
              properties: {
                data: { 
                  type: 'string' 
                }
              },
              required: ['data']
            }
          }
        },
        handler: function (request, reply) {
          const mymesej = request.body.nama + ' ' + request.body.emel
          console.log(request.body)
          reply.send({ data: mymesej })
        }
      })
    return app
  }
  
```

## Langkah 2.3 - Latihan PUT Serialization

* Ubah kod di fail **salam.js** untuk **Schema Response PUT Serialization** dan **{ data: "Maklumat berjaya dikemaskini" }** untuk maklumbalas.

* Buka fail **uji.http** untuk uji aplikasi. Klik **Send Request** untuk **PUT http://localhost:8090/salam/1001** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal**

* Berikut adalah contoh kod

```javascript
export default async function (app, opts = {}) {
 
    app.route({
        method: 'PUT',
        url: '/salam/:id/:nama',
        schema: {
          params: {
            type: 'object',
            required: ['id'],
            properties: {
              id: {
                type: 'integer'
              },
              nama: {
                type: 'string'
              },
            },
          },
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
          },
          response: {
            200: {
              type: 'object',
              properties: {
                data: { 
                  type: 'string' 
                }
              },
              required: ['data']
            }
          }
        },
        handler: function (request, reply) {
          console.log(request.body)
          console.log(request.params)
          reply.send({data: "Maklumat berjaya dikemaskini" })
        }
      })

    return app
  }
  
```


## Langkah 2.4 - Latihan DELETE Serialization

* Ubah kod di fail **salam.js** untuk **Schema Response DELETE Serialization** dan **{ data: "Maklumat berjaya dihapuskan" }** untuk maklumbalas.

* Buka fail **uji.http** untuk uji aplikasi. Klik **Send Request** untuk **DELETE http://localhost:8090/salam/1001** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal**

* Berikut adalah contoh kod

```javascript
export default async function (app, opts = {}) {
 
    app.route({
        method: 'DELETE',
        url: '/salam/:id',
        schema: {
          params: {
            type: 'object',
            required: ['id'],
            properties: {
              id: {
                type: 'integer'
              }
            },
          },
          response: {
            200: {
              type: 'object',
              properties: {
                data: { 
                  type: 'string' 
                }
              },
              required: ['data']
            }
          }
        },
        handler: function (request, reply) {
          console.log(request.params)
          reply.send({data: "Maklumat berjaya dihapuskan" })
        }
      })
    
    return app
  }
  

```
