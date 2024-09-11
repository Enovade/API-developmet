[[_TOC_]]

# Latihan 10.7: _State Management with Pinia_

Latihan ini adalah untuk menunjukkan pemahaman penggunaan **Pinia as State Management** dalam pembangunan aplikasi menggunakan Nuxt3
<br>
Untuk maklumat lanjut berkenaan **Pinia*:
- [Vue Pinia](https://pinia.vuejs.org/)
- [Nuxt Pinia Module](https://pinia.vuejs.org/ssr/nuxt.html)

Latihan ini adalah sambungan dari latihan [Latihan 10.6: Pembangunan Nuxt Front-end](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%2010%20-%20Nuxt.js/Latihan%2010.6%20-%20Pembangunan%20Nuxt%20Front-end.md)

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
  app: {
    head: {
      script: [
        {
          src: 'https://cdn.jsdelivr.net/npm/flowbite@2.5.1/dist/flowbite.min.js',
          type: 'text/javascript',
          defer: true
        }
      ]
    }
  },
  compatibilityDate: '2024-04-03',
  devtools: { enabled: true },
  css: ['~/assets/css/main.css'],
  modules: ["@nuxtjs/tailwindcss", '@pinia/nuxt']
})
```

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

<img src="https://code.cloud-connect.asia/msp/akademi-cloud-connect/training-modules/pembangunan-aplikasi-moden/uploads/0612afb6201d1d80fb8a6a842a7fc30b/image.png" width=200>

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
<section class="bg-white dark:bg-gray-900">
    <div class="grid max-w-screen-xl px-4 py-8 mx-auto lg:gap-8 xl:gap-0 lg:py-16 lg:grid-cols-12">
        <div class="mr-auto place-self-center lg:col-span-7">
            <h1 class="max-w-2xl mb-4 text-4xl font-extrabold tracking-tight leading-none md:text-5xl xl:text-6xl dark:text-white">Latihan Aplikasi Moden</h1>
            <p class="max-w-2xl mb-6 font-light text-gray-500 lg:mb-8 md:text-lg lg:text-xl dark:text-gray-400">Latihan Nuxt.js, Prisma ORM, Fastify dan TailwindCSS.</p>
            <a href="#" class="inline-flex items-center justify-center px-5 py-3 mr-3 text-base font-medium text-center text-white rounded-lg bg-primary-700 hover:bg-primary-800 focus:ring-4 focus:ring-primary-300 dark:focus:ring-primary-900">
                Get started
                <svg class="w-5 h-5 ml-2 -mr-1" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
            </a>
            <a href="#" class="inline-flex items-center justify-center px-5 py-3 text-base font-medium text-center text-gray-900 border border-gray-300 rounded-lg hover:bg-gray-100 focus:ring-4 focus:ring-gray-100 dark:text-white dark:border-gray-700 dark:hover:bg-gray-700 dark:focus:ring-gray-800">
              <svg class="w-[30px] h-[30px] text-gray-800 dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24">
              <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 11h2v5m-2 0h4m-2.592-8.5h.01M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z"/>
            </svg> 
            &nbsp;Lihat Lagi
            </a> 
        </div>
        <div class="hidden lg:mt-0 lg:col-span-5 lg:flex">
            <img src="https://padu.gov.my/_next/image?url=%2Fimages%2Fjata_negara.png&w=256&q=75" alt="mockup">
        </div>                
    </div>
    
</section>

<div class=" p-6 items-center bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">

    <pre class="m-0">StrapiURL - {{ strapiURL }}</pre>
    <pre class="m-0">Identifier - {{ identifier }}</pre>
    <pre class="m-0">Katalaluan - {{ katalaluan }}</pre>
    <pre class="m-0">Jwt - {{ jwttoken }}</pre>
    
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

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/8c17a2786d70e141d7d996e1a23f3d67/image.png" width=600>

<hr>

# Langkah 5.0: Penggunaan devtools

* Di bahagian bawah browser, klik ikon berikut <img src="https://code.cloud-connect.asia/msp/akademi-cloud-connect/training-modules/pembangunan-aplikasi-moden/uploads/277b9494df9ae5befeb40a404cc8a304/image.png" width=50> untuk dapat contoh paparan seperti berikut

<img src="https://code.cloud-connect.asia/msp/akademi-cloud-connect/training-modules/pembangunan-aplikasi-moden/uploads/a17c5f69a86bff7631d57d0fa95efa96/image.png" width=400>

* Klik **stores** dan klik **ConfigStore** untuk dapat contoh paparan seperti berikut

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/d01f94c9b1408030b3d7e3ac9a7d668b/image.png" width=400>

