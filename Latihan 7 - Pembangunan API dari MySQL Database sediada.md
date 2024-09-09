[[_TOC_]]

# Latihan 7: Pembangunan API dari MySQL Database sediada
Latihan ini adalah untuk menunjukkan pemahaman membangunkan MySQL API dari MySQL database yang sudah mempunyai data dengan menggunakan **_PRISMA ORM and Fastify Framework_**. Untuk latihan ini MySQL database server akan disediakan di persekitaran pengkomputeran awan.

**Nota:**
Jika hendak menyediakan persekitaran MySQL database untuk di komputer anda, sila rukjuk pautan berikut untuk maklumat lebih lanjut: https://dev.mysql.com/doc/mysql-installation-excerpt/8.0/en/windows-installation.html

Sila layari https://www.prisma.io/ untuk maklumat lanjut 

Latihan ini adalah sambungan dari latihan [Latihan 6: Fastify Validation and Serialization](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%206%20-%20Fastify%20Validation%20and%20Serialization.md)


# Langkah 1.0: _Install Visual Studio Code Prisma Extension_
Langkah ini adalah untuk _install Prisma extensions_ untuk memudahkan pembangunan MySQL API

* Di Visual Studio Code, dari senarai ikon di kiri, klik _**Extension**_

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/25165bc1d1cd649f14bd96da890e1a44/image.png">

* Buat carian, _**Prisma**_

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/5f4419f955484a1ea331170d4a44eebb/image.png" width=250>

* Klik Install

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/985a2a6ba548f3b9fefdd7bbe585b274/image.png" width=600>

# Langkah 2.0: _Install & Initialize_ Persekitaran Prisma
Langkah ini adalah untuk _install and initialize Prisma environment_ sebagai langkah untuk pembangunan MSQL API

* Di **Command Prompt** atau **Terminal**, taip kod seperti berikut untuk _**install Prisma Client**_

```
npm install prisma --save-dev
```

* Taip kod seperti berikut untuk _**initialize Prisma environment**_

```
npx prisma init
```

* Jika berjaya, sila rujuk paparan berikut:

```bash
> npx prisma init

✔ Your Prisma schema was created at prisma/schema.prisma
  You can now open it in your favorite editor.

Next steps:
1. Set the DATABASE_URL in the .env file to point to your existing database. If your database has no tables yet, read https://pris.ly/d/getting-started
2. Set the provider of the datasource block in schema.prisma to match your database: postgresql, mysql, sqlite, sqlserver, mongodb or cockroachdb.
3. Run prisma db pull to turn your database schema into a Prisma schema.
4. Run prisma generate to generate the Prisma Client. You can then start querying your database.
5. Tip: Explore how you can extend the ORM with scalable connection pooling, global caching, and real-time database events. Read: https://pris.ly/cli/beyond-orm

More information in our documentation:
https://pris.ly/d/getting-started

```

* Pastikan direktori **prisma**, fail **.env** dan **prisma/schema.prisma** diwujudkan. Sila rujuk paparan berikut:

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/3613cd309d3e1f9f5d6b4dd3098edc0b/image.png" width=300>

# Langkah 3.0: _Connecting to MySQL Database using Prisma_
Langkah ini adalah untuk membuat _connection_ ke MSQL database

* Buka fail **.env**, tukar maklumat **DATABASE_URL** dengan salin dan tampal kod seperti berikut

```
DATABASE_URL="mysql://pentadbir:rahsia@167.71.217.175:3306/testdb"
```

```
Nota:
- pentadbir : adalah username untuk akses ke MySQL database
- rahsia : adalah katalaulan untuk username root
- 167.71.217.175 : adalah database server URL atau IP address localhost / 127.0.0.1 jika dari komputer sendiri
- 3306 : adalah port untuk MySQL server
- testdb : adalah nama database
```

* Simpan / (Save) fail.

* Buka fail **schema.prisma** di direktori **prisma**, tukar maklumat **datasource db** dengan salin dan tampal kod seperti berikut

```
datasource db {
  provider = "mysql"
  url      = env("DATABASE_URL")
}
```

* Simpan / (Save) fail **schema.prisma**. Berikut adalah contoh kod:

```
// This is your Prisma schema file,
// learn more about it in the docs: https://pris.ly/d/prisma-schema

// Looking for ways to speed up your queries, or scale easily with your serverless or edge functions?
// Try Prisma Accelerate: https://pris.ly/cli/accelerate-init

generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "mysql"
  url      = env("DATABASE_URL")
}

```

