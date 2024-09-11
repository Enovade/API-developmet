[[_TOC_]]

# Latihan 10.7: _State Management with Pinia_

Latihan ini adalah untuk menunjukkan pemahaman penggunaan **Pinia as State Management** dalam pembangunan aplikasi menggunakan Nuxt3
<br>
Untuk maklumat lanjut berkenaan **Pinia*:
- [Vue Pinia](https://pinia.vuejs.org/)
- [Nuxt Pinia Module](https://pinia.vuejs.org/ssr/nuxt.html)

Latihan ini adalah sambungan dari latihan [Latihan 6: Pembangunan Nuxt Front-end](https://code.cloud-connect.asia/msp/akademi-cloud-connect/training-modules/pembangunan-aplikasi-moden/-/blob/master/Latihan%2011/Latihan%206%20-%20Pembangunan%20Nuxt%20Front-end.md)

# Langkah 1.0: Konfigurasi _Pinia_

* Di ***Command Prompt*** taip kod seperti berikut untuk **install Pinia library**

```
npm install pinia -f
```

* kemudian **install Pinia Nuxt3 Module** dengan taip kod seperti berikut

```
npx nuxi@latest module add pinia
```

* Pastikan kedua-dua **Pinia Libraries** tersenarai di fail **package.json**, seperti contoh paparan berikut. (Maklumat versi mungkin berbeza)

```json
"dependencies": {
    "@pinia/nuxt": "^0.5.4",
    ...
    "pinia": "^2.2.2",
  }
```

* Buka fail **nuxt.config.ts**, dan pastikan **@pinia/nuxt** tersenarai di **modules** seperti contoh paparan berikut

```typescript
// https://nuxt.com/docs/api/configuration/nuxt-config
export default defineNuxtConfig({
  compatibilityDate: '2024-04-03',
  devtools: { enabled: true },
  modules: ['@bootstrap-vue-next/nuxt', '@nuxt/icon', "@pinia/nuxt"],
  css: ['bootstrap/dist/css/bootstrap.min.css'],
})
```

* Simpan / _save_ fail **nuxt.config.ts**

# Langkah 2.0: _Pinia State Management_

* Di **VS Code**, wujudkan direktori baru **stores**

* Di direktori **stores**, wujudkan fail baru **config.js**, salin dan tampal kod berikut

```javascript
export const useConfigStore = defineStore('ConfigStore', {
    state: () => {
      return {
        strapiURL: "http://latihan.cloud-connect.asia:1337",
        identifier: "developer",
        password: "Pentadbir123",
        jwttoken: null,
      };
    },
    getters: {},
    actions: {},
  });
```

<img src="/uploads/0612afb6201d1d80fb8a6a842a7fc30b/image.png" width=200>

* Simpan / _save_ fail **config.js**

# Langkah 3.0: _Using Pinia_

* Buka fail **index.vue**, padam kod sedia ada, salin dan tampal kod berikut

```vue
<script setup>
import { useConfigStore } from '~~/stores/config';

const configStore = useConfigStore();

const strapiURL = configStore.strapiURL
const identifier = configStore.identifier
const katalaluan = configStore.password
let jwttoken = configStore.jwttoken

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

* Simpan / _save_ fail **index.vue**

# Langkah 4.0: Uji Pinia

* Di **Command Prompt**, taip kod berikut untuk buka aplikasi Nuxt 3

```
npm run dev
```

* Berikut adalah contoh paparan jika berjaya

<img src="/uploads/dcb908ecbb5a43f00917d7465c95b3a9/image.png" width=600>

<hr>

# Langkah 5.0: Penggunaan devtools

* Di bahagian bawah browser, klik ikon berikut <img src="/uploads/277b9494df9ae5befeb40a404cc8a304/image.png" width=50> untuk dapat contoh paparan seperti berikut

<img src="/uploads/a17c5f69a86bff7631d57d0fa95efa96/image.png" width=400>

* Klik **stores** dan klik **ConfigStore** untuk dapat contoh paparan seperti berikut

<img src="/uploads/230946779495a826a58f3728243c86e8/image.png" width=400>

