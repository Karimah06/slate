---
title: Paycoll API Documentation

language_tabs: # must be one of https://git.io/vQNgJ
  - HTTP

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

<!-- includes:
  - errors -->

search: true
---

# Introduction

Payment Collection (Paycoll) adalah .....

This example API documentation page was created with [Slate](https://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Format

Kita menggunakan JSON untuk semua request dan responses.

## Headers

> Headers :

```json
Content-Type: application/json
accesstoken: [access_token]
apikey: [client_secret]
```

Untuk dapat berhasil berkomunikasi dengan Paycoll API, anda harus menyediakan
header berikut di beberapa API request:

Nama | Tipe | Deskipsi
-----| -----| --------
Content-Type | Alphanumeric | Konten dari request body anda. e.g application/json
accesstoken | Alphanumeric | Token Format value
apikey | Alphanumeric | API Key anda

## Response

> Contoh Response :

```json
{
  "status": "success",
  "message": "data found",
  "data": {
    "appsetting":[
      {
        "keyid": "URL",
        "keterangan": "url website",
        "value": "https:\/\/www.tokoonderdilmurah.com\/"
      }
    ]   
  }
}
```

Untuk format response kita menggunakan format JSEND

Nama | Deskipsi
-----| --------
status | Ada 4 tipe status pada response `success,fail,error` .
data | Data adalah output dari request anda.
message | message akan menampilkan status `fail` dan `error` .
request | Parameter request akan return jika status `fail` .

# Error References



# General

Terdiri dari beberapa endpoint yang dapat digunakan oleh semua tipe user (Toko, maupun Collector)

## GENERAL :: UPDATE PASSWORD

Endpoint ini digunakan oleh user untuk mengupdate password. Request anda harus berisi informasi berikut

### HTTP Request

`POST http://paycoll.javasign.id/api/toko/password/update`

> Request

```json
POST http://paycoll.javasign.id/api/login HTTP/1.1
Host: paycoll.javasign.id
Content-Type: application/json
accesstoken: [access_token]




{
  "password_lama": "Admin123",
  "password_baru": "Admin1234"
}
```

### Request

Nama      | Tipe Data | Required | Deskripsi
--------- | --------- | -------- | ---------
passwordlama | string | Y | Password lama user
passwordbaru | string | Y | Password baru user

> Response

```json
{
  "status": "success",
  "message": "password has been updated",
  "data": {
    "userinfo": {
      "id": 2,
      "username": "C-09106",
      "password": "eyJpdiI6Ikt1NnUxN3pNbEdBUFQ5Y1wvUHJOdVlBPT0iLCJ2YWx1ZSI6IjJCZVNPVUVCTWhWRG5ia1h4azZ1SUE9PSIsIm1hYyI6IjM3MGRkZTY1ZGYyYjZmOGZmZTFkYTcxZmZlZTBhZWE0ZjNiZWE4NzUyNGE4MWNiMDU5MDlkZWVkY2M2NjdlMDkifQ==",
      "typeuser": "collector",
      "api_token": "aAU7XGzxjaZxYMwSD5HfeKRBX0otzV42yc9JcJmiXxa22UY4CdxRIj000308",
      "status": true,
      "remember_token": null,
      "userid": 1111,
      "createdby": "SYSTEM",
      "createdon": "2017-08-30 14:23:25",
      "lastupdatedby": "SYSTEM",
      "updated_at": "2017-09-19 08:30:53"
    }
  }
}
```

### Response

Nama      | Tipe Data | Deskripsi
--------- | --------- | ---------
id | integer | Id user
username | string | username untuk user
password | string | Password untuk user
typeuser | string | Tipe user, apakah toko atau collector
api_token| string | Encrypted text dari user yang dijadikan identifikasi saat request
status | boolean | Status user ketika login, jika benar maka true, jika tidak maka false
remember_token | string | Untuk fitur remember login
userid | integer | Jika login sebagai toko maka id toko, jika login sebagai collector maka id collector
createdby | string | Yang membuat user
createdon | datetime | Tanggal dan waktu ketika user dibuat
lastupdateby | string | Yang terakhir mengupdate updated_at datetime Tanggal dan waktu ketika user diupdate
updated_at | datetime | Tanggal dan waktu ketika user diupdate

## GENERAL :: APP SETTING

Endpoint ini memberikan informasi tentang aplikasi Paycoll.

### HTTP Request

`POST http://paycoll.javasign.id/api/app-setting`

> Request

```json
POST http://paycoll.javasign.id/api/login HTTP/1.1
Host: paycoll.javasign.id
Content-Type: application/json
accesstoken: [access_token]
```

### Request

Tidak ada parameter yang dibutuhkan. Hanya request header.

> Response

```json
{
  "status": "success",
  "message": "data found",
  "data": {
    "appsetting":[
      {
        "keyid": "URL",
        "keterangan": "url website",
        "value": "https:\/\/www.tokoonderdilmurah.com\/"
      }
    ]   
  }
}
```

### Response

Nama      | Tipe Data | Deskripsi
--------- | --------- | ---------
**appsetting** | |
keyid | string | Key id
keterangan | string | Keterangan
value | url | Value

# Toko

Client dari perusahaan sparepart kendaraan bermotor yang menggunakan API Paycoll.

## TOKO :: LOGIN

Endpoint ini digunakan oleh user untuk login, dan ketika return client akan mendapatkan `api_token` . Request anda harus berisi informasi berikut

### HTTP Request

`POST http://paycoll.javasign.id/api/login`

> Request

```json
POST http://paycoll.javasign.id/api/login HTTP/1.1
Host: paycoll.javasign.id
Content-Type: application/json
apikey: [client_secret]




{
  "username": "andreastesting",
  "password": "Admin123"
}
```

### Request

Nama      | Tipe Data | Required | Deskripsi
--------- | --------- | -------- | ---------
username | string | Y | username untuk user
password | string | Y | password untuk user

> Response

```json
{
  "status": "success",
  "message": "user found",
  "data": {
    "userinfo": {
      "id": 3,
      "username": "andreastesting",
      "password": "eyJpdiI6IkJTc2o3dkhqaXpkb0F6TVc3YkRWUWc9PSIsInZhbHVlIjoibjhDUUwrSjVEcUpWckluNmdDM2dcL0E9PSIsIm1hYyI6ImVhMjk1YmQ0MTIxOTkzNTAxM2RiY2JlNzZjNGQ1YzcyNTEwNDcxOWFlYThlZWFhMzA1YWJjODdiNGE4MWY5ZTcifQ==",
      "typeuser": "toko",
      "api_token": "aAU7XGzxjaZxYMwSD5HfeKRBX0otzV42yc9JcJmiXxa22UY4CdxRIj000301",
      "status": true,
      "remember_token": null,
      "userid": 20970,
      "createdby": "SYSTEM",
      "createdon": "2017-08-30 14:23:25",
      "lastupdatedby": "SYSTEM",
      "updated_at": "2017-10-05 08:27:41",
      "namatoko": "PINJAMAN",
      "alamat": "JL. KAYU PUTIH TENGAH 1B NO.3",
      "propinsi": "DKI Jakarta",
      "kota": "JAKARTA TIMUR",
      "kecamatan": "KAYU PUTIH",
      "telp": "4899161",
      "tipebisnis": "PARTAI"
    }
  }
}
```

### Response

Nama      | Tipe Data | Deskripsi
--------- | --------- | ---------
id | integer | Id user
username | string | username untuk user
password | string | Password untuk user
typeuser | string | Tipe user, apakah toko atau collector
api_token| string | Encrypted text dari user yang dijadikan identifikasi saat request
status | boolean | Status user ketika login, jika benar maka true, jika tidak maka false
remember_token | string | Untuk fitur remember login
userid | integer | Jika login sebagai toko maka id toko, jika login sebagai collector maka id collector
createdby | string | Yang membuat user
createdon | datetime | Tanggal dan waktu ketika user dibuat
lastupdateby | string | Yang terakhir mengupdate updated_at datetime Tanggal dan waktu ketika user diupdate
namatoko | string | Nama toko user
alamat | string | Alamat user
propinsi | string | Propinsi user
kota | string | Kota user
kecamatan | string | Kecamatan user
telp | string | Nomor telepon user
tipebisnis | string | Tipe bisnis user

## TOKO :: DETAIL TOKO

Endpoint ini menampilkan semua info data detail toko. Request anda harus berisi informasi berikut

### HTTP Request

`POST http://paycoll.javasign.id/api/login`

> Request

```json
POST http://paycoll.javasign.id/api/login HTTP/1.1
Host: paycoll.javasign.id
Content-Type: application/json
accesstoken: [access_token]
```

### Request

Tidak ada parameter yang dibutuhkan. Hanya request header.

> Response

```json
{
  "status": "success",
  "message": "user found",
  "data": {
    "detail": {
      "id": 20886,
      "tokoidwarisan": "9902348",
      "tokoidwarisanlama": "9902348",
      "kodetoko": "C112014101416:30:47",
      "namatoko": "BUANA ABADI MOTOR",
      "alamat": "JL.RAYA PARDASUKA PRINGSEWU KERBANG PARDASUKA KODE POS 36382",
      "propinsi": "LAMPUNG",
      "kota": "PRINGSEWU",
      "kecamatan": "PRINGSEWU",
      "customwilayah": "DA-0614",
      "telp": "07297014195",
      "fax": "",
      "penanggungjawab": "KO ALUN(ALUNDRA WIJA",
      "tgldob": "2015-02-20",
      "catatan": "",
      "statusaktif": false,
      "pemilik": "KO ALUN(ALUNDRA WIJAYA)",
      "gender": "L",
      "tempatlahir": "",
      "tgllahir": "2012-10-12",
      "email": "",
      "norekening": "",
      "namabank": "",
      "nonpwp": "",
      "tipebisnis": "PARTAI",
      "isarowid": "a4fe07af-a8e8-447d-bf53-2762054291d4",
      "createdby": "wisermigration",
      "createdon": "2017-09-02 08:47:26.645551+07",
      "lastupdatedby": "Plafon_UpdateJS",
      "lastupdatedon": "2017-03-01 11:36:52.647+07",
      "Tgltambahanplafonexpired": null,
      "hp": "08154036179\/081379632186"
    }
  }
}
```

### Response

Nama      | Tipe Data | Deskripsi
--------- | --------- | ---------
id | integer | Id user
tokoidwarisan | string | Id toko warisan
tokoidwarisanlama | string | Id toko warisan lama
kodetoko | string | Kode toko
namatoko | string | Nama toko
alamat | string | Alamat toko
propinsi | string | Propinsi toko
kota | string | Kota toko
kecamatan | string | Kecamatan toko
customwilayah | string | Wilayah toko
telp | string | Nomor telepon toko
fax | string | Nomor fax toko
penanggungjawab | string | Nama penganggung jawab toko
tgldob | date | Tanggal berdirinya toko
catatan | string | Catatan toko
statusaktif | boolean | Status aktif atau tidaknya toko, jika aktif akan bernilai true, jika tidak akan bernilai false.
pemilik | string | Pemilik toko
gender | string | Gender pemilik toko
tempatlahir | string | Tempat lahir pemilik toko
tgllahir | date | Tanggal lahir pemilik toko
email | string | Email pemilik toko
norekening | string | Nomor rekening pemilik toko
namabank | string | Nama bank pamilik toko
nonpwp | string | Nomor npwp pemilik toko
tipebisnis | string | Tipe bisnis
isarowid | string | Dihasilkan secara otomatis pada saat penginputan id.
createdby | string | Yang membuat detail toko
createdon | datetime | Tanggal dan waktu ketika membuat detail toko
lastupdateby | string | Yang terakhir mengupdate detail toko
lastupdateon | datetime | Tanggal dan waktu terakhir detail toko diupdate
Tgltambahanplafonexpired | date | Tanggal tambahan plafon kedaluwarsa
hp | string | Nomor hp pemilik toko

## TOKO :: SUMMARY PIUTANG

Endpoint ini menampilkan semua info data piutang dan tagihan.

### HTTP Request

`GET http://paycoll.javasign.id/api/piutang`

> Request

```json
GET http://paycoll.javasign.id/api/piutang HTTP/1.1
Host: paycoll.javasign.id
Content-Type: application/json
accesstoken: [access_token]
```

### Request

Tidak ada parameter yang dibutuhkan. Hanya request header.

> Response

```json
{
  "status": "success",
  "message": "data piutang",
  "data": {
    "saldoTotalPiutang": 0,
    "jatuhTempo": 0,
    "blmJatuhTempo": 0,
    "tanggalBayarTerakhir": "2017-06-06",
    "nota": [
      {
        "nonota": "IKO1180",
        "nomnota": 3465000,
        "tgljt": "2015-05-01",
        "saldoPtg": 0
      },
      {
        "nonota": "IKO0125",
        "nomnota": 13300000,
        "tgljt": "2015-04-06",
        "saldoPtg": 0
      }
    ],
    "bayar": [
      {
        "tgltrans": "2017-06-06",
        "nomtrans": 6889600,
        "kodetrans": "TRN"
      },
      {
        "tgltrans": "2017-06-06",
        "nomtrans": 5288320,
        "kodetrans": "TRN"
      }
    ]
  }
}
```

### Response

Nama      | Tipe Data | Deskripsi
--------- | --------- | ---------
saldoTotalPiutang | integer | Total saldo piutang user
jatuhTempo | integer | username untuk user
blmJatuhTempo | integer | Password untuk user
tanggalBayarTerakhir | date | Tanggal bayar terakhir piutang user
**nota** |  | 
nonota | string | Nomor nota
nomnota | string | Nominal nota
tgljt | date | Tanggal jatuh tempo
saldoPtg | integer | Saldo piutang
**bayar** |  | 
tgltrans | date | Tanggal transfer
nomtrans | integer | Nominal transfer
kodetrans | string | Kode transfer

## TOKO :: REQUEST DIKUNJUNGI

Endpoint ini memberikan informasi tentang toko yang mengirimkan request untuk dikunjungi. Request anda harus berisi informasi berikut

### HTTP Request

`POST http://paycoll.javasign.id/api/request/create`

> Request

```json
GET http://paycoll.javasign.id/api/piutang HTTP/1.1
Host: paycoll.javasign.id
Content-Type: application/json
accesstoken: [access_token]




{
  "keterangan": "aku mau bayar nih 2"
}
```

### Request

Nama      | Tipe Data | Required | Deskripsi
--------- | --------- | -------- | ---------
keterangan | string | Y | Keterangan dari user ketika meminta dikunjungi

> Response

```json
{
  "status": "success",
  "message": "request has been saved",
  "data": {
    "tokoid": 20886,
    "createdby": "andreastesting",
    "tglrequest": "2017-09-28",
    "keterangan": "aku mau bayar nih 2",
    "updated_at": "2017-09-28 09:16:55",
    "created_at": "2017-09-28 09:16:55",
    "id": 13
  }
}
```

### Response

Nama      | Tipe Data | Deskripsi
--------- | --------- | ---------
tokoid | integer | Id toko
tglrequest | date | Tanggal ketika mengirim request untuk dikunjungi
keterangan | string | Keterangan ketika mengirim request untuk dikunjungi
updated_at | datetime | Tanggal dan waktu ketika mengupdate request untuk dikunjungi
created_at | datetime | Tanggal dan waktu ketika membuat request untuk dikunjungi
id | integer | Id user

## TOKO :: REQUEST DIKUNJUNGI LIST

Endpoint ini menampilkan semua info data yang mengirim permintaan untuk dikunjungi.

### HTTP Request

`GET http://paycoll.javasign.id/api/request/list`

> Request

```json
GET http://paycoll.javasign.id/api/piutang HTTP/1.1
Host: paycoll.javasign.id
Content-Type: application/json
accesstoken: [access_token]
```

### Request

Tidak ada parameter yang dibutuhkan. Hanya request header.

> Response

```json
{
  "status": "success",
  "message": "data request",
  "data": {
    "request": [
      {
        "id": 9,
        "tokoid": 20886,
        "tglrequest": "2017-09-28",
        "keterangan": "aku mau bayar lho",
        "createdby": "andreastesting",
        "created_at": "2017-09-28 06:24:50",
        "updated_at": "2017-09-28 06:24:50"
      },
      {
        "id": 10,
        "tokoid": 20886,
        "tglrequest": "2017-09-28",
        "keterangan": "oooo",
        "createdby": "andreastesting",
        "created_at": "2017-09-28 08:11:32",
        "updated_at": "2017-09-28 08:11:32"
      }
    ]
  }
}
```

### Response

Nama      | Tipe Data | Deskripsi
--------- | --------- | ---------
id | integer | Id user
tokoid | integer | Id toko
tglrequest | date | Tanggal ketika mengirim request untuk dikunjungi
keterangan | string | Keterangan ketika mengirim request untuk dikunjungi
createdby | string | Yang membuat request
created_at | datetime | Tanggal dan waktu ketika membuat request untuk dikunjungi
updated_at | datetime | Tanggal dan waktu ketika mengupdate request untuk dikunjungi

## TOKO :: LIST BANK

Endpoint ini menampilkan semua list bank. Request anda harus berisi informasi berikut

### HTTP Request

`GET http://paycoll.javasign.id/api/bank`

> Request

```json
GET http://paycoll.javasign.id/api/piutang HTTP/1.1
Host: paycoll.javasign.id
Content-Type: application/json
accesstoken: [access_token]
```

### Request

Tidak ada parameter yang dibutuhkan. Hanya request header.

> Response

```json
{
  "status": "success",
  "message": "data found",
  "data": [
    {
      "id": 915,
      "namabankdankota": "MANDIRI BEKASI"
    },
    {
      "id": 916,
      "namabankdankota": "LIPPO GARUT"
    },
    {
      "id": 917,
      "namabankdankota": "BII CIKARANG"
    },
    {
      "id": 918,
      "namabankdankota": "BCA SURABAYA"
    },
    {
      "id": 919,
      "namabankdankota": "DANAMON SINGKAWANG"
    },
    {
      "id": 920,
      "namabankdankota": "BCA PEKAN BARU"
    }
  ]
}
```

### Response

Nama      | Tipe Data | Deskripsi
--------- | --------- | ---------
id | integer | Id bank
namabankdankota | string | Nama bank dan kota dari bank tersebut

# Collector

Perantara antara perusahaan yang menjual sparepart kendaraan bermotor dengan toko.

## COLLECTOR :: LOGIN

Layanan ini digunakan oleh user untuk login, dan ketika return client akan mendapatkan `api_token`. Request anda harus berisi informasi berikut

### HTTP Request

`POST http://paycoll.javasign.id/api/login`

> Request

```json
POST http://paycoll.javasign.id/api/login HTTP/1.1
Host: paycoll.javasign.id
Content-Type: application/json
apikey: [client_secret]




{
  "username": "C-09106",
  "password": "Admin1234"
}
```

### Request

Nama      | Tipe Data | Required | Deskripsi
--------- | --------- | -------- | ---------
username | string | Y | username untuk user
password | string | Y | password untuk user

> Response

```json
{
  "status": "success",
  "message": "user found",
  "data": {
    "userinfo": {
      "id": 2,
      "username": "C-09106",
      "password": "eyJpdiI6Ikt1NnUxN3pNbEdBUFQ5Y1wvUHJOdVlBPT0iLCJ2YWx1ZSI6IjJCZVNPVUVCTWhWRG5ia1h4azZ1SUE9PSIsIm1hYyI6IjM3MGRkZTY1ZGYyYjZmOGZmZTFkYTcxZmZlZTBhZWE0ZjNiZWE4NzUyNGE4MWNiMDU5MDlkZWVkY2M2NjdlMDkifQ==",
      "typeuser": "collector",
      "api_token": "aAU7XGzxjaZxYMwSD5HfeKRBX0otzV42yc9JcJmiXxa22UY4CdxRIj000308",
      "status": true,
      "remember_token": null,
      "userid": 1111,
      "createdby": "SYSTEM",
      "createdon": "2017-08-30 14:23:25",
      "lastupdatedby": "SYSTEM",
      "updated_at": "2017-09-19 08:30:53",
      "nama": "AGUNG PARIANTO"
    }
  }
}
```
### Response

Nama      | Tipe Data | Deskripsi
--------- | --------- | ---------
id | integer | Id user
username | string | username untuk user
password | string | Password untuk user
typeuser | string | Tipe user, apakah toko atau collector
api_token| string | Encrypted text dari user yang dijadikan identifikasi saat request
status | boolean | Status user ketika login, jika benar maka true, jika tidak maka false
remember_token | string | Untuk fitur remember login
userid | integer | Jika login sebagai toko maka id toko, jika login sebagai collector maka id collector
createdby | string | Yang membuat user
createdon | datetime | Tanggal dan waktu ketika user dibuat
lastupdateby | string | Yang terakhir mengupdate updated_at datetime Tanggal dan waktu ketika user diupdate
updated_at | datetime | Tanggal dan waktu ketika user diupdate
nama | string | Nama user

## COLLECTOR :: SETOR (POST)

Endpoint ini memberi informasi tentang uang yang sudah disetorkan ke bank. Request anda harus berisi informasi berikut

### HTTP Request

`POST http://paycoll.javasign.id/api/sync`

> Request

```json
POST http://paycoll.javasign.id/api/login HTTP/1.1
Host: paycoll.javasign.id
Content-Type: application/json
accesstoken: [access_token]




{
  "setoruang": [
    {
      "nominal": 50,
      "berita": "bbbb",
      "nama_bank": "bri",
      "tanggal": "2017-09-05"
    }
  ]
}
```

### Request

Nama      | Tipe Data | Required | Deskripsi
--------- | --------- | -------- | ---------
nominal | integer | Y | Nominal yang telah disetorkan
berita | string | Y | Berita ketika menyetorkan uang
nama_bank | string | Y | Nama bank
tanggal | date | Y | Tanggal menyetorkan uang

> Response

```json
{
  "status": "success",
  "message": "sync success",
  "data": {
    "setoruang": [
      {
        "nominal": 50,
        "berita": "bbbb",
        "nama_bank": "bri",
        "tanggal": "2017-09-05"
      }
    ],
    "bayar": [],
    "hasilPembayaran": []
  }
}
```

### Response

Nama      | Tipe Data | Deskripsi
--------- | --------- | ---------
**setorUang** | | 
nominal | integer | Nominal yang telah disetorkan
berita | string | Berita ketika menyetorkan uang
nama_bank | string | Nama bank
tanggal | date | Tanggal menyetorkan uang

## COLLECTOR :: SETOR UANG

Endpoint ini menampilkan semua info data toko yang telah menyetorkan uang.

### HTTP Request

`GET http://paycoll.javasign.id/api/setoruang/lists`

> Request

```json
GET http://paycoll.javasign.id/api/piutang HTTP/1.1
Host: paycoll.javasign.id
Content-Type: application/json
accesstoken: [access_token]
```

### Request

Tidak ada parameter yang dibutuhkan. Hanya request header.

> Response

```json
{
  "status": "success",
  "message": "data found",
  "data": {
    "register": [
      {
        "id": 1,
        "collectorid": 1111,
        "tgltransfer": "04-09-2017",
        "nominaltransfer": "9020000",
        "beritatransfer": "pembayaran toko SARANG DIESEL",
        "namabank": "BRI",
        "createdby": "SYSTEM",
        "created_at": "2017-09-04 13:30:55",
        "lastupdatedby": "SYSTEM",
        "updated_at": "2017-09-04 13:30:55"
      },
      {
        "id": 3,
        "collectorid": 1111,
        "tgltransfer": "05-09-2017",
        "nominaltransfer": "200",
        "beritatransfer": "aaa",
        "namabank": "BRI",
        "createdby": null,
        "created_at": null,
        "lastupdatedby": null,
        "updated_at": null
      }
    ]
  }
}
```

### Response

Nama      | Tipe Data | Deskripsi
--------- | --------- | ---------
id | integer | Id user
collectorid | integer | Id collector
tgltransfer | date | Tanggal ketika transfer
nominaltransfer | string | Nominal uang yang ditransfer
beritatransfer | string | Berita ketika transfer
createdby | string | Yang membuat request
created_at | datetime | Tanggal dan waktu ketika membuat request untuk dikunjungi
lastupdateby | string | Yang terakhir mengupdate
updated_at | datetime | Tanggal dan waktu ketika mengupdate request untuk dikunjungi

## COLLECTOR :: BAYAR

Endpoint ini memberi informasi tentang data toko yang telah membayar serta jenis pembayarannya. Request anda harus berisi informasi berikut

### HTTP Request

`POST http://paycoll.javasign.id/api/sync`

> Request

```json
POST http://paycoll.javasign.id/api/login HTTP/1.1
Host: paycoll.javasign.id
Content-Type: application/json
accesstoken: [access_token]




{
  "bayar": [
    {
      "idtoko": 50,
      "tgl_bayar": "2017-09-19",
      "keterangan": "aku bayar nih",
      "data": [
        {
          "total_bayar": 1000,
          "jenis_pembayaran": "KAS"
        },
        {
          "total_bayar": 1000,
          "jenis_pembayaran": "BGC",
          "no_bgc": "no_bgc",
          "jenis_bgc": "jenis_bgc",
          "tgl_jatuh_tempo_bgc": "2017-09-19"
        }
      ]
    }
  ]
}
```

### Request

Nama      | Tipe Data | Required | Deskripsi
--------- | --------- | -------- | ---------
**bayar** | | 
idtoko | integer | Y | Id toko
tgl_bayar | date | Y | Tanggal melakukan pembayaran
keterangan | string | Y | Keterangan ketika membayar
**data** | |
total_bayar | integer | Y | Total ketika membayar
jenis_pembayaran | string | Y | Jenis pembayaran
total_bayar | integer | Y | Total ketika membayar
jenis_pembayaran | string | Y | Jenis pembayaran
no_bgc | string | Y | Nomor bilyet giro
jenis_bgc | string | Y | Jenis bilyet giro
tgl_jatuh_tempo_bgc | date | Y | Tanggal jatuh tempo bilyet giro

> Response

```json
{
  "status": "success",
  "message": "sync success",
  "data": {
    "setoruang": [],
    "bayar": [
      {
        "idtoko": 50,
        "tgl_bayar": "2017-09-19",
        "keterangan": "aku bayar nih",
        "data": [
          {
            "total_bayar": 1000,
            "jenis_pembayaran": "KAS"
          },
          {
            "total_bayar": 1000,
            "jenis_pembayaran": "BGC",
            "no_bgc": "no_bgc",
            "jenis_bgc": "jenis_bgc",
            "tgl_jatuh_tempo_bgc": "2017-09-19"
          }
        ]
      }
    ],
    "hasilTagihan": []
  }
}
```

### Response

Nama      | Tipe Data | Deskripsi
--------- | --------- | ---------
**bayar** | | 
idtoko | integer | Id toko
tgl_bayar | date | Tanggal melakukan pembayaran
keterangan | string | Keterangan ketika membayar
**data** | |
total_bayar | integer | Total ketika membayar
jenis_pembayaran | string | Jenis pembayaran
total_bayar | integer | Total ketika membayar
jenis_pembayaran | string | Jenis pembayaran
no_bgc | string | Nomor bilyet giro
jenis_bgc | string | Jenis bilyet giro
tgl_jatuh_tempo_bgc | date | Tanggal jatuh tempo bilyet giro

## COLLECTOR :: STATUS PEMBAYARAN

Endpoint ini menampilkan semua info data status pembayaran, baik tunai maupun giro.

### HTTP Request

`GET http://paycoll.javasign.id/api/pembayaran/status`

> Request

```json
GET http://paycoll.javasign.id/api/piutang HTTP/1.1
Host: paycoll.javasign.id
Content-Type: application/json
accesstoken: [access_token]
```

### Request

Tidak ada parameter yang dibutuhkan. Hanya request header.

> Response

```json
{
  "status": "success",
  "message": "data status",
  "data": {
    "tunaiDiTangan": 10023020,
    "tunaiDiSetor": 9020870,
    "tunaiDiTransfer": 100,
    "giro": [
      {
        "nominal": "144476",
        "nomorGiro": "1010101"
      },
      {
        "nominal": "100",
        "nomorGiro": "1323123"
      },
      {
        "nominal": "20",
        "nomorGiro": "1323123"
      }
    ]
  }
}
```

### Response

Nama      | Tipe Data | Deskripsi
--------- | --------- | ---------
tunaiDiTangan | integer | Jumlah nominal tunai yang ada ditangan
tunaiDiSetor | integer | Jumlah nominal tunai yang disetor
tunaiDiTransfer | integer | Jumlah nominal tunai yang ditransfer giro
nominal | string | Nominal yang telah dibayarkan
nomorGiro | string | Nomor giro

## COLLECTOR :: HASIL TAGIHAN

Endpoint ini memberikan informasi tentang toko yang sudah membayar. Request anda harus berisi informasi berikut

### HTTP Request

`POST http://paycoll.javasign.id/api/sync`

> Request

```json
POST http://paycoll.javasign.id/api/login HTTP/1.1
Host: paycoll.javasign.id
Content-Type: application/json
accesstoken: [access_token]




{
  "hasiltagihan": [
    {
      "idtoko": 50,
      "tgl_tagih": "2017-09-22",
      "keterangan": "bri"
    }
  ]
}
```

### Request

Nama      | Tipe Data | Required | Deskripsi
--------- | --------- | -------- | ---------
idtoko | integer | Y | Id toko
tgl_tagih | date | Y | Tanggal ketika melakukan penagihan
keterangan | string | Y | Keterangan ketika melakukan penagihan

> Response

```json
{
  "status": "success",
  "message": "sync success",
  "data": {
    "setoruang": [],
    "bayar": [],
    "hasilPembayaran": [
      {
        "tokoid": 50,
        "tgltagih": "2017-09-22",
        "keterangantagih": "bri",
        "updated_at": "2017-09-28 09:18:53",
        "created_at": "2017-09-28 09:18:53",
        "id": 9
      }
    ]
  }
}
```

### Response

Nama      | Tipe Data | Deskripsi
--------- | --------- | ---------
**hasilPembayaran** | |
tokoid | integer | Id toko
tgltagih | date | Tanggal ketika melakukan penagihan
keterangantagih | string | Keterangan ketika melakukan penagihan
updated_at | datetime | Tanggal dan waktu ketika
mengupdate | hasil | pembayaran
created_at | datetime | Tanggal dan waktu ketika membuat hasil pembayaran
id | integer | Id hasil pembayaran

## COLLECTOR :: REGISTER INDEX

Endpoint ini menampilkan semua tagihan beserta nota dan detailnya

### HTTP Request

`GET http://paycoll.javasign.id/api/register/lists`

> Request

```json
GET http://paycoll.javasign.id/api/piutang HTTP/1.1
Host: paycoll.javasign.id
Content-Type: application/json
accesstoken: [access_token]
```

### Request

Tidak ada parameter yang dibutuhkan. Hanya request header.

> Response

```json
{
  "status": "success",
  "message": "data found",
  "data": {
    "register": [
      {
        "noreg": "6105900",
        "tglreg": "21-10-2016",
        "id": 27847,
        "nota": [
          {
            "nama": "PERKASA MOTOR",
            "wilayah": "hb-0091",
            "password": "undefined",
            "TokoIDWiser": 24844,
            "tokoIDISA": "0001231",
            "amountTotal": "1350000",
            "amountPaidTotal": 0,
            "listnota": [
              {
                "kartupiutangid": 168429,
                "detailId": 914264,
                "tglJthtempo": "27-07-2011",
                "tglNota": "27-04-2011",
                "rptagih": "1350000",
                "bayar": 0,
                "nonota": "IFB0958"
              }
            ]
          },
          {
            "nama": "BUDI MOTOR",
            "wilayah": "hb-0091",
            "password": "undefined",
            "TokoIDWiser": 17131,
            "tokoIDISA": "1045595",
            "amountTotal": 1209000,
            "amountPaidTotal": 0,
            "listnota": [
              {
                "kartupiutangid": 265608,
                "detailId": 914279,
                "tglJthtempo": "23-09-2014",
                "tglNota": "21-06-2014",
                "rptagih": "1195000",
                "bayar": 0,
                "nonota": "IME1083"
              },
              {
                "kartupiutangid": 265609,
                "detailId": 914282,
                "tglJthtempo": "22-09-2015",
                "tglNota": "24-06-2015",
                "rptagih": "14000",
                "bayar": 0,
                "nonota": "IKE1382"
              }
            ]
          }
        ]
      }
    ]
  }
}
```

### Response

Nama      | Tipe Data | Deskripsi
--------- | --------- | ---------
noreg | string | Nomor registrasi user
tglreg | date | Tanggal registrasi user
id | integer | Id user
**nota** |  |
nama | string | Nama toko yang ada pada nota
wilayah | string | Wilayah toko yang ada pada nota
password | string | Password saat login
TokoIDWiser | integer | Value id dari tabel toko
tokoIDISA | string | Value dari tokoidwarisan
amountTotal | integer | Total amount tagihan
amountPaidTotal | integer | Total yang dibayarkan dari tagihan
**listnota** | |
kartupiutangid | integer | Id kartu piutang
detailId | integer | Id dari tagihan detail
tglJthtempo | date | Tanggal jatuh tempo
tglNota | date | Tanggal yang ada pada nota
rptagih | string | Jumlah tagihan
bayar | integer | Jumlah yang dibayarkan
nonota | string | Nomor nota
