[[_TOC_]]

# Latihan 2: Nuxt UI Framework
Latihan ini adalah untuk menunjukkan penggunaan **Flowbite - a TailwindCSS based UI Framework**. 

Untuk maklumat lanjut boleh layari https://flowbite.com/

# Langkah 1.0: Penyediaan Persekitaran Projek

*  Di aplikasi ***Command Prompt*** untuk Windows atau ***Terminal*** untuk MacOS
*  Wujudkan direktori baru - **latihan-2** di dalam Projek **Latihan-11**

```
mkdir latihan-2
cd latihan-2
```

* Taip kod seperti berikut untuk wujudkan aplikasi **Nuxt 3**

```
npx nuxi init mynuxt
```

* Untuk soalan **Ok to proceed? (y)**, taip **y**
* Untuk soalan **Which package manager would you like to use?**, pilih **npm**
* Untuk soalan **Initialize git repository?**, pilih **Yes**


- **mynuxt** adalah nama projek aplikasi Nuxt 3

* Berikut adalah contoh paparan jika berjaya

```
✨ Nuxt project has been created with the v3 template. Next steps:
 › cd mynuxt
 › Start development server with npm run dev
```

* Taip kod berikut untuk ke direktori **mynuxt**

```
cd mynuxt
```

* Taip kod berikut untuk buka aplikasi Nuxt 3

```
npm run dev

```
atau

```
npm run dev -- -o
```

* Berikut adalah contoh paparan di browser jika berjaya

<img src="/uploads/87a5b303a6ff8434d3d58390249a5ba6/image.png" width=550>

* Buka aplikasi **Command Prompt** baru. Taip kod berikut unktu buka projek **mynuxt** dengan **VS Code**

```
code .
```
> Instructor to explain Nuxt structure from Visual Studio Code

<img src="/uploads/c36a54c85bea905f4e9d7b65f4bea395/image.png" width=550>

* Di aplikasi **Command Prompt**, taip **CTRL-C** untuk hentikan aplikasi.

# Langkah 2.0: Penggunaan BootstrapVueNext UI Framework
Langkah ini adalah untuk menggunakan **BootstrapVueNext** sebagai **UI Framework** - https://bootstrap-vue-next.github.io/bootstrap-vue-next/

## Langkah 2.1: Tetapan BootstrapVueNext UI Framework

Sila rujuk pautan ini untuk rujukan tetapan [https://bootstrap-vue-next.github.io/bootstrap-vue-next/docs.html#installation-nuxt-js-3](https://bootstrap-vue-next.github.io/bootstrap-vue-next/docs.html#installation-nuxt-js-3)

* Di terminal Visual Studio Code, taip kod seperti berikut untuk **install bootstrap and bootstrap-vue-next**

```bash
> npm i bootstrap bootstrap-vue-next @bootstrap-vue-next/nuxt -D
```

* Pastikan kesemua components yang sudah di**install** tersenarai di fail **package.json** seperti contoh paparan berikut

```json
{
  "name": "nuxt-app",
  "private": true,
  "type": "module",
  "scripts": {
    "build": "nuxt build",
    "dev": "nuxt dev",
    "generate": "nuxt generate",
    "preview": "nuxt preview",
    "postinstall": "nuxt prepare"
  },
  "dependencies": {
    "nuxt": "^3.12.4",
    "vue": "latest"
  },
  "devDependencies": {
    "@bootstrap-vue-next/nuxt": "^0.24.9",
    "bootstrap": "^5.3.3",
    "bootstrap-vue-next": "^0.24.9"
  }
}

```

## Langkah 2.2: Konfigurasi nuxt.config.ts

* Buka fail **nuxt.config.ts**, padamkan semua kod, salin dan tampal kod berikut 

```
// https://nuxt.com/docs/api/configuration/nuxt-config
export default defineNuxtConfig({
  compatibilityDate: '2024-04-03',
  devtools: { enabled: true },
  modules: ['@bootstrap-vue-next/nuxt'],
  css: ['bootstrap/dist/css/bootstrap.min.css'],
})
```

* Simpan / **(Save)** fail **nuxt.config.ts**.

* Taip kod berikut untuk buka aplikasi Nuxt 3

```
npm run dev

```
atau

```
npm run dev -- -o
```

* Berikut adalah contoh paparan di browser jika berjaya

<img src="/uploads/c6ec5b2a755b211b80cc090196fe5c5e/image.png" width=550>

# Langkah 3.0: Tetapan icons

Sila rujuk pautan ini untuk **Nuxt Icon** [https://nuxt.com/modules/icon](https://nuxt.com/modules/icon) 

* Di terminal Visual Studio Code, taip kod seperti berikut untuk **install Nuxt Icons**

```bash
> npx nuxi module add icon
```

* Taip kod berikut untuk **install Material Design Icons** [https://icon-sets.iconify.design/mdi/](https://icon-sets.iconify.design/mdi/)

```bash
> npm i -D @iconify-json/mdi
```



* Pastikan **icon libraries** tersenarai di fail **package.json** seperti contoh paparan berikut

```json
{
  "name": "nuxt-app",
  "private": true,
  "type": "module",
  "scripts": {
    "build": "nuxt build",
    "dev": "nuxt dev",
    "generate": "nuxt generate",
    "preview": "nuxt preview",
    "postinstall": "nuxt prepare"
  },
  "dependencies": {
    "@nuxt/icon": "^1.4.7",
    "nuxt": "^3.12.4",
    "vue": "latest"
  },
  "devDependencies": {
    "@bootstrap-vue-next/nuxt": "^0.24.9",
    "@iconify-json/mdi": "^1.1.68",
    "bootstrap": "^5.3.3",
    "bootstrap-vue-next": "^0.24.9"
  }
}
```
