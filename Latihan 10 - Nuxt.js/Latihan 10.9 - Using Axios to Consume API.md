[[_TOC_]]

# Latihan 10.9: _Using Axios To Consume API_

Latihan ini adalah untuk menunjukkan pemahaman penggunaan **Axios** dalam kaedah untuk membaca **API** dari sumber luar.
<br>
Untuk maklumat lanjut rujuk pautan berikut:
- [https://axios-http.com/](https://axios-http.com/)
- [Axios Instance Custom Config](https://axios-http.com/docs/req_config) - kaedah yang flexible

Latihan ini adalah sambungan dari latihan [Latihan 10.8: Environment Variables](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%2010%20-%20Nuxt.js/Latihan%2010.8%20-%20Environment%20Variables.md)

> Pra-syarat latihan: Pastikan Back-end API dari [Latihan 8 - Pembangunan API dari MySQL Database yang baru](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%208%20-%20Pembangunan%20API%20dari%20MySQL%20Database%20yang%20baru.md) berfungsi.

# Langkah 1.0: Konfigurasi Axios

* Di **Command Prompt** atau **Terminal**, taip kod berikut untuk **install axios library**

```
npm install axios
```
* Jika berjaya, pastikan **axios** tersenarai di **dependencies** di fail **package.json**

```json
  "dependencies": {
    "@nuxt/icon": "^1.4.7",
    "@pinia/nuxt": "^0.5.4",
    "axios": "^1.7.5",
    "nuxt": "^3.12.4",
    "pinia": "^2.2.2",
    "vue": "latest"
  },
```

# Langkah 2.0: Dapatkan data dari API menggunakan Axios

* Buka fail **pengguna.vue**. Padam kod sedia ada, salin dan tampal kod berikut

```js
<script setup lang="ts">

import axios from 'axios';

//use onMounted to perform tasks such as fetching data from an API, initializing third-party libraries, or setting up event listeners
onMounted (() => {
  getPengguna()
})

async function getPengguna(){
  await axios.get("http://localhost:8090/pengguna")
  .then(function (response) {
    console.log('response.data :>> ', response);
  })
  .catch(error => {
    console.log('error.response :>> ', error);
  })  
}
</script>

<template>
  <div>
    Senarai Pengguna
  </div>
</template>

<style scoped></style>
```

* Simpan / save fail **pengguna.vue**

* Di **VSCode terminal**, taip kod berikut untuk buka aplikasi Nuxt

```
npm run dev
```

* Di internet browser, akses ke laman **Pengguna** dan **Right-Click -> Inspect -> Console** untuk lihat data

* Sila ambil perhatian kepada maklumat berikut

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/cfa73e65504f4daf8e89d8aaff42cc44/image.png" >

* Di **VSCode terminal**, taip **CTRL_C** untuk hentikan aplikasi Nuxt.

# Langkah 3.0: Menangani Isu CORS

* Untuk menangani isu **CORS** seperti langkah sebelum ini. Di **VSCode** sila buka projek [Latihan 8 - Pembangunan API dari MySQL Database yang baru](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%208%20-%20Pembangunan%20API%20dari%20MySQL%20Database%20yang%20baru.md)

* Di **VSCode Terminal** taip kod berikut untuk **install @fastify/cors plugins**

```bash
npm i @fastify/cors
```

* Buka fail **app.js**, padam kod sedia ada, salin dan tampal kod berikut

```js
import fastify from 'fastify'
import autoload from '@fastify/autoload'
import { dirname, join } from 'path'
import { fileURLToPath } from 'url'
import cors from '@fastify/cors'

const __dirname = dirname(fileURLToPath(import.meta.url))

export async function build (opts = {}) {
  const app = fastify(opts)

  await app.register(cors, { 
    origin: "*"
  })

  app.register(autoload, {
    dir: join(__dirname, 'routes')
  })

  app.register(autoload, {
    dir: join(__dirname, 'routes/pengguna')
  })

  app.register(autoload, {
    dir: join(__dirname, 'routes/salam')
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

* Simpan / save fail **app.js**

* Di **VSCode terminal**, taip kod berikut untuk buka aplikasi Fastify

```
npm run dev
```

# Langkah 4.0: Penggunaan Axios

* Kembali ke projek aplikasi **Nuxt**, Di **VSCode terminal**, taip kod berikut untuk buka aplikasi Nuxt

```
npm run dev
```

* Di internet browser, akses ke laman **Pengguna** dan **Right-Click -> Inspect -> Console** dan pastikan tiada masalah **CORS** seperti contoh paparan berikut

> Sila ambil perhatian kepada maklumat berikut <img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/820df7479484568122a5a18cd050ffef/image.png" width=700>

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/4fa29fd6c37d9eb9401f446a65ae39e3/image.png" width=700>

* Di **VSCode terminal**, taip **CTRL_C** untuk hentikan aplikasi Nuxt.

# Langkah 5.0: Dapatkan data dari API menggunakan Axios - Kaedah Axios Instance Custom Config

* Buka fail **pengguna.vue**. Padam kod sedia ada, salin dan tampal kod berikut

```js
<script setup lang="ts">

import axios from 'axios';

//use onMounted to perform tasks such as fetching data from an API, initializing third-party libraries, or setting up event listeners
onMounted (() => {
  getPengguna()
  dapatPengguna()
})

async function getPengguna(){
  await axios.get("http://localhost:8090/pengguna")
  .then(function (response) {
    console.log('response.data :>> ', response);
  })
  .catch(error => {
    console.log('error.response :>> ', error);
  })  
}

async function dapatPengguna(){
  await axios ({
    // default method is 'get'
    method: 'get',
    url: 'http://localhost:8090/pengguna'
    }
  )
  .then(function (response) {
    console.log("dapatPengguna: response.data :>> ", response.data);
    console.log("dapatPengguna: response.status :>> ", response.status);
    console.log("dapatPengguna: response.statusText :>> ", response.statusText);
    console.log("dapatPengguna: response.headers :>> ", response.headers);
    console.log("dapatPengguna: response.config :>> ",response.config);
  })
  .catch(error => {
    console.log('error.response :>> ', error);
  })  
}
</script>

<template>
  <div>
    Senarai Pengguna
  </div>
</template>

<style scoped></style>
```

* Simpan / save fail **pengguna.vue**

* Di **VSCode terminal**, taip kod berikut untuk buka aplikasi Nuxt

```
npm run dev
```

* Di internet browser, akses ke laman **Pengguna** dan **Right-Click -> Inspect -> Console** untuk lihat data seperti contoh paparan berikut

> Sila ambil perhatian kepada maklumat yang di paparkan

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/0bfdd00b46d9a29d020ab7acefa1718e/image.png" width=700>

* Di **VSCode terminal**, taip **CTRL_C** untuk hentikan aplikasi Nuxt.


