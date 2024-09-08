[[_TOC_]]

# Latihan 5: API
Latihan ini adalah untuk menunjukkan pemahaman membangunkan API menggunakan **_ExpressJS Framework_**

# Langkah 1.0: _Install Visual Studio Code Extension_
Langkah ini adalah untuk _install Express Framework_ dan _REST Client extensions_ untuk memudahkan pembangunan API

* Di Visual Studio Code, dari senarai ikon di kiri, klik _**Extension**_

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/25165bc1d1cd649f14bd96da890e1a44/image.png">

* Buat carian, _**ExpressJs 4 Snippets**_

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/49c4c53a495b34b47a44ac5711b43a7c/image.png">

* Klik Install

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/2713f45d6fa38c7c0f584517cb8182db/image.png">

* Buat carian sekali lagi, _**REST Client**_

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/4cb7cc8ec03a94979224becd8fa550ef/image.png">

* Klik Install

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/c83e430e1249301217ec6e353c49cc9d/image.png">

Note: Untuk menggunakan **REST Client**, pastikan **Code Lens** diaktifkan di **Visual Studio Code -> click Manage icon -> Settings -> Text Editor -> Enable Code Lens**

# Langkah 2.0: Penyediaan Persekitaran Projek

*  Buka aplikasi ***Command Prompt*** untuk Windows atau ***Terminal*** untuk MacOS.

Nota: Untuk Windows, buka aplikasi ***Command Prompt*** dengan menggunakan **Administration mode** seperti paparan berikut:

<img src="https://code.cloud-connect.asia/Hanafiah/pembangunan-aplikasi-moden/uploads/c87c68041ae977df59582ea634de13bd/cmd-prompt.png">

*  Di aplikasi ***Command Prompt*** untuk Windows atau ***Terminal*** untuk MacOS
*  Wujudkan direktori baru - latihan-5 dengan taip kod seperti berikut

```
> mkdir latihan-5
> cd latihan-5
```
* Taip kod berikut untuk membuka aplikasi Visual Studio Code

```
> code .
```

# Langkah 3.0: _**Initialize**_ Persekitaran NodeJS
Langkah ini adalah untuk initialize NodeJS environment sebagai langkah pertama untuk pembangunan API
*  Buka terminal, dari Menu klik _**Terminal -> New Terminal**_ 
*  Di terminal taip kod seperti berikut

```
> npm init
```
* Masukkan maklumat yang di perlukan seperti paparan berikut

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/52ea822daaa484df35b92d95e2386d25/image.png">

* Dari senarai ikon di kiri Visual Studio Code, klik ikon _**Explorer**_ untuk pastikan fail _**package.json**_ wujud dan mempunyai maklumat yang sama seperti yang dimasukkan sebelum ini. Sila rujuk paparan berikut:

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/ac4849231324d633864a5a7897f5be3d/image.png">

# Langkah 4.0: _Install ExpressJS Framework_
Langkah ini adalah untuk _Install ExpressJS Framework_
<br>
Sila layari https://www.npmjs.com/package/express untuk maklumat lanjut

*  Di terminal taip kod seperti berikut

```
> npm install express
```

* Setelah selesai, di fail _**package.json**_, pastikan _**express**_ adalah salah satu _**dependencies**_. Sila rujuk paparan berikut:

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/2bcc6ae4766a61355f76725ef761a2cc/image.png">

# Langkah 5.0: Penggunaan _ExpressJS Framework_
Langkah ini adalah untuk membangunkan API menggunakan ExpressJS Framework
* Wujudkan fail **index.js**. Dari Menu, klik **_File -> New File_**
* Salin dan tampal kod berikut

```
const express = require('express');
const app = express();

app.get('/', (req, res) => {
    res.send('Salam Muafakat!');
});

app.listen(8080, () => {
    console.log('App listening on port 8080!');
});

//Run app, then load http://localhost:8080 in a browser to see the output.
```
* Simpan / (_**Save**_) fail. Sila rujuk paparan berikut:

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/d3ea4578e7d749d9f419feaa7feef73a/image.png">

# Langkah 6.0: Uji Penggunaan ExpressJS Framework

* Di terminal taip kod seperti berikut:

```
> node index.js
```
* Jika berjaya, berikut adalah paparan maklumat di terminal:
```
App listening on port 8080!
```
* Buka internet browser, dan layari **http://localhost:8080** dengan paparan berikut

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/6b34f04a0263af57eaad377c073696ce/image.png" width=400>

* Di terminal, untuk **_stop_** applikasi NodeJS, tekan kekunci **_Ctrl-C_**

# Langkah 7.0: Using HTTP GET / POST & JSON
Langkah ini adalah untuk membangunkan API menggunakan _**HTTP GET / POST & JSON data**_


## Langkah 7.1: Using HTTP GET & JSON
Langkah ini adalah untuk membangunkan API menggunakan _**HTTP GET & JSON data**_

* Wujudkan fail **getjson.js**. Dari Menu, klik **_File -> New File_**
* Salin dan tampal kod berikut

```
const express = require('express');
const app = express();

app.get('/', (req, res) => {
    res.send('Salam Muafakat!');
});

app.get('/johor', (req, res) => {
    res.json({ data: "Salam Muafakat" });
});

app.listen(8080, () => {
    console.log('App listening on port 8080!');
});
```
* Simpan / (_**Save**_) fail. Sila rujuk paparan berikut:

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/f29dd7a41c2ab73394e67d9ee633873d/image.png">
