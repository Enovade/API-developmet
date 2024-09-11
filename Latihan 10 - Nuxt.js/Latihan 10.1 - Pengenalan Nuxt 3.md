[[_TOC_]]

# Latihan 10.1: Nuxt 3
Latihan ini adalah untuk menunjukkan pemahaman membangunkan aplikasi web atau website menggunakan **Nuxt 3 Framework**. 

# Langkah 1.0: Penyediaan Persekitaran Projek

## Langkah 1.1: _Install Vue.js devtools_
* Di browser, akses ke https://devtools.vuejs.org/ dan klik **Install now**.
* Pilih **Install on Chrome** jika menggunakan **Chrome browser**.
* Klik **Add to Chrome** di laman **Vue.js devtools** dan klik **Add extension**


## Langkah 1.2: Wujudkan Direktori Projek
*  Di aplikasi ***Command Prompt*** untuk Windows atau ***Terminal*** untuk MacOS
*  Wujudkan direktori baru - **latihan-10.1**

```
mkdir latihan-10.1
cd latihan-10.1
```

* Taip kod berikut untuk membuka aplikasi Visual Studio Code

```
code .
```

# Langkah 2.0: _Install Visual Studio Code Extension_
Langkah ini adalah untuk _**install Vue - Official extension**_ untuk memudahkan pembangunan aplikasi Nuxt 3

* Di Visual Studio Code, dari senarai ikon di kiri, klik _**Extension**_
* Buat carian, _**Vue - Official**_ dan klik **Install** seperti contoh paparan berikut

<img src="https://code.cloud-connect.asia/msp/akademi-cloud-connect/training-modules/pembangunan-aplikasi-moden/uploads/ef10b95e95a5615b4cb178b1ce5f6484/image.png" width=450>

# Langkah 3: Wujudkan aplikasi Nuxt 3
Langkah ini adalah untuk wujudkan aplikasi Nuxt 3

* Taip kod seperti berikut untuk wujudkan aplikasi **Nuxt 3**

```
npx nuxi init mynuxtapp
```

* Untuk soalan **Ok to proceed? (y)**, taip **y**
* Untuk soalan **Which package manager would you like to use?**, pilih **npm**
* Untuk soalan **Initialize git repository?**, pilih **Yes**


- **mynuxtapp** adalah nama projek aplikasi Nuxt 3

* Berikut adalah contoh paparan jika berjaya

```
✨ Nuxt project has been created with the v3 template. Next steps:
 › cd mynuxtapp
 › Start development server with npm run dev
```

* Taip kod berikut untuk ke direktori **mynuxtapp*

```
cd mynuxtapp
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

<img src="https://code.cloud-connect.asia/msp/akademi-cloud-connect/training-modules/pembangunan-aplikasi-moden/uploads/87a5b303a6ff8434d3d58390249a5ba6/image.png" width=550>

* Buka aplikasi **Command Prompt** baru, taip kod berikut unktu buka projek **mynuxt** dengan **VS Code**

```
code .
```
> Instructor to explain Nuxt structure from Visual Studio Code

<img src="https://code.cloud-connect.asia/msp/akademi-cloud-connect/training-modules/pembangunan-aplikasi-moden/uploads/c36a54c85bea905f4e9d7b65f4bea395/image.png" width=550>

* Di aplikasi **Command Prompt**, taip **CTRL-C** untuk hentikan aplikasi.
