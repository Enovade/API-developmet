[[_TOC_]]

# Latihan 10.10: _Using Axios To Consume API_

Latihan ini adalah untuk menunjukkan pemahaman penggunaan **Axios** dalam kaedah untuk membaca **API** dari sumber luar.
<br>
Untuk maklumat lanjut rujuk pautan berikut:
- [https://axios-http.com/](https://axios-http.com/)
- [Axios Instance Custom Config](https://axios-http.com/docs/req_config) - kaedah yang flexible

Latihan ini adalah sambungan dari latihan [Latihan 10.9: Nuxt Server Routes](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%2010%20-%20Nuxt.js/Latihan%2010.9%20-%20Nuxt%20Server%20Routes.md)

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

# Langkah 6.0: Penggunaan Nuxt Server Routes dengan Axios
Langkah ini adalah untuk menggunakan **Nuxt Server Routes** dengan **Axios** untuk akses data dari **Pengguna API Endpoints**

Untuk langkah ini, sila rujuk latihan [Latihan 10.9 - Langkah 2.0: Pembangunan Data Pengguna Api Endpoints](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%2010%20-%20Nuxt.js/Latihan%2010.9%20-%20Nuxt%20Server%20Routes.md#langkah-20-pembangunan-data-pengguna-api-endpoints)


## Langkah 6.1: Penggunaan _GET Methods_ 
Langkah ini adalah untuk menggunakan **Nuxt Server Routes** dengan **Axios** untuk akses data dari **Pengguna API Endpoints** menggunakan **GET Methods**

* Buka fail **pengguna/index.get.ts**. Padam kod sedia ada, salin dan tampal kod berikut

```ts
import axios from "axios"
export default defineEventHandler( async (event) => {
  const result = await axios.get("http://127.0.0.1:8090/pengguna")
  .then(function (response) {
    return response.data
  })
  .catch(error => {
    console.log('error.response :>> ', error);
  })  
  return {
    senarai: result
  }
})
```

* Simpan / **Save** fail **pengguna/index.get.ts**

* Di ***Command Prompt*** taip kod seperti berikut untuk buka aplikasi Nuxt

```
npm run dev
```

* Buka fail **uji.http**, salin dan tampal kod berikut

```
###
GET http://localhost:3000/api/pengguna
```

* Simpan / **Save** fail **uji.http**

* Di fail **uji.http** untuk uji aplikasi. Klik **Send Request** untuk **GET http://localhost:3000/api/pengguna** dan lihat maklumbalas di VSCode.

* Berikut adalah contoh paparan jika berjaya:

```json
{
  "senarai": [
    {
      "id": 1,
      "nama": "jdn01",
      "email": "jpn@cloud-connect.asia",
      "alamat": "Everly Putrajaya",
      "daerah": "Putrajaya",
      "negeri": "Wilayah Persekutuan Putrajaya"
    }
  ]
}
```

## Langkah 6.2 - Latihan Penggunaan _POST Methods_
Latihan ini adalah untuk menggunakan **Nuxt Server Routes** dengan **Axios** untuk hantar data ke **Pengguna API Endpoints** menggunakan **POST Methods**

* Buka fail **uji.http**, salin dan tampal kod berikut

```
###
POST http://localhost:3000/api/pengguna
content-type: application/json

{
    "nama": "jdn",
    "email": "jdn@cloud-connect.asia",
    "alamat": "Everly Putrajaya",
    "daerah": "Putrajaya",
    "negeri": "Wilayah Persekutuan Putrajaya"
}
```

* Simpan / **Save** fail **uji.http**

* Di fail **uji.http** untuk uji aplikasi. Klik **Send Request** untuk **POST http://localhost:3000/api/pengguna** dan lihat maklumbalas di VSCode.

* Berikut adalah contoh kod **index.post.ts**

```ts
import axios from "axios"
export default defineEventHandler(async (event) => {
  const body = await readBody(event)
  // const myData = {
  //   nama: body.nama,
  //   email: body.email,
  //   alamat: body.alamat,
  //   daerah: body.daerah,
  //   negeri: body.negeri
  // }
  const result = await axios.post("http://127.0.0.1:8090/pengguna", body)
  .then(function (response) {
    return response.data
  })
  .catch(error => {
    console.log('error.response :>> ', error);
  })

  return {
    salam: "Salam Warga JDN!!",
    data: result
  }

})

```

## Langkah 6.3 - Latihan Penggunaan _UPDATE Methods_
Latihan ini adalah untuk menggunakan **Nuxt Server Routes** dengan **Axios** untuk mengemaskini data ke **Pengguna API Endpoints** menggunakan **PUT Methods**

* Buka fail **uji.http**, salin dan tampal kod berikut

```
###
PUT http://localhost:3000/api/pengguna/?id=<id yang dijana sebelum ini>
Content-Type: application/json

{
    "email": "b@a.com",
    "alamat": "kg baru majidee"
}
```

* Simpan / **Save** fail **uji.http**

* Di fail **uji.http** untuk uji aplikasi. Klik **Send Request** untuk **PUT http://localhost:3000/api/pengguna/?id=<id yang dijana sebelum ini>** dan lihat maklumbalas di VSCode.

* Berikut adalah contoh kod **index.put.ts**

```ts
import axios from 'axios'
export default defineEventHandler(async (event) => {
  const queryid = await getQuery(event)
  const body = await readBody(event)

  const result = await axios.put("http://127.0.0.1:8090/pengguna/" + queryid.id, body)
  .then(function (response) {
    return response.data
  })
  .catch(error => {
    console.log('error.response :>> ', error);
  })

  return {
    data: "Maklumat berjaya dikemaskini",
    id: queryid.id,
    nama: body.nama,
    email: body.emel
  }

})

```

## Langkah 6.4 - Latihan Penggunaan _DELETE Methods_
Latihan ini adalah untuk menggunakan **Nuxt Server Routes** dengan **Axios** untuk menghapuskan data di **Pengguna API Endpoints** menggunakan **PUT Methods**

* Buka fail **uji.http**, salin dan tampal kod berikut

```
###
DELETE http://localhost:3000/api/pengguna/?id=<id yang dijana sebelum ini>
```

* Simpan / **Save** fail **uji.http**

* Di fail **uji.http** untuk uji aplikasi. Klik **Send Request** untuk **http://localhost:3000/api/pengguna/?id=<id yang dijana sebelum ini>** dan lihat maklumbalas di VSCode.

* Berikut adalah contoh kod **index.delete.ts**

```ts
import axios from 'axios'
export default defineEventHandler(async (event) => {

  const queryid = await getQuery(event)

  const result = await axios.delete("http://127.0.0.1:8090/pengguna/" + queryid.id)
  .then(function (response) {
    return response.data
  })
  .catch(error => {
    console.log('error.response :>> ', error);
  })

  return {
    data: "Maklumat berjaya dihapuskan"
  }

})

```

# Latihan 7.0: Tambah data baru dari Laman Daftar
Latihan ini adalah untuk menggunakan **Nuxt Server Routes** dengan **Axios** untuk hantar data ke **Pengguna API Endpoints** menggunakan **POST Methods** melalui Laman Daftar

* Berikut adalah contoh kod **Daftar.vue**

```vue
<script setup lang="ts">
import axios from 'axios'
  definePageMeta({
    layout: false,
  })
  const form = reactive({
    nama: "",
    email: '',
    alamat: '',
    daerah: '',
    negeri: ''
  })
  const show = ref(true)

  const onSubmit = async (event: Event) => {
    event.preventDefault()
    const result = await axios.post("/api/pengguna", form)
    .then(function (response) {
      return response.data
    })
    .catch(error => {
      console.log('error.response :>> ', error);
    })

    alert(JSON.stringify(form))
  }

  const onReset = (event: Event) => {
    event.preventDefault()
    // Reset our form values
    form.nama = ''
    form.email = ''
    form.alamat = ''
    form.negeri = ''
    // Trick to reset/clear native browser form validation state
    show.value = false
    nextTick(() => {
      show.value = true
    })
  }
</script>

<template>
  <div>
    <section class="bg-gray-50 dark:bg-gray-900">
      <div class="flex flex-col items-center justify-center px-6 py-8 mx-auto md:h-screen lg:py-0">
          <NuxtLink to="/">
            <a href="#" class="flex items-center mb-6 text-2xl font-semibold text-gray-900 dark:text-white">
                <img class="w-22 h-20 mr-2" src="https://padu.gov.my/_next/image?url=%2Fimages%2Fjata_negara.png&w=256&q=75" alt="logo">
            </a>
          </NuxtLink>
          <div class="w-full bg-white rounded-lg shadow dark:border md:mt-0 sm:max-w-md xl:p-0 dark:bg-gray-800 dark:border-gray-700">
              <div class="p-6 space-y-4 md:space-y-6 sm:p-8">
                  <h1 class="text-xl font-bold leading-tight tracking-tight text-gray-900 md:text-2xl dark:text-white">
                      Laman Daftar
                  </h1>
                  <form @submit="onSubmit" @reset="onReset" v-if="show" class="space-y-4 md:space-y-6">
                      <div>
                          <label for="nama" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Nama</label>
                          <input type="text" v-model="form.nama" name="nama" id="nama" class="bg-gray-50 border border-gray-300 text-gray-900 rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Masukkan nama anda" required="">
                      </div>
                      <div>
                          <label for="email" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Emel</label>
                          <input type="email" v-model="form.email" name="email" id="email" class="bg-gray-50 border border-gray-300 text-gray-900 rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="name@company.com" required="">
                      </div>
                      <div>
                          <label for="alamat" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Alamat</label>
                          <input type="text" v-model="form.alamat" name="alamat" id="alamat" class="bg-gray-50 border border-gray-300 text-gray-900 rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Masukkan alamat terkini anda">
                      </div>
                      <div>
                        <label for="daerah" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Daerah</label>
                        <select v-model="form.daerah" name="daerah" id="daerah"  class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
                          <option selected>Pilih Daerah</option>
                          <option value="Johor Bahru">Johor Bahru</option>
                          <option value="Kota Tinggi">Kota Tinggi</option>
                          <option value="Muar">Muar</option>
                          <option value="Batu Pahat">Batu Pahat</option>
                        </select>
                      </div>
                      <div>
                          <label for="negeri" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Negeri</label>
                          <input type="text" v-model="form.negeri" name="negeri" id="negeri" class="bg-gray-50 border border-gray-300 text-gray-900 rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Masukkan nama anda">
                      </div>
                      <div class="flex items-center justify-between">
                          <div class="flex items-start">
                              <div class="flex items-center h-5">
                                <input id="remember" aria-describedby="remember" type="checkbox" class="w-4 h-4 border border-gray-300 rounded bg-gray-50 focus:ring-3 focus:ring-primary-300 dark:bg-gray-700 dark:border-gray-600 dark:focus:ring-primary-600 dark:ring-offset-gray-800" required="">
                              </div>
                              <div class="ml-3 text-sm">
                                <label for="remember" class="text-gray-500 dark:text-gray-300"><i>Remember me</i></label>
                              </div>
                          </div>
                          <a href="#" class="text-sm font-medium text-primary-600 hover:underline dark:text-primary-500">Terlupa Katalaluan?</a>
                      </div>
                      <button type="submit" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800">Hantar</button>
                      <button type="reset" class="focus:outline-none text-white bg-red-700 hover:bg-red-800 focus:ring-4 focus:ring-red-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2 dark:bg-red-600 dark:hover:bg-red-700 dark:focus:ring-red-900">Reset</button>
                      <p class="text-sm font-light text-gray-500 dark:text-gray-400">
                          Tiada akses? <a href="#" class="font-medium text-primary-600 hover:underline dark:text-primary-500">Daftar Sekarang</a>
                      </p>
                  </form>
              </div>
          </div>
      </div>
    </section>
  </div>
</template>

<style scoped></style>

```


# Langkah 8.0: Penggunaan _DataTable Components_

Latihan ini adalah untuk menggunakan **Nuxt Server Routes** dengan **Axios** untuk akses data dari **Pengguna API Endpoints** menggunakan **GET Methods** melalui Laman Pengguna

Latihan ini akan menggunakan **vue3-easy-data-table DataTable components** dari https://hc200ok.github.io/vue3-easy-data-table-doc/

* Taip kod berikut untuk **install** **vue3-easy-data-table DataTable components**

```
npm install vue3-easy-data-table
```

* Berikut adalah contoh kod **pengguna.vue**

```vue
<script setup lang="ts">

import Vue3EasyDataTable from 'vue3-easy-data-table';
import 'vue3-easy-data-table/dist/style.css';
import axios from 'axios';

const searchField = ["nama", "alamat","daerah","negeri"];
const searchValue = ref();
const loading =ref(true)

  const headers = [
    { text: "id", value: "id" },
    { text: "Nama", value: "nama", sortable: true },
    { text: "Emel", value: "email", sortable: true },
    { text: "Alamat", value: "alamat", sortable: true },
    { text: "Daerah", value: "daerah", sortable: true },
    { text: "Negeri", value: "negeri", sortable: true },
    { text: "Tindakan", value: "action" },
  ]

  let items = ref([])

  onMounted (() => {
    getPengguna()
  })

  async function getPengguna(){
    await axios.get("/api/pengguna")
    .then(function (response) {
      loading.value = false
      console.log('response.data :>> ', response.data.senarai);
      items.value = response.data.senarai
    })
    .catch(error => {
      loading.value = false
      console.log('error.response :>> ', error);
    })  
  }


</script>

<template>
  <div>
    Senarai Pengguna
    <Vue3EasyDataTable
        :headers="headers"
        :items="items"
        :search-field="searchField"
        :search-value="searchValue"
        show-index
        :loading="loading"
      >
        <template #loading>
          <img
            src="https://i.pinimg.com/originals/94/fd/2b/94fd2bf50097ade743220761f41693d5.gif"
            style="width: 100px; height: 80px;"
          />
        </template>
        
      </Vue3EasyDataTable>

  </div>
</template>

<style scoped></style>

```

