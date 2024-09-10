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

<img src="https://code.cloud-connect.asia/Hanafiah/mindef-latihan-cloud-native/uploads/c719f036cc48791db05a7a7f24540f4e/image.png" width=550>

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

<img src="https://code.cloud-connect.asia/Hanafiah/mindef-latihan-cloud-native/uploads/3f19f582ab5965ff831cdc9ada363139/image.png" width=550>

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

# Langkah 3.0: Penggunaan Nuxt Icon
Langkah ini adalah untuk menunjukkan pengunaan **Nuxt Icon**. Sila rujuk pautan **Nuxt Icon** [https://nuxt.com/modules/icon](https://nuxt.com/modules/icon)

* Buka fail **index.vue**, padam kod sediada, salin dan tampal kod berikut

```
<script lang="ts" setup></script>

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
    </div>
  </div>
</template>

<style scoped></style>
```
Nota:
```
<Icon name="mdi:square-edit-outline" size="1.5em" />
```
* **mdi** adalah merujuk kepada **Material Design Icons** [https://icon-sets.iconify.design/mdi/](https://icon-sets.iconify.design/mdi/) dan [https://icon-sets.iconify.design/mdi/square-edit-outline/](https://icon-sets.iconify.design/mdi/square-edit-outline/)

* Simpan / **Save** fail **index.vue**

* Di ***Command Prompt*** taip kod seperti berikut untuk buka aplikasi Nuxt

```
npm run dev
```

* Di browser layari pautan berikut **http://localhost:3000/** seperti contoh paparan berikut

<img src="/uploads/32f0ae5a1c744f4502e689a23c46c6d0/image.png" width=550>
