# Automasi Pengujian Web BPJS Ketenagakerjaan

Repository ini berisi project automation testing berbasis **Katalon Studio**.

Fokus pengujian ada pada beberapa alur utama di website BPJS Ketenagakerjaan, terutama yang berhubungan dengan navigasi halaman publik, pergantian bahasa, validasi elemen halaman kontak, dan akses ke fitur simulasi saldo. Selain suite utama yang sudah dirangkai untuk dijalankan, project ini juga sudah memiliki beberapa test case tambahan hasil pengembangan lanjutan pada area homepage.

## Tujuan Pengerjaan

Project ini di susun untuk menunjukkan pendekatan kerja dalam menulis automation test UI, yaitu:

- memecah skenario ke dalam test case yang kecil dan jelas
- mengelompokkan skenario sejenis ke dalam test suite
- memisahkan object locator ke `Object Repository`
- menjaga project tetap rapi untuk kebutuhan version control

## Cakupan Pengujian

Pengujian dalam repository ini saat ini mencakup empat area utama yang sudah tersusun dalam test suite, ditambah beberapa test case tambahan yang sudah tersedia di level project.

### 1. Pergantian Bahasa di Homepage

Suite: [ts_lang.ts](Test%20Suites/ts_lang.ts)

Skenario yang diuji:

- mengganti bahasa dari Indonesia ke English
- mengganti bahasa dari English ke Indonesia
- menangani popup agar alur pengujian tetap stabil

Test case yang dipakai:

- `main/setup_01_buka_web_tanpa_login`
- `homepage/lang-01_ganti_bahasa_ke_english`
- `main/util_01_close_popup_tanpa_buka_browser`
- `homepage/lang-02_ganti_bahasa_ke_indo`
- `main/teardown_close_browser`

### 2. Navigasi Header Homepage

Suite: [ts_header.ts](Test%20Suites/ts_header.ts)

Skenario yang diuji:

- menu penerima upah
- menu bukan penerima upah
- menu jasa konstruksi
- menu pekerja migran Indonesia
- menu cara klaim
- menu berita
- menu tentang kami
- menu laporan pengelolaan program
- menu laporan integrasi
- menu good governance
- menu peraturan
- menu TJSL

Test case yang dipakai:

- `main/setup_01_buka_web_tanpa_login`
- `homepage/head-01_inkep_penerima_upah`
- `homepage/head-02_inkep_bkn_penerima_upah`
- `homepage/head-03_inkep_jasa_konstruksi`
- `homepage/head-04_inkep_pekerja_migran_indo`
- `homepage/head-05_cara_claim`
- `homepage/head-06_berita`
- `homepage/head-07_tentang_kami`
- `homepage/head-08_ip_lpp`
- `homepage/head-09_ip_lap_integrasi`
- `homepage/head-10_ip_good_governance`
- `homepage/head-11_ip_peraturan`
- `homepage/head-12_ip_tjls`
- `main/teardown_close_browser`

### 3. Halaman Kontak

Suite: [ts_contact.ts](Test%20Suites/ts_contact.ts)

Skenario yang diuji:

- membuka halaman kontak
- memvalidasi keberadaan elemen peta kantor pusat

Test case yang dipakai:

- `main/setup_01_buka_web_tanpa_login`
- `contact_page/con-01_maps_head_office`
- `main/teardown_close_browser`

### 4. Halaman Simulasi Saldo

Suite: [ts_simulasi_saldo.ts](Test%20Suites/ts_simulasi_saldo.ts)

Skenario yang diuji:

- membuka website tanpa login
- mengakses dan memvalidasi alur menuju halaman simulasi saldo

Test case yang dipakai:

- `main/setup_01_buka_web_tanpa_login`
- `simulasi_saldo/vw_simulasi_saldo`
- `main/teardown_close_browser`

Di luar suite ini, project juga memiliki test case tambahan terkait saldo, yaitu:

- `homepage/saldo_upah`
- `saldo_upah`

Kedua file tersebut saat ini sudah tersedia di project, tetapi belum dirangkai ke dalam test suite yang aktif.

## Struktur Project

```text
.
|-- Test Cases/
|-- Test Suites/
|-- Object Repository/
|-- Scripts/
|-- Profiles/
|-- Include/
|-- settings/
|-- Bpjs Ketenagakerjaan.prj
|-- build.gradle
```

Keterangan singkat:

- `Test Cases/` berisi skenario pengujian per kasus
- `Test Suites/` berisi kumpulan test case yang dijalankan bersama
- `Object Repository/` berisi locator elemen
- `Scripts/` berisi script Groovy hasil generate Katalon
- `Profiles/` berisi konfigurasi environment

Secara keseluruhan, isi project saat ini terdiri dari:

- 22 test case
- 4 test suite utama
- object repository untuk halaman homepage, contact page, dan simulasi saldo

## Konfigurasi Dasar

Profile default yang dipakai ada di [default.glbl](Profiles/default.glbl) dengan nilai:

- `base_url`: `https://www.bpjsketenagakerjaan.go.id/`
- `contact_url`: `https://www.bpjsketenagakerjaan.go.id/en/kontak.html`

## Cara Menjalankan

### Melalui Katalon Studio

1. Buka Katalon Studio.
2. Open project ini.
3. Pilih test suite yang ingin dijalankan:
   - `ts_lang`
   - `ts_header`
   - `ts_contact`
   - `ts_simulasi_saldo`
4. Jalankan suite dengan browser yang diinginkan.

### Melalui Katalon Runtime

Project ini juga menyertakan file [build.gradle](build.gradle), tetapi eksekusi utamanya tetap ditujukan untuk Katalon Studio atau Katalon Runtime Engine.

Jika runtime Katalon tersedia, project dapat dijalankan dengan mengarah ke file:

- `Bpjs Ketenagakerjaan.prj`

## Catatan

- Repository ini disusun sebagai submission technical test, jadi prioritas utamanya adalah keterbacaan struktur dan kejelasan cakupan test.
- Folder hasil generate seperti `Reports/`, `bin/`, `Libs/`, dan konfigurasi lokal tidak disertakan ke repository.
- Locator disimpan di `Object Repository/` agar perubahan elemen UI lebih mudah di mantain.
- Project ini belum dimaksudkan sebagai test suite yang lengkap untuk seluruh website, tetapi sebagai representasi cara menyusun automation test yang terstruktur dan mudah ditelusuri saat direview.
