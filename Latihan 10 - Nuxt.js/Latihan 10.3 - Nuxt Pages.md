[[_TOC_]]

# Latihan 10.3: Nuxt Pages
Latihan ini adalah untuk menunjukkan pemahaman **Nuxt Pages**. 

Latihan ini adalah sambungan dari latihan [Latihan 10.2: Nuxt UI Framework](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%2010%20-%20Nuxt.js/Latihan%2010.2%20-%20Nuxt%20UI%20Framework.md)

# Langkah 1.0: Wujudkan fail menggunakan _Command Nuxi_
Langkah ini adalah untuk konfigurasi _**Command Nuxi**_ untuk mewujudkan fail Nuxt 3

*  Di ***Command Prompt*** taip kod seperti berikut

```
npx nuxi add page index
```
- **index** adalah nama fail - index.vue

* Di **VS Code**, pastikan terdapat fail **index.vue** diwujudkan di dalam direktori **pages**

* Buka fail **index.vue** yang baru diwujudkan, tukar maklumat **Page: index** kepada **Salam Malaysia Madani**, seperti contoh paparan berikut

```vue
<script setup lang="ts"></script>

<template>
  <div>
    Salam Malaysia Madani
  </div>
</template>

<style scoped></style>

```

* Simpan / **Save** fail **index.vue**

* Buka fail **app.vue**, padam kod sediada, salin dan tampal kod berikut

```
<template>
  <div>
    <NuxtPage />
  </div>
</template>
```

* Simpan / **Save** fail **app.vue**

* Di ***Command Prompt*** taip kod seperti berikut untuk buka aplikasi Nuxt

```
npm run dev
```

* Di browser layari pautan berikut **http://localhost:3000/**

* Di aplikasi **Command Prompt**, taip **CTRL-C** untuk hentikan aplikasi.

## Langkah 1.1: Wujudkan fail Daftar menggunakan _Command Nuxi_

*  Di ***Command Prompt*** taip kod seperti berikut

```
npx nuxi add page daftar
```
- **daftar** adalah nama fail - **daftar.vue**

* Di **VS Code**, pastikan terdapat fail **daftar.vue** diwujudkan di dalam direktori **pages**

* Buka fail **daftar.vue** yang baru diwujudkan, tukar maklumat **Page: index** kepada **Daftar Pengguna**, seperti contoh paparan berikut

```vue
<script setup lang="ts"></script>

<template>
  <div>
    Daftar Pengguna
  </div>
</template>

<style scoped></style>
```

* Simpan / **Save** fail **daftar.vue**

* Di ***Command Prompt*** taip kod seperti berikut untuk buka aplikasi Nuxt

```
npm run dev
```

* Di browser layari pautan berikut **http://localhost:3000/daftar**

* Berikut adalah contoh paparan jika berjaya

<img src="https://code.cloud-connect.asia/Hanafiah/mindef-latihan-cloud-native/uploads/8434352d9a101a4af0934a01c1814427/image.png" width=550>

## Langkah 1.2: Wujudkan fail Pengguna menggunakan _Command Nuxi_

*  Di ***Command Prompt*** taip kod seperti berikut

```
npx nuxi add page pengguna
```
- **pengguna** adalah nama fail - pengguna.vue

* Di **VS Code**, pastikan terdapat fail **pengguna.vue** diwujudkan di dalam direktori **pages**


* Buka fail **pengguna.vue** yang baru diwujudkan, tukar maklumat **Page: index** kepada **Senarai Pengguna**, seperti contoh paparan berikut

```vue
<script setup lang="ts"></script>

<template>
  <div>
    Senarai Pengguna
  </div>
</template>

<style scoped></style>

```

* Simpan / **Save** fail **pengguna.vue**

* Di ***Command Prompt*** taip kod seperti berikut untuk buka aplikasi Nuxt

```
npm run dev
```

* Di browser layari pautan berikut **http://localhost:3000/pengguna**

