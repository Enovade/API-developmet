[[_TOC_]]

# Latihan 1: Pengenalan Fastify
Latihan ini adalah untuk menunjukkan pemahaman membangunkan API menggunakan **_Fastify Framework_**

# Langkah 1.0: _Install Visual Studio Code Extension_
Langkah ini adalah untuk **_install Fastify Snippets_** dan **_REST Client extensions_** untuk memudahkan pembangunan API

* Di Visual Studio Code, dari senarai ikon di kiri, klik _**Extension**_

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/25165bc1d1cd649f14bd96da890e1a44/image.png">

* Buat carian, _**Fastify Snippets**_

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/7a0235b8e411376ac1c09e03317889b3/image.png" width=300>

* Klik **_Install_**

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/cafa32f842013545e96aa64928ebb7a9/image.png" width=500>

* Buat carian sekali lagi, _**REST Client**_

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/4cb7cc8ec03a94979224becd8fa550ef/image.png">

* Klik Install

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/c83e430e1249301217ec6e353c49cc9d/image.png" width=500>

Note: Untuk menggunakan **REST Client**, pastikan **Code Lens** diaktifkan di **Visual Studio Code -> click Manage icon -> Settings -> Text Editor -> Enable Code Lens**

# Langkah 2.0: Penyediaan Persekitaran Projek

*  Buka aplikasi ***Command Prompt*** untuk Windows atau ***Terminal*** untuk MacOS.

Nota: Untuk Windows, buka aplikasi ***Command Prompt*** dengan menggunakan **Administration mode** seperti paparan berikut:

<img src="https://code.cloud-connect.asia/Hanafiah/pembangunan-aplikasi-moden/uploads/c87c68041ae977df59582ea634de13bd/cmd-prompt.png">

*  Di aplikasi ***Command Prompt*** untuk Windows atau ***Terminal*** untuk MacOS
*  Wujudkan direktori baru - latihan-5 dengan taip kod seperti berikut

```bash
mkdir latihan-1
cd latihan-1
```
* Taip kod berikut untuk membuka aplikasi Visual Studio Code

```bash
code .
```

# Langkah 3.0: _**Initialize**_ Persekitaran NodeJS
Langkah ini adalah untuk initialize NodeJS environment sebagai langkah pertama untuk pembangunan API
*  Buka terminal, dari Menu klik _**Terminal -> New Terminal**_ 
*  Di terminal taip kod seperti berikut

```
npm init -y
```

* Dari senarai ikon di kiri Visual Studio Code, klik ikon _**Explorer**_ untuk pastikan fail _**package.json**_ wujud dan mempunyai maklumat yang sama seperti yang dimasukkan sebelum ini. Sila rujuk contoh paparan berikut:

```json
{
  "name": "latihan-1",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}

```
* **Enable ECMAScript Modules (ESM)** di dalam projek dengan tambah kod berikut di fail **package.json**

```
"type": "module",
```

* Tambah konfigurasi untuk menggunakan command **NPM RUN** dengan tambah kod berikut di **scripts** di fail **package.json** seperti contoh paparan berikut

```json
{
  "name": "latihan-1",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "node app.js",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "type": "module",
  "keywords": [],
  "author": "",
  "license": "ISC"
}

```

# Langkah 4.0: _Install Fastify Framework_
Langkah ini adalah untuk **_Install Fastify Framework_**
<br>
Sila layari https://fastify.dev/ untuk maklumat lanjut

*  Di terminal taip kod seperti berikut

```bash
npm install fastify
```

atau

```bash
npm i fastify
```

* Setelah selesai, di fail _**package.json**_, pastikan _**fastify**_ adalah salah satu _**dependencies**_. Sila rujuk contoh paparan berikut, versi **fastify** mungkin berbeza:

```json
{
  "name": "latihan-1",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "fastify": "^4.28.1"
  }
}

```

# Langkah 5.0: Penggunaan _Fastify Framework_
Langkah ini adalah untuk membangunkan API menggunakan Fastify Framework
* Wujudkan fail **app.js**. Dari Menu, klik **_File -> New File_**
* Salin dan tampal kod berikut

```javascript
import Fastify from 'fastify'

const app = Fastify({
  logger: true
})
)
app.get('/', async (request, reply) => {
  return { hello: 'world' }
})
app.post('/', async (request, reply) => {
  return request.body
})
app.listen({ port: 8080 })
```
* Simpan / (_**Save**_) fail **app.js**. Sila rujuk paparan berikut:

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/d3ea4578e7d749d9f419feaa7feef73a/image.png">

# Langkah 6.0: Uji Penggunaan ExpressJS Framework

* Di terminal taip kod seperti berikut:

```
node index.js
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
