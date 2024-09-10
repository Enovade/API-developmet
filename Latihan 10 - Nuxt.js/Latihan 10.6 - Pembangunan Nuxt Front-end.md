[[_TOC_]]

# Latihan 10.6: Pembangunan Nuxt Front-end

Latihan ini adalah untuk menunjukkan pemahaman pembangunan **Nuxt Front-end** yang akan menggunakan **Nuxt Pages, Layouts, Components** yang diwujudkan dari latihan sebelum ini.

Latihan ini adalah sambungan dari latihan [Latihan 5: Nuxt Components](https://code.cloud-connect.asia/msp/akademi-cloud-connect/training-modules/pembangunan-aplikasi-moden/-/blob/master/Latihan%2011/Latihan%205%20-%20Nuxt%20Components.md)


# Langkah 1.0: Laman Login

## Langkah 1.1: Ubah Laman Login

* Di VS Code, buka fail **login.vue** di direktori **pages**, padam kod sedia ada, salin dan tampal kod berikut

```vue
<script setup lang="ts">
  definePageMeta({
    layout: false,
  })
  const form = reactive({
    emel: '',
    katalaluan: ''
  })
  const show = ref(true)

  const onSubmit = (event: Event) => {
    event.preventDefault()
    alert(JSON.stringify(form))
  }

  const onReset = (event: Event) => {
    event.preventDefault()
    // Reset our form values
    form.emel = ''
    form.katalaluan = ''
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
                      Laman Login
                  </h1>
                  <form @submit="onSubmit" @reset="onReset" v-if="show" class="space-y-4 md:space-y-6">
                      <div>
                          <label for="email" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Emel</label>
                          <input type="email" v-model="form.emel" name="email" id="email" class="bg-gray-50 border border-gray-300 text-gray-900 rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="name@company.com" required="">
                      </div>
                      <div>
                          <label for="password" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Katalaluan</label>
                          <input type="password" v-model="form.katalaluan" name="password" id="password" placeholder="••••••••" class="bg-gray-50 border border-gray-300 text-gray-900 rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" required="">
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

* Simpan / **Save** fail **login.vue**

## Langkah 1.2: Uji Laman Login

* * Di ***Command Prompt*** taip kod seperti berikut untuk buka aplikasi Nuxt

```
npm run dev
```

* Di browser layari pautan berikut **http://localhost:3000/login**, berikut adalah contoh paparan

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/583ad2e7c1c3dde9b56e58c87b817092/image.png" width=350>

# Langkah 2.0: Laman Daftar

## Langkah 2.1: Latihan Ubah Laman Daftar

* Ubah **Laman Daftar** supaya mempunyai maklumat berikut

| item | component | type |
| ------ | ------ | ------ |
| Nama | input | text |
| Emel | input | email |
| Alamat | input | text |
| Daerah | select |  |
| Negeri | input | text |
| Hantar | button | submit |
| Reset | button | reset |

* Di VS Code, buka fail **daftar.vue** di direktori **pages**, padam kod sedia ada, salin dan tampal kod berikut

```vue

```

* Simpan / **Save** fail **daftar.vue**

## Langkah 2.2: Uji Laman Daftar

* Di ***Command Prompt*** taip kod seperti berikut untuk buka aplikasi Nuxt

```
npm run dev
```

* Di browser layari pautan berikut **http://localhost:3000/daftar**, berikut adalah contoh paparan

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/d77249cc699249a765a54a0cb4a54837/image.png" width=400>