# Langkah 4.0: Penggunaan _Prisma db pull_
Langkah ini adalah untuk menggunakan **Prisma db pull** untuk akses semua maklumat **table** di **testdb** database dan menjana **schema** untuk **Prisma** 

* Di **Command Prompt** atau **Terminal**, taip kod seperti berikut

```
npx prisma db pull
```

* Setelah selesai, buka fail **schema.prisma**, Berikut adalah contoh kod yang telah dijana:

```
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "mysql"
  url      = env("DATABASE_URL")
}

model pengguna {
  id     Int    @id @default(autoincrement()) @db.UnsignedInt
  nama   String @unique(map: "pengguna.nama_unique") @db.VarChar(255)
  email  String @db.VarChar(255)
  alamat String @db.VarChar(255)
  daerah String @db.VarChar(255)
  negeri String @db.VarChar(255)
}

```

# Langkah 5.0: Penggunaan _Prisma Generate_
Langkah ini adalah untuk menggunakan **Prisma Generate** untuk **generate Prisma Client**

* Di **Command Prompt** atau **Terminal**, taip kod seperti berikut

```
npx prisma generate
```

* Berikut adalah contoh paparan jika berjaya

```bash
Environment variables loaded from .env
Prisma schema loaded from prisma/schema.prisma

✔ Installed the @prisma/client and prisma packages in your project

✔ Generated Prisma Client (v5.19.1) to ./node_modules/@prisma/client in 31ms

Start by importing your Prisma Client (See: http://pris.ly/d/importing-client)

Tip: Easily identify and fix slow SQL queries in your app. Optimize helps you enhance your visibility: https://pris.ly/--optimize
```

# Langkah 6.0: Penggunaan _Prisma Studio_
Langkah ini adalah untuk menggunakan **Prisma Studio** untuk akses MySQL database

* Di **Command Prompt** atau **Terminal**, taip kod seperti berikut

```
npx prisma studio
```
atau

```
npx prisma studio --browser none
```

* Jika berjaya, sila rujuk paparan berikut:

```bash

> npx prisma studio
Environment variables loaded from .env
Prisma schema loaded from prisma/schema.prisma
Prisma Studio is up on http://localhost:5555
```

* Buka **internet browser** dengan URL http://localhost:5555/ seperti paparan berikut

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/7da9841ad5d0d1ee6485ed03b314bbad/image.png" width=500>

* Untuk melihat data di database. Klik **pengguna** di senarai **All Models**, sila rujuk paparan berikut

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/93ec26f059e6dd367d554e191af8a89b/image.png">

* klik **CTRL-C** untuk hentikan aplikasi **Prisma Studio**


# Langkah 7.0: _Install Prisma Client_
Langkah ini adalah untuk _Install Prisma Client_
<br>

*  Di **Command Prompt** atau **Terminal**, taip kod seperti berikut

```
npm install @prisma/client
```

# Langkah 8.0: Pembangunan API menggunakan Fastify & Prisma ORM

## Langkah 8.1: _READ API for MySQL_
Langkah ini adalah untuk membangunkan _Read API for MySQL_ untuk membaca data di **table Pengguna**

* Wujudkan fail baru **pengguna.js** di direktori **routes**. Salin dan tampal kod berikut 

```
import { PrismaClient }  from '@prisma/client';
const prisma = new PrismaClient();

export default async function (app, opts = {}) {
 
  // READ API
  app.route({
    method: 'GET',
    url: '/pengguna',
    handler: async function (request, reply) {
      const jawapan = await prisma.pengguna.findMany();
      reply.send(jawapan)
    }
  })

  // CREATE / ADD API

  // UPDATE API

  // DELETE API

  return app
}
```

* Simpan / (_**Save**_) fail **pengguna.js**. 

## Langkah 8.2: Uji _READ API for MySQL_

* Di **Command Prompt** atau **Terminal**, taip kod berikut untuk mulakan aplikasi **Fastify**

```bash
npm run dev
```

* Buka fail **uji.http**. Salin dan tampal kod berikut di akhir fail

```
###
http://localhost:8090/pengguna
```
* Simpan / (_**Save**_) fail u**uji.http**. 

* Di fail **uji.http** untuk uji aplikasi. Klik **Send Request** untuk **GET http://localhost:8090/pengguna** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal**


* Berikut adalah contoh paparan jika berjaya:

