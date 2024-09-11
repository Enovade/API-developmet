[[_TOC_]]

# Latihan 10.8: _Environment Variables_
Latihan ini adalah untuk menunjukkan pemahaman penggunaan **Environment Variables** dalam pembangunan aplikasi menggunakan Nuxt3
<br>
Untuk maklumat lanjut rujuk pautan berikut:
- [https://nuxt.com/docs/guide/going-further/runtime-config#environment-variables](https://nuxt.com/docs/guide/going-further/runtime-config#environment-variables)
- [https://nuxt.com/docs/guide/directory-structure/env](https://nuxt.com/docs/guide/directory-structure/env)

Latihan ini adalah sambungan dari latihan [Latihan 10.7: State Management with Pinia](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%2010%20-%20Nuxt.js/Latihan%2010.7%20-%20State%20Management%20with%20Pinia.md)

# Langkah 1.0: Wujudkan fail _Environment Variables_

* Di aplikasi **VS Code**, wujudkan fail **.env**, salin dan tampal kod berikut

```
identifier=developer
password=Pentadbir123
rahsia=password123
```

* Simpan / save fail **.env**

# Langkah 2.0: Konfigurasi _Environment Variables_

* Buka fail **nuxt.config.ts**, padam kod sedia ada, salin dan tampal kod berikut

```
// https://nuxt.com/docs/api/configuration/nuxt-config
export default defineNuxtConfig({
  compatibilityDate: '2024-04-03',
  devtools: { enabled: true },
  modules: ['@bootstrap-vue-next/nuxt', '@nuxt/icon', "@pinia/nuxt"],
  css: ['bootstrap/dist/css/bootstrap.min.css'],
  runtimeConfig: {
    rahsia: process.env.rahsia,
    public: {
        identifier: process.env.identifier,
        password: process.env.password
    }
  },
})
```

* Simpan / save fail **nuxt.config.ts**

* Buka fail **index.vue** di dalam direktori **pages**, padam kod sedia ada, salin dan tampal kod berikut

```
<script setup>
import { useConfigStore } from '~~/stores/config';


// initilize Environment Variables
const configEnv = useRuntimeConfig();
// initilize Pinia State Management
const configStore = useConfigStore();

// calling Pinia State Management data
const strapiURL = configStore.strapiURL
const identifier = configStore.identifier
const katalaluan = configStore.password
let jwttoken = configStore.jwttoken


// configEnv.identifier and configEnv.password as public environment variables which is visible from client side.
console.log('configEnv.identifier :>> ', configEnv.identifier);
console.log('configEnv.password :>> ', configEnv.password);

// configEnv.rahsia as private environment variables which is visible only from server scripting. Check th  output from both terminal and browser console to see the difference
console.log('configEnv.rahsia :>> ', configEnv.rahsia);


onMounted (() => {
  if (jwttoken == null) {
    console.log('Tiada token')
    configStore.identifier = "nama baru"
    configStore.jwttoken = "token baru"
  }
})
</script>

<template>
  <div>
    <Head>
      <Title>Utama</Title>
    </Head>
    <div class="mt-4 p-5 bg-info text-white rounded">
      <h1>Salam Malaysia Madani</h1>
      <h2>Portal Latihan Cloud Native</h2>
      <p>Untuk maklumat lanjut sila buat pendaftaran</p>
      <BButton variant="outline-primary"><Icon name="mdi:square-edit-outline" size="1.5em" />&nbsp;Daftar</BButton>
      <br>
      <BCard class="mt-3" header="Pinia State Management">
        <pre class="m-0">StrapiURL - {{ strapiURL }}</pre>
        <pre class="m-0">Identifier - {{ identifier }}</pre>
        <pre class="m-0">Katalaluan - {{ katalaluan }}</pre>
        <pre class="m-0">Jwt - {{ jwttoken }}</pre>
      </BCard>
    </div>
  </div>
</template>

<style scoped></style>
```

* Simpan / save fail **index.vue**

# Langkah 3.0: Uji _Environment Variables_

* Di **Command Prompt**, taip kod berikut untuk buka aplikasi Nuxt 3

```
npm run dev
```

* Nota:

`configEnv.rahsia as private environment variables which is visible only from server scripting. Check th  output from both terminal and Nuxt DevTools atau browser console to see the difference`


* Contoh paparan di **Nuxt DevTools**

<img src="/uploads/0fd10e015788ff4e0a0a55390e98568a/image.png" width=700>

* Contoh paparan di **Terminal**

```bash
configEnv.identifier :>>  undefined
configEnv.password :>>  undefined
configEnv.rahsia :>>  password123
```