* Berikut adalah contoh paparan jika berjaya

<img src="https://code.cloud-connect.asia/Hanafiah/mindef-latihan-cloud-native/uploads/f75c613c80b94cd841a60e91715ef866/image.png" width=550>

## Langkah 1.3: Wujudkan fail Login menggunakan _Command Nuxi_

*  Di ***Command Prompt*** taip kod seperti berikut

```
npx nuxi add page login
```
- **login** adalah nama fail - login.vue

* Di **VS Code**, pastikan terdapat fail **login.vue** diwujudkan di dalam direktori **pages**


* Buka fail **login.vue** yang baru diwujudkan, tukar maklumat **Page: index** kepada **Laman Login**, seperti contoh paparan berikut

```vue
<script setup lang="ts"></script>

<template>
  <div>
    Laman Login
  </div>
</template>

<style scoped></style>

```

* Simpan / **Save** fail **login.vue**

* Di ***Command Prompt*** taip kod seperti berikut untuk buka aplikasi Nuxt

```
npm run dev -- -o
```

* Di browser layari pautan berikut **http://localhost:3000/login**

* Berikut adalah contoh paparan jika berjaya

<img src="https://code.cloud-connect.asia/Hanafiah/mindef-latihan-cloud-native/uploads/adece9dc59f8c56477fa7b618973f5b7/image.png" width=550>

# Langkah 2.0: Wujudkan _Page Title_
Langkah ini adalah untuk mewujudkan _**Page Title**_ untuk untuk semua fail Nuxt

* Buka fail **index.vue**, padam maklumat sedia-ada, salin dan tampal kod berikut

```
<script lang="ts" setup></script>

<template>
  <div>
    <Head>
      <Title>Utama</Title>
    </Head>
    Salam Malaysia Madani
  </div>
</template>

<style scoped></style>
```

* Simpan / **Save** fail **index.vue**

* Buka fail **daftar.vue**, padam maklumat sedia-ada, salin dan tampal kod berikut

```
<script lang="ts" setup></script>

<template>
  <div>
    <Head>
      <Title>Daftar</Title>
    </Head>
    Daftar Pengguna
  </div>
</template>

<style scoped></style>
```

* Simpan / **Save** fail **daftar.vue**

* Buka fail **pengguna.vue**, padam maklumat sedia-ada, salin dan tampal kod berikut

```
<script lang="ts" setup></script>

<template>
  <div>
    <Head>
      <Title>Pengguna</Title>
    </Head>
    Senarai Pengguna
  </div>
</template>

<style scoped></style>
```

* Simpan / **Save** fail **pengguna.vue**

* Buka fail **login.vue**, padam maklumat sedia-ada, salin dan tampal kod berikut

```
<script lang="ts" setup></script>

<template>
  <div>
    <Head>
      <Title>Login</Title>
    </Head>
    Laman Login
  </div>
</template>

<style scoped></style>
```

* Simpan / **Save** fail **login.vue**

* Di ***Command Prompt*** taip kod seperti berikut untuk buka aplikasi Nuxt

```
npm run dev -- -o
```

* Di browser layari pautan berikut **http://localhost:3000/**, **http://localhost:3000/daftar**, **http://localhost:3000/pengguna** dan **http://localhost:3000/login**. Pastikan **Page Title** wujud untuk setiap laman.

# Langkah 3.0: Penggunaan UI Components
Langkah ini adalah untuk menggunakan UI components - **Hero Sections**

Untuk maklumat lanjut UI components - **Hero Sections** sila layari https://flowbite.com/blocks/marketing/hero/

* Buka fail **index.vue**, padam maklumat sedia-ada, salin dan tampal kod berikut

```vue
<script setup lang="ts"></script>

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
</template>

<style scoped></style>

```

* Simpan / **Save** fail **index.vue**

* Di browser layari pautan berikut **http://localhost:3000/**, berikut adalah contoh paparan

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/608ea575438940f4ddcd696941b39022/image.png" width=600>
