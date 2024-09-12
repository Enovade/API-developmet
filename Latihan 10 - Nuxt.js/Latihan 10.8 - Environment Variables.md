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
IDENTIFIER=developer
PASSWORD=Pentadbir123
RAHSIA=password123
```

* Simpan / save fail **.env**

# Langkah 2.0: Konfigurasi _Environment Variables_

* Buka fail **nuxt.config.ts**, padam kod sedia ada, salin dan tampal kod berikut

```
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
  modules: ["@nuxtjs/tailwindcss", '@pinia/nuxt'],
  runtimeConfig: {
    rahsia: process.env.RAHSIA,
    public: {
        identifier: process.env.IDENTIFIER,
        password: process.env.PASSWORD
    }

  },
})
```

* Simpan / save fail **nuxt.config.ts**

* Buka fail **index.vue** di dalam direktori **pages**, padam kod sedia ada, salin dan tampal kod berikut

```vue
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
