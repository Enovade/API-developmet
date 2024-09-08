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
* Ubah maklumat **"main": "index.js"** kepada **"main": "app.js"**

* **Enable ECMAScript Modules (ESM)** di dalam projek dengan tambah kod berikut di akhir fail **package.json**

```json
"type": "module"
```

* Berikut adalah contoh paparan jika berjaya:

```json
{
  "name": "latihan-1",
  "version": "1.0.0",
  "description": "",
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "type": "module"
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
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "type": "module",
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

const app = Fastify()

app.get('/', async (request, reply) => {
  return { hello: 'world' }
})

/**
 * Run the server!
 */
const start = async () => {
  try {
    await app.listen({ port: 8080 })
    console.log('Server listening at http://localhost:8080')
  } catch (err) {
    console.log(err)
    process.exit(1)
  }
}
start()
```
* Simpan / (_**Save**_) fail **app.js**.

# Langkah 6.0: Uji Penggunaan Fastify Framework

* Di terminal taip kod seperti berikut:

```
node app.js
```
* Jika berjaya, berikut adalah paparan maklumat di terminal:

```bash
Server listening at http://localhost:8080
```
* Wujudkan fail **uji.http**, salin dan tampal kod berikut

```
GET http://localhost:8080
```
* klik **Send Request** seperti contoh paparan berikut

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/76ed2cf75af8d4e4b51378e38a30f76d/image.png" width=400>

* Berikut adalah paparan jika berjaya

```json
{
  "hello": "world"
}
```

* Simpan / (_**Save**_) fail **uji.http**.

* Di terminal, untuk **_stop_** applikasi NodeJS, tekan kekunci **_Ctrl-C_**

# Penggunaan NPM RUN

Langkah ini adalah untuk membuat konfigurasi NodeJS dengan menggunakan **command * NPM RUN**

* Di fail **package.json**, tukar kod **"script"** dengan salin dan tampal kod seperti berikut

```json
"scripts": {
  "dev": "node app.js"
},
```

* Simpan / (_**Save**_) fail **package.json**.

* Berikut adalah contoh paparan jika berjaya:

```json
{
  "name": "latihan-1",
  "version": "1.0.0",
  "description": "",
  "main": "app.js",
  "scripts": {
    "dev": "node app.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "type": "module",
  "dependencies": {
    "fastify": "^4.28.1"
  }
}
```

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
