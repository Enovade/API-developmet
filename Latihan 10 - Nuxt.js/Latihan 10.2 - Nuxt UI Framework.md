[[_TOC_]]

# Latihan 10.2: Nuxt UI Framework
Latihan ini adalah untuk menunjukkan penggunaan **Flowbite - a TailwindCSS based UI Framework**. 

Untuk maklumat lanjut boleh layari https://flowbite.com/

Latihan ini adalah sambungan dari latihan [Latihan 10.1: Pengenalan Nuxt 3](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%2010%20-%20Nuxt.js/Latihan%2010.1%20-%20Pengenalan%20Nuxt%203.md)

# Langkah 1.0: Penggunaan Flowbite TailwindCSS UI Framework
Langkah ini adalah untuk menggunakan **Flowbite** sebagai **UI Framework**

## Langkah 2.1: Tetapan TailwindCSS

* Di **Command Prompt** atau **Terminal**, taip kod berikut

```bash
npx nuxi module add @nuxtjs/tailwindcss
```
* Buka fail **nuxt.config.ts** pastikan **modules: ['@nuxtjs/tailwindcss']** tersenarai seperti contoh paparan berikut

```typescript
// https://nuxt.com/docs/api/configuration/nuxt-config
export default defineNuxtConfig({
  compatibilityDate: '2024-04-03',
  devtools: { enabled: true },
  modules: ["@nuxtjs/tailwindcss"]
})
```

* Di **Command Prompt** atau **Terminal**, taip kod berikut untuk **initialize tailwindCSS**

```bash
npx tailwindcss init
```

* Jika berjaya, pastikan terdapat fail **tailwind.config.js**, buka fail untuk lihat maklumat seperti contoh berikut

```js
/** @type {import('tailwindcss').Config} */
export default {
  content: [],
  theme: {
    extend: {},
  },
  plugins: [],
}

```

* Di **VSCode**, wujudkan direktori baru **assets/css** dan kemudian wujudkan fail **main.css**

* Salin dan tampal kod berikut

```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

* Simpan / (_**Save**_) fail **main.css**.

* Buka fail **nuxt.config.ts**, padam kod sedia ada, salin dan tampal kod berikut

```ts
// https://nuxt.com/docs/api/configuration/nuxt-config
export default defineNuxtConfig({
  compatibilityDate: '2024-04-03',
  devtools: { enabled: true },
  css: ['~/assets/css/main.css'],
  modules: ['@nuxtjs/tailwindcss']
})
```
* Simpan / (_**Save**_) fail **nuxt.config.ts**.

* Di **Command Prompt** atau **Terminal**, taip kod berikut untuk mulakan aplikasi **Nuxt 3**

```bash
npm run dev
```

* Uji dengan layari laman **http://localhost:3000**

## Langkah 2.2: Tetapan Flowbite

Sila rujuk pautan ini untuk rujukan tetapan [https://flowbite.com/docs/getting-started/nuxt-js/](https://flowbite.com/docs/getting-started/nuxt-js/)

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

<img src="https://code.cloud-connect.asia/msp/akademi-cloud-connect/training-modules/pembangunan-aplikasi-moden/uploads/c6ec5b2a755b211b80cc090196fe5c5e/image.png" width=550>

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
