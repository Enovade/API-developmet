[[_TOC_]]

# Latihan 10.9: _Nuxt Server Routes_

Latihan ini adalah sambungan dari latihan [Latihan 10.8: Environment Variables](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%2010%20-%20Nuxt.js/Latihan%2010.8%20-%20Environment%20Variables.md)


# Langkah 1.0: _Nuxt Server Routes as API endpoints_ 
Langkah ini adalah untuk konfigurasi _**Command Nuxi**_ untuk mewujudkan **API Endpoints** di aplikasi Nuxt


## Langkah 1.1: Penggunaan _Nuxt Server Routes_

* Di **Commmand Prompt** atau **Terminal**, taip kod berikut

```bash
npx nuxi add api salam
```

* Jika berjaya, buka **VSCode**, pastikan contoh paparan seperti berikut di direktori **server**

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/9883b5363e4c2f0032e1c59cb5cabf4f/image.png">

* Buka fail **salam.ts**, padam kod sedia ada, salin dan tampal kod berikut

```
export default defineEventHandler((event) => {
  return {
    salam: "Salam Malaysia Madani!!"
  }
})
```
* Simpan / **Save** fail **salam.ts**

* Di ***Command Prompt*** taip kod seperti berikut untuk buka aplikasi Nuxt

```
npm run dev -- -o
```

* Di browser layari pautan berikut **http://localhost:3000/api/salam**

* Berikut adalah contoh paparan jika berjaya

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/3d6459f7575941717f40ba09061eeb3d/image.png" width=500>

<hr>

* Di ***Command Prompt***, taip **CTRL-C** untuk hentikan aplikasi Nuxt.

## Langkah 1.2: Penggunaan _GET Methods_

* Di **Commmand Prompt** atau **Terminal**, taip kod berikut

```bash
npx nuxi add api salam.get
```

* Jika berjaya, buka **VSCode**, pastikan contoh paparan seperti berikut di direktori **server**

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/564ed353db21a2b93065c910b6a0a4fb/image.png">

* Buka fail **salam.get.ts**, padam kod sedia ada, salin dan tampal kod berikut

```
export default defineEventHandler((event) => {
  return {
    salam: "Salam Warga JDN!!"
  }
})
```
* Simpan / **Save** fail **salam.get.ts**

* Di ***Command Prompt*** taip kod seperti berikut untuk buka aplikasi Nuxt

```
npm run dev
```

* Wujudkan fail **uji.http**, salin dan tampal kod berikut

```
GET http://localhost:3000/api/salam
```

* Simpan / **Save** fail **uji.http**

* Di fail **uji.http** untuk uji aplikasi. Klik **Send Request** untuk **GET http://localhost:3000/api/salam** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal**

* Berikut adalah contoh paparan jika berjaya:

```json
{
  "salam": "Salam Warga JDN!!"
}
```

* Di ***Command Prompt***, taip **CTRL-C** untuk hentikan aplikasi Nuxt.

## Langkah 1.3: Penggunaan _POST Methods_

* Di **Commmand Prompt** atau **Terminal**, taip kod berikut

```bash
npx nuxi add api salam.post
```

* Jika berjaya, buka **VSCode**, pastikan contoh paparan seperti berikut di direktori **server**

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/f77175f96277cd45996bcf946e1aff42/image.png">

* Buka fail **salam.post.ts**, padam kod sedia ada, salin dan tampal kod berikut

```
export default defineEventHandler( async (event) => {
  const body = await readBody(event)
  return {
    salam: "Salam Warga JDN!!",
    post: body
  }
})
```
* Simpan / **Save** fail **salam.post.ts**

* Di ***Command Prompt*** taip kod seperti berikut untuk buka aplikasi Nuxt

```
npm run dev
```

* Buka fail **uji.http**, salin dan tampal kod berikut

```
###
POST http://localhost:3000/api/salam
Content-Type: application/json

{
    "nama": "Hanafiah",
    "emel": "hanafiah@cloud-connect.asia"
}
```

* Simpan / **Save** fail **uji.http**

* Di fail **uji.http** untuk uji aplikasi. Klik **Send Request** untuk **POST http://localhost:3000/api/salam** dan lihat maklumbalas di VSCode dan **Command Prompt** atau **Terminal**

* Berikut adalah contoh paparan jika berjaya:

```json
{
  "salam": "Salam Warga JDN!!",
  "post": {
    "nama": "Hanafiah",
    "emel": "hanafiah@cloud-connect.asia"
  }
}
```

* Di ***Command Prompt***, taip **CTRL-C** untuk hentikan aplikasi Nuxt.
