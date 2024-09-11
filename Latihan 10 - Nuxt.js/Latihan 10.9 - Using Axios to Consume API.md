[[_TOC_]]

# Latihan 10.9: _Using Axios To Consume API_

Latihan ini adalah untuk menunjukkan pemahaman penggunaan **Axios** dalam kaedah untuk membaca **API** dari sumber luar.
<br>
Untuk maklumat lanjut rujuk pautan berikut:
- [https://axios-http.com/](https://axios-http.com/)
- [Axios Instance Custom Config](https://axios-http.com/docs/req_config) - kaedah yang flexible

Latihan ini adalah sambungan dari latihan [Latihan 10.8: Environment Variables](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%2010%20-%20Nuxt.js/Latihan%2010.8%20-%20Environment%20Variables.md)

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

```
<script setup lang="ts">

import axios from 'axios';

//use onMounted to perform tasks such as fetching data from an API, initializing third-party libraries, or setting up event listeners
onMounted (() => {
  getPengguna()
})

async function getPengguna(){
  await axios.get("http://latihan.cloud-connect.asia:8080/pengguna")
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
    Page: pengguna
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

> Sila ambil perhatian kepada maklumat berikut <img src="/uploads/95075b0a5e19faec1c7a320d4a50c433/image.png" width=300>

<img src="/uploads/2931e7baceed9245bb34f1df97327085/image.png" width=700>

* Di **VSCode terminal**, taip **CTRL_C** untuk hentikan aplikasi Nuxt.


# Langkah 3.0: Dapatkan data dari API menggunakan Axios - Kaedah Axios Instance Custom Config

* Buka fail **pengguna.vue**. Padam kod sedia ada, salin dan tampal kod berikut

```
<script setup lang="ts">

import axios from 'axios';

//use onMounted to perform tasks such as fetching data from an API, initializing third-party libraries, or setting up event listeners
onMounted (() => {
  getPengguna()
  dapatPengguna()
})

async function getPengguna(){
  await axios.get("http://latihan.cloud-connect.asia:8080/pengguna")
  .then(function (response) {
    console.log('getPengguna: response.data :>> ', response);
  })
  .catch(error => {
    console.log('error.response :>> ', error);
  })  
}

async function dapatPengguna(){
  await axios ({
    // default method is 'get'
    method: 'get',
    url: 'http://latihan.cloud-connect.asia:8080/pengguna'
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
    Page: pengguna
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

<img src="/uploads/fc820c180768e5431be6942390120937/image.png" width=700>

* Di **VSCode terminal**, taip **CTRL_C** untuk hentikan aplikasi Nuxt.


