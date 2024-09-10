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

<img src="https://code.cloud-connect.asia/Hanafiah/mindef-latihan-cloud-native/uploads/46169695f1c5b0757bf61e037eb781ba/image.png" width=550>

* Pastikan juga di pautan **http://localhost:3000/daftar** dan **http://localhost:3000/pengguna** terdapat **Layout: default** di paparan.

## Langkah 2.2: Konfigurasi untuk tiada **layouts**

* Buka fail **login.vue** di direktori **pages**, padam maklumat sedia ada, salin dan tampal kod berikut

```
<script lang="ts" setup>
definePageMeta({
  layout: false,
});
</script>

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
* Simpan / **Save** fail **app.vue**

* Di browser layari pautan berikut **http://localhost:3000/login**. Pastikan tidak terdapat **Layout: default** di paparan

* Berikut adalah contoh paparan jika berjaya

<img src="https://code.cloud-connect.asia/Hanafiah/mindef-latihan-cloud-native/uploads/b0c5ba2ebf258c9f0466df777405bbae/image.png" width=550>

# Langkah 3.0: **Navigation Bar Layouts**

Sila rujuk pautan ini untuk **Navigation Bar Components** [https://bootstrap-vue-next.github.io/bootstrap-vue-next/docs/components/navbar.html](https://bootstrap-vue-next.github.io/bootstrap-vue-next/docs/components/navbar.html) 

* Buka fail **default.vue** di direktori **layouts**, padam maklumat sedia ada, salin dan tampal kod berikut

```
<script setup lang="ts"></script>

<template>
  <div>
    <BNavbar toggleable="sm" variant="primary" v-b-color-mode="'dark'">
      <BNavbarToggle target="nav-text-collapse" />
      <BNavbarBrand><Icon name="mdi:graph-box-outline" ></Icon></BNavbarBrand>
      <BCollapse id="nav-text-collapse" is-nav>
        <BNavbarNav>
          <BNavItem>
            <NuxtLink to="/">
              <a>Utama</a>
            </NuxtLink>
          </BNavItem>
          <BNavItem >
            <NuxtLink to="/daftar">
              <a>Daftar</a>
            </NuxtLink>
          </BNavItem>
          <BNavItem >
            <NuxtLink to="/pengguna">
              <a>Pengguna</a>
            </NuxtLink>
          </BNavItem>
          <BNavItem >
            <NuxtLink to="/login">
              <a>Login</a>
            </NuxtLink>
          </BNavItem>
        </BNavbarNav>
      </BCollapse>
    </BNavbar>
    <slot />
  </div>
</template>

<style scoped>
a { text-decoration: none; }
</style>

```

* Simpan / **Save** fail **default.vue**

* Di browser layari pautan berikut **http://localhost:3000/**. Pastikan terdapat **Navigation Bar** di paparan seperti contoh berikut

<img src="/uploads/4f4d63fe826124d42f2073c0c56515e9/image.png" width=700>

* Pastikan juga di pautan **http://localhost:3000/daftar** dan **http://localhost:3000/pengguna** terdapat **Navigation Bar**  di paparan.

* Pastikan di pautan **http://localhost:3000/login** tidak terdapat **Navigation Bar** seperti contoh paparan berikut

<img src="https://code.cloud-connect.asia/Hanafiah/mindef-latihan-cloud-native/uploads/9182ae8973c3da3a629430cff75f59b7/image.png" width=550>

