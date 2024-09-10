[[_TOC_]]

# Latihan 10.2: Nuxt UI Framework
Latihan ini adalah untuk menunjukkan penggunaan **Flowbite - a TailwindCSS based UI Framework**. 

Untuk maklumat lanjut boleh layari https://flowbite.com/

Latihan ini adalah sambungan dari latihan [Latihan 10.1: Pengenalan Nuxt 3](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%2010%20-%20Nuxt.js/Latihan%2010.1%20-%20Pengenalan%20Nuxt%203.md)

# Langkah 1.0: Penggunaan Flowbite TailwindCSS UI Framework
Langkah ini adalah untuk menggunakan **Flowbite** sebagai **UI Framework**

## Langkah 1.1: Tetapan TailwindCSS

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

## Langkah 1.2: Tetapan Flowbite

Sila rujuk pautan ini untuk rujukan tetapan [https://flowbite.com/docs/getting-started/nuxt-js/](https://flowbite.com/docs/getting-started/nuxt-js/)

* Di **Command Prompt** atau **Terminal**, taip kod berikut

```bash
npm install flowbite
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
    "@nuxtjs/tailwindcss": "^6.12.1",
    "flowbite": "^2.5.1",
    "nuxt": "^3.13.0",
    "vue": "latest",
    "vue-router": "latest"
  }
}
```

* Buka fail **tailwind.config.ts**, padam kod sedia ada , salin dan tampal kod berikut

```ts
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./node_modules/flowbite/**/*.{js,ts}"
  ],
  theme: {
    extend: {},
  },
  plugins: [
    require('flowbite/plugin')
  ],
}

```
* Simpan / (_**Save**_) fail **tailwind.config.ts**.

* Buka fail **nuxt.config.ts**, padam kod sedia ada , salin dan tampal kod berikut

```ts
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
  modules: ["@nuxtjs/tailwindcss"]
})

```

* Simpan / (_**Save**_) fail **nuxt.config.ts**.

* Di **Command Prompt** atau **Terminal**, taip kod berikut untuk mulakan aplikasi **Nuxt 3**

```bash
npm run dev
```

* Uji dengan layari laman **http://localhost:3000**

* Di browser klik **Shift + Option + D** untuk buka paparan **Devtools**


