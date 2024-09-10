[[_TOC_]]

# Latihan 9: Vue 3 Framework
Latihan ini adalah untuk menunjukkan pemahaman membangunkan aplikasi web atau website menggunakan **Vuejs Framework version 3**. 

# Langkah 1.0: Penyediaan Persekitaran Projek
*  Di aplikasi ***Command Prompt*** untuk Windows atau ***Terminal*** untuk MacOS
*  Wujudkan direktori baru - **latihan-9**

```
> mkdir latihan-9
> cd latihan-9
```

* Taip kod berikut untuk membuka aplikasi Visual Studio Code

```
> code .
```

# Langkah 2.0: _Install Visual Studio Code Extension_
Langkah ini adalah untuk _**install Vue VSCode Snippets extension**_ untuk memudahkan pembangunan aplikasi Vue

* Di Visual Studio Code, dari senarai ikon di kiri, klik _**Extension**_

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/25165bc1d1cd649f14bd96da890e1a44/image.png">

* Buat carian, _**Vue 3 Snippets**_ dan **Vue Official**

<img src="https://code.cloud-connect.asia/msp/akademi-cloud-connect/training-modules/pembangunan-aplikasi-moden/uploads/476dae065373eec8ea155f56635ae83d/image.png" width=250>

* Klik Install

<img src="https://code.cloud-connect.asia/msp/akademi-cloud-connect/training-modules/pembangunan-aplikasi-moden/uploads/8f169e56102cc03c7edb1142621f3d2e/image.png" width=700>

<img src="/uploads/471c350d12922583192c27cffd431223/image.png" width=700>

# Langkah 3.0: Vue 3

## Langkah 3.1: _**Install**_ Vue CLI
Langkah ini adalah untuk _install Vue CLI (Command Line Interface)_ sebagai langkah pertama untuk pembangunan aplikasi menggunakan Vuejs

*  Di ***Command Prompt*** atau **Visual Studio Code terminal** taip kod seperti berikut

```
> npm create vue@latest
```

* Untuk soalan **Ok to proceed? (y)**, taip **y**
* Untuk soalan **Project name:**, taip **vueapp**
* Untuk soalan **Add TypeScript**, pilih **No**
* Untuk soalan **Add JSX Support**, pilih **No**
> Pastikan pilih **Yes** untuk **Add Vue Router for Single Page Application development?**
* Untuk soalan **Add Vue Router for Single Page Application development?**, pilih **Yes**
* Untuk soalan **Add Pinia for state management?**, pilih **No**
* Untuk soalan **Add Vitest for Unit Testing?**, pilih **No**
* Untuk soalan **Add an End-to-End Testing Solution?**, pilih **No**
* Untuk soalan **Add ESLint for code quality?**, pilih **No**
* Untuk soalan **Add Vue DevTools 7 extension for debugging? (experimental)**, pilih **No**
* Berikut adalah contoh paparan jika berjaya



```
hanafiah > npm create vue@latest
Need to install the following packages:
create-vue@3.10.4
Ok to proceed? (y) y

Vue.js - The Progressive JavaScript Framework

✔ Project name: … vue-app
✔ Add TypeScript? … No / Yes
✔ Add JSX Support? … No / Yes
✔ Add Vue Router for Single Page Application development? … No / Yes
✔ Add Pinia for state management? … No / Yes
✔ Add Vitest for Unit Testing? … No / Yes
✔ Add an End-to-End Testing Solution? › No
✔ Add ESLint for code quality? … No / Yes
✔ Add Vue DevTools 7 extension for debugging? (experimental) … No / Yes

Scaffolding project in /Users/hanafiah/Documents/workshop/ICT@Johor/latihan-10/vueapp...

Done. Now run:

  cd vueapp
  npm install
  npm run dev
```
* Taip kod berikut untuk **run** aplikasi

```
cd vueapp
npm install
npm run dev
```

* Akses ke aplikasi menggunakan browser - **http://localhost:xxxx**

* Berikut adalah paparan jika berjaya

<img src="https://code.cloud-connect.asia/msp/akademi-cloud-connect/training-modules/pembangunan-aplikasi-moden/uploads/11baf17b2f53f9e7367031088a3b3a55/image.png" width=700>

* Di aplikasi **Command Prompt**, taip **CTRL-C** untuk hentikan aplikasi.


## Langkah 3.2: Ubah aplikasi Vue.js
Langkah ini adalah untuk memahami Vue.js components

* Di aplikasi **Command Prompt**, taip kod berikut untuk buka aplikasi **Visual Studio Code**

```
code .
```
* Berikut adalah contoh paparan jika berjaya

<img src="https://code.cloud-connect.asia/msp/akademi-cloud-connect/training-modules/pembangunan-aplikasi-moden/uploads/f4ac179799283f14cea91c345f9c71c9/image.png" width=300>

* Buka fail **App.vue** di direktori **src**, tukar maklumat di garis **11** dari

`<HelloWorld msg="You did it!" />`

kepada berikut

`<HelloWorld msg="Salam Bangsa Johor!" />`

seperti contoh paparan berikut

<img src="https://code.cloud-connect.asia/msp/akademi-cloud-connect/training-modules/pembangunan-aplikasi-moden/uploads/d3209c57e5398ed28f028575a1bb2740/image.png" width=700>

* **Save** / Simpan fail **App.vue**

## Langkah 3.3: Uji Aplikasi web

* Di aplikasi **Command Prompt**, taip kod berikut untuk mulakan aplikasi

```
npm run dev
```

* Akses ke aplikasi menggunakan browser - **http://localhost:xxxx**

* Berikut adalah paparan jika berjaya

<img src="https://code.cloud-connect.asia/msp/akademi-cloud-connect/training-modules/pembangunan-aplikasi-moden/uploads/5db8ec486fc2d2a1ebe41202785f67c7/image.png" width=700>

* Di aplikasi **Command Prompt**, taip **CTRL-C** untuk hentikan aplikasi.



