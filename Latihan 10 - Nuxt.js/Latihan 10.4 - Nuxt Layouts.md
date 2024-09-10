[[_TOC_]]

# Latihan 10.4: _**Nuxt Layouts**_
Latihan ini adalah untuk menunjukkan pemahaman **Nuxt Layouts**. 

Latihan ini adalah sambungan dari latihan [Latihan 10.3: Nuxt Pages](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%2010%20-%20Nuxt.js/Latihan%2010.3%20-%20Nuxt%20Pages.md)

Sila rujuk pautan ini untuk **Nuxt Layouts** [https://nuxt.com/docs/guide/directory-structure/layouts](https://nuxt.com/docs/guide/directory-structure/layouts) 


# Langkah 1.0: Wujudkan _**Nuxt Layouts**_

* Di aplikasi ***Command Prompt***, taip kod berikut untuk wujudkan **Nuxt Layouts**

```
npx nuxi add layout default
```

* **default** adalah nama fail - **default.vue**

* Di VS Code, pastikan terdapat fail **default.vue** diwujudkan di dalam direktori **layouts**

* Buka fail **default.vue** yang baru diwujudkan, seperti contoh paparan berikut

<img src="https://code.cloud-connect.asia/Hanafiah/mindef-latihan-cloud-native/uploads/a4742ab32cec68881d6c7af111ca5b4a/image.png" width=550>

# Langkah 2.0: Konfigurasi _**Nuxt Layouts**_

## Langkah 2.1: Konfigurasi untuk **default layouts**

* Di VS Code, buka fail **app.vue**, padam maklumat sedia ada, salin dan tampal kod berikut

```
<template>
  <div>
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
  </div>
</template>
```

* Simpan / **Save** fail **app.vue**

* Di browser layari pautan berikut **http://localhost:3000/**. Pastikan terdapat **Layout: default** di paparan

* Berikut adalah contoh paparan jika berjaya

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/f77f44ba44a55b54d743a07f551d9a7b/image.png" width=550>

* Pastikan juga di pautan **http://localhost:3000/daftar**, **http://localhost:3000/pengguna** dan **http://localhost:3000/login** terdapat **Layout: default** di paparan.

## Langkah 2.2: Konfigurasi untuk tiada **layouts**

* Buka fail **login.vue** di direktori **pages**, padam maklumat sedia ada, salin dan tampal kod berikut

```
<script setup lang="ts">
  definePageMeta({
    layout: false,
  });
</script>

<template>
  <div>
    Laman Login
  </div>
</template>

<style scoped></style>

```
* Simpan / **Save** fail **login.vue**

* Di browser layari pautan berikut **http://localhost:3000/login**. Pastikan **tidak** terdapat **Layout: default** di paparan.

# Langkah 3.0: **Navigation Bar Layouts**

Sila rujuk pautan ini untuk **Navigation Bar Components** [https://flowbite.com/blocks/e-commerce/navbars/](https://flowbite.com/blocks/e-commerce/navbars/) 

* Buka fail **default.vue** di direktori **layouts**, padam maklumat sedia ada, salin dan tampal kod berikut

```vue
<script setup lang="ts"></script>

<template>
  <div>
    <nav class="bg-white dark:bg-gray-800 antialiased">
      <div class="max-w-screen-xl px-4 mx-auto 2xl:px-0 py-4">
        <div class="flex items-center justify-between">

          <div class="flex items-center space-x-8">
            <div class="shrink-0">
              <a href="#" title="" class="">
                <img class="block w-auto h-8 dark:hidden" src="https://padu.gov.my/_next/image?url=%2Fimages%2Fjata_negara.png&w=256&q=75" alt="">
                <img class="hidden w-auto h-8 dark:block" src="https://padu.gov.my/_next/image?url=%2Fimages%2Fjata_negara.png&w=256&q=75" alt="">
              </a>
            </div>

            <ul class="hidden lg:flex items-center justify-start gap-6 md:gap-8 py-3 sm:justify-center">
              <li>
                <NuxtLink to="/">
                  <a href="#" title="" class="flex text-sm font-medium text-gray-900 hover:text-primary-700 dark:text-white dark:hover:text-primary-500">
                    Utama
                  </a>
                </NuxtLink>
              </li>
              <li class="shrink-0">
                <NuxtLink to="/daftar">
                  <a href="#" title="" class="flex text-sm font-medium text-gray-900 hover:text-primary-700 dark:text-white dark:hover:text-primary-500">
                    Daftar
                  </a>
                </NuxtLink>
              </li>
              <li class="shrink-0">
                <NuxtLink to="/pengguna">
                  <a href="" title="" class="flex text-sm font-medium text-gray-900 hover:text-primary-700 dark:text-white dark:hover:text-primary-500">
                    Pengguna
                  </a>
                </NuxtLink>
              </li>
              <li class="shrink-0">
                <NuxtLink to="/login">
                  <a href="#" title="" class="text-sm font-medium text-gray-900 hover:text-primary-700 dark:text-white dark:hover:text-primary-500">
                    Login
                  </a>
                </NuxtLink>
              </li>
            </ul>
          </div> 
        </div>
      </div>
    </nav>
    <slot />
  </div>
</template>

<style scoped></style>

```

* Simpan / **Save** fail **default.vue**

* Di browser layari pautan berikut **http://localhost:3000/**. Pastikan terdapat **Navigation Bar** di paparan seperti contoh berikut

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/046751f296616ec4618d4075968b8a73/image.png" width=700>

* Pastikan juga di pautan **http://localhost:3000/daftar** dan **http://localhost:3000/pengguna** terdapat **Navigation Bar**  di paparan.

* Pastikan di pautan **http://localhost:3000/login** tidak terdapat **Navigation Bar** seperti contoh paparan berikut

<img src="https://code.cloud-connect.asia/Hanafiah/mindef-latihan-cloud-native/uploads/9182ae8973c3da3a629430cff75f59b7/image.png" width=550>

