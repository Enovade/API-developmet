[[_TOC_]]

# Latihan 10.5: _**Nuxt Components**_
Latihan ini adalah untuk menunjukkan pemahaman **Nuxt Components**. Pembangunan **component header** yang akan menggunakan **Navigation Bar** yang diwujudkan dari latihan sebelum ini.

Latihan ini adalah sambungan dari latihan [Latihan 10.4: Nuxt Layouts](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%2010%20-%20Nuxt.js/Latihan%2010.4%20-%20Nuxt%20Layouts.md)

Sila rujuk pautan ini untuk **Vue Components** [https://vuejs.org/guide/essentials/component-basics.html) 
<br>
Sila rujuk pautan ini untuk **Nuxt Components** [https://nuxt.com/docs/guide/directory-structure/components) 

# Langkah 1.0: Wujudkan _**Nuxt Components**_

* Di aplikasi ***Command Prompt***, taip kod berikut untuk wujudkan **Nuxt Components**

```
npx nuxi add component header
```

* **header** adalah nama fail - **header.vue**

* Di VS Code, pastikan terdapat fail **header.vue** diwujudkan di dalam direktori **components**

* Buka fail **header.vue** yang baru diwujudkan, seperti contoh paparan berikut

<img src="/uploads/fd04fdac0759c8c7533ceca968aab2b6/image.png" width=550>

# Langkah 2.0: Penggunaan _**Nuxt Components**_

* Di fail **header.vue**, padam kod sedia ada, salin dan tampal kod berikut

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

* Simpan / **Save** fail **header.vue**

* Buka fail **default.vue** di direktori **layouts**, padam kod sedia ada, salin dan tampal kod berikut

```
<script setup lang="ts"></script>

<template>
  <div>
    <Header />
    <slot />
  </div>
</template>

<style scoped>
a { text-decoration: none; }
</style>
```

* Simpan / **Save** fail **default.vue**

# Langkah 3.0: Uji _**Nuxt Components**_

* * Di ***Command Prompt*** taip kod seperti berikut untuk buka aplikasi Nuxt

```
npm run dev -- -o
```

* Di browser layari pautan berikut **http://localhost:3000/**, pastikan **Navigation Bar** berfungsi seperti contoh paparan berikut

<img src="/uploads/6d1c6a5294d81c3e92480d5e1073b22c/image.png" width=550>
