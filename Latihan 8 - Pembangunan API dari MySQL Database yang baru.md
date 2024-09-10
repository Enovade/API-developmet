[[_TOC_]]

# Latihan 8: Pembangunan API dari MySQL Database yang baru
Latihan ini adalah untuk menunjukkan pemahaman membangunkan MySQL API dari MySQL Database yang baru menggunakan **_PRISMA ORM and Fastify Framework_**. Untuk latihan ini MySQL database server akan disediakan di persekitaran pengkomputeran awan. 

**Nota:**
Jika hendak menyediakan persekitaran MySQL database untuk di komputer anda, sila rukjuk pautan berikut untuk maklumat lebih lanjut: https://dev.mysql.com/doc/mysql-installation-excerpt/8.0/en/windows-installation.html

Sila layari https://www.prisma.io/ untuk maklumat lanjut 

Latihan ini adalah sambungan dari latihan [Latihan 7: Pembangunan API dari MySQL Database sediada](https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/-/blob/master/Latihan%207%20-%20Pembangunan%20API%20dari%20MySQL%20Database%20sediada.md)


# Langkah 1.0: _Connecting to new MySQL Database using Prisma_
Langkah ini adalah untuk membuat _connection_ ke MSQL database

* Buka fail **.env**, tukar maklumat **DATABASE_URL** dengan salin dan tampal kod seperti berikut

```
DATABASE_URL="mysql://pentadbir:rahsia@167.71.217.175:3306/userX"
```

> Penting: Sila gunakan nama database yang telah diberikan cth: user1 / user2 / user3 ...**


```
Nota:
- pentadbir : adalah username untuk akses ke MySQL database
- rahsia : adalah katalaulan untuk username root
- 167.71.217.175 : adalah database server URL atau IP address localhost / 127.0.0.1 jika dari komputer sendiri
- 3306 : adalah port untuk MySQL server
- userX : adalah nama database
```

* Simpan / (Save) fail **.env**

* Buka fail **schema.prisma** di direktori **prisma**, pastikan maklumat **datasource db** seperti kod berikut

```
datasource db {
  provider = "mysql"
  url      = env("DATABASE_URL")
}
```

# Langkah 2.0: Penggunaan _Prisma Migrate_
Langkah ini adalah untuk menggunakan **Prisma Migrate** untuk wujudkan **table** di database

* Di terminal di Visual Studio Code, taip kod seperti berikut

```
npx prisma migrate dev
```
* Masukkan **first migrate** bila ditanya **Enter a name for the new migration:**
* Setelah selesai, sila rujuk paparan berikut dan maklumat yang dipaparkan mungkin berbeza di komputer masing-masing

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/49899e96e6c90a16c3a270e8cccd9eed/image.png" width=600>

* Pastikan direktori **migrations** di wujudkan di bawah direktori **prisma** seperti paparan berikut. Maklumat yang dipaparkan mungkin berbeza di komputer masing-masing

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/c1dceff899ef8af3b5b7a8b96b8c6360/image.png" width=300>

* Sila lihat kandungan fail **migration.sql**

# Langkah 3.0: Penggunaan _Prisma Studio_
Langkah ini adalah untuk menggunakan **Prisma Studio** untuk akses MySQL database

* Buka aplikasi Command Prompt untuk Windows atau Terminal untuk MacOS dan pastikan berada di direktori projek **latihan-7**, taip kod seperti berikut

```
npx prisma studio
```
atau

```
npx prisma studio --browser none
```

* Jika berjaya, sila rujuk paparan berikut:

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/54e585920ebc15dd7a30e47066a5b599/image.png" width=600>

* Secara automatik juga, **internet browser** dengan URL http://localhost:5555/ akan dibuka seperti paparan berikut

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/7da9841ad5d0d1ee6485ed03b314bbad/image.png" width=300>

* Untuk melihat data di database. Klik **pengguna** di senarai **All Models**, sila rujuk paparan berikut

<img src="https://gitlab.com/akademi-cloud-connect/johor-ict/latihan-pembangunan-aplikasi-moden/uploads/3c1c040068d585988945c93aec055d25/image.png" width=600>


# Langkah 4.0: Uji _Create, Read, Update and Delete_ API

* Buka fail **uji.http**, dan buat ujian dan pastikan semua fungsi berjalan lancar.