```json
[
  {
    "id": 944,
    "nama": "hanafiah",
    "email": "user1@cloud-connect.asia",
    "alamat": "Space U8, Bukit Jelutong",
    "daerah": "Shah Alam",
    "negeri": "Selangor"
  },
  .....
  .....
  {
    "id": 968,
    "nama": "yana",
    "email": "yana@cloud-connect.asia",
    "alamat": "Space U8, Bukit Jelutong",
    "daerah": "Shah Alam",
    "negeri": "Selangor"
  }
]

```

* Sila pastikan data adalah sama dengan maklumat laman **Prisma Studio** seperti di Langkah 6.0

## Langkah 8.3: _CREATE / Add API for MySQL_
Langkah ini adalah untuk membangunkan _Create / Add API for MySQL_ untuk wujudkan atau tambah data di **table Pengguna**

* Di fail **pengguna.js**. Salin dan tampal kod berikut pada kod sediada

```

// CREATE / ADD API
  // contoh maklumat yang dihantar
  // {
  //     "nama": "user1",
  //     "email": "user@cloud-connect.asia",
  //     "alamat": "Kg Melayu Kangkar Pulai",
  //     "daerah": "Johor Bahru",
  //     "negeri": "Johor"
  // }
  app.route({
    method: 'POST',
    url: '/pengguna',
    schema: {
      body: {
        type: 'object',
        required: ['nama', 'email'],
        properties: {
          nama: {
            type: 'string'
          },
          email: {
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
    handler: async function (request, reply) {
      const jawapan = await prisma.pengguna.create({ data: request.body });
      console.log(jawapan)
      reply.send({ data: jawapan })
    }
  })
```

* Simpan / (_**Save**_) fail **pengguna.js**. 

## Langkah 8.4: Uji _CREATE API for MySQL_

* Buka fail **uji.http**. Salin dan tampal kod berikut di akhir fail

```
###
POST http://localhost:8090/pengguna
content-type: application/json

{
    "nama": "jpnuser",
    "email": "jpn@cloud-connect.asia",
    "alamat": "Everly Putrajaya",
    "daerah": "Putrajaya",
    "negeri": "Wilayah Persekutuan Putrajaya"
}
```
* Simpan / (_**Save**_) fail u**uji.http**. 

* Di fail **uji.http** untuk uji aplikasi. Klik **Send Request** untuk **POST http://localhost:8090/pengguna** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal**

* Sila pastikan data yang dimasukkan tersenarai dalam database dengan membuat ujian seperti **Langkah 8.2**

## Langkah 8.5 - Latihan _UPDATE API for MySQL_

* Latihan ini adalah untuk membangunkan **_Update API for MySQL_** untuk menukar data di **table Pengguna**

* Ubah kod di fail **pengguna.js** untuk mengemaskini maklumat dengan menggunakan **PUT Request**. Gunakan **params** dan **body** untuk **schema validation** dan **{ data: "Maklumat berjaya dikemaskini" }** untuk maklumbalas.

> Gunakan fungsi Prisma berikut - **prisma.pengguna.update({ where: { id: request.params.id } , data: request.body })**

* Buka fail **uji.http** untuk uji aplikasi. Tambah kod berikut di akhir fail

```
###
PUT http://localhost:8080/pengguna/<id data yang baru dijana>
content-type: application/json

{
  "emel": "emel@baru.com
  "alamat": "Kg Nong Chik"
}
```

* Di fail **uji.http** untuk uji aplikasi. Klik **Send Request** untuk **http://localhost:8080/pengguna/<id data yang baru dijana>** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal**

* Sila pastikan data yang dikemaskini tersenarai dalam database dengan membuat ujian seperti **Langkah 8.2**


## Langkah 8.5 - Latihan _DELETE API for MySQL_

* Langkah ini adalah untuk membangunkan _DELETE API for MySQL_ untuk membuang data di **table Pengguna**

* Ubah kod di fail **salam.js** untuk menghapuskan maklumat dengan menggunakan **DELETE Request**. Gunakan **params** untuk **schema validation** dan **{ data: "Maklumat berjaya dihapuskan" }** untuk maklumbalas.

> Gunakan fungsi Prisma berikut - **prisma.pengguna.delete({ where: { id: request.params.id }})**


* Buka fail **uji.http** untuk uji aplikasi. Tambah kod berikut di akhir fail

```
###
DELETE http://localhost:8090/salam/<id data yang baru dijana>

```

* Klik **Send Request** untuk **DELETE http://localhost:8090/salam/<id data yang baru dijana>** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal**

* Sila pastikan data yang dihapuskan tiada dalam senarai dengan membuat ujian seperti **Langkah 8.2**

