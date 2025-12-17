---
title: Datasource Grafana - File Spreadsheets
updated: 2025-12-16 23:08:51Z
created: 2025-12-16 23:00:02Z
latitude: -6.40248440
longitude: 106.79424050
altitude: 0.0000
---

<span style="color: rgb(0, 0, 0);">Untuk menggunakan data dari Excel di Grafana, Anda perlu mengonversi file Excel (XLSX) ke format CSV, lalu gunakan plugin Datasource seperti Infinity atau plugin CSV langsung untuk mengimpornya, atau gunakan Google Sheets plugin jika datanya di Google Sheets, lalu visualisasikan dalam panel Grafana, karena Excel sendiri bukan sumber data native bawaan Grafana seperti database atau Prometheus.</span>

<span style="color: rgb(0, 0, 0);">Langkah-langkah Umum:</span>

1.  <span style="color: rgb(0, 0, 0);">**Konversi Excel ke CSV**:</span>
    - <span style="color: rgb(0, 0, 0);">Buka file Excel Anda (XLSX).</span>
    - <span style="color: rgb(0, 0, 0);">Pilih **File > Save As** dan pilih format **CSV (Comma delimited) (\*.csv)**.</span>
2.  <span style="color: rgb(0, 0, 0);">**Pilih Plugin Datasource Grafana**:</span>
    - <span style="color: rgb(0, 0, 0);">**Plugin Infinity**: Plugin ini sangat populer untuk membaca data dari CSV atau JSON langsung dari URL atau file, sangat fleksibel.</span>
    - <span style="color: rgb(0, 0, 0);">**CSV Datasource Plugin**: Ada plugin khusus untuk menangani file CSV.</span>
    - <span style="color: rgb(0, 0, 0);">**Google Sheets Plugin**: Jika Anda mengunggah data ke Google Sheets, plugin ini memungkinkan Grafana membaca langsung dari Google Sheets.</span>
3.  <span style="color: rgb(0, 0, 0);">**Tambahkan Datasource di Grafana**:</span>
    - <span style="color: rgb(0, 0, 0);">Buka Grafana, masuk ke **Configuration > Data sources > Add data source**.</span>
    - <span style="color: rgb(0, 0, 0);">Cari dan pilih plugin yang Anda instal (misalnya, Infinity, CSV, atau Google Sheets).</span>
    - <span style="color: rgb(0, 0, 0);">Konfigurasi URL file CSV atau Google Sheet Anda.</span>
4.  <span style="color: rgb(0, 0, 0);">**Buat Dashboard & Visualisasi**:</span>
    - <span style="color: rgb(0, 0, 0);">Buat panel baru (misalnya, *Time series*, *Table*, *Gauge*).</span>
    - <span style="color: rgb(0, 0, 0);">Pilih Datasource yang telah Anda buat.</span>
    - <span style="color: rgb(0, 0, 0);">Gunakan fitur **Transform** di Grafana untuk memfilter, mengatur ulang, atau menggabungkan data jika diperlukan.</span>

<span style="color: rgb(0, 0, 0);">Contoh Praktis (Menggunakan Infinity):</span>

1.  <span style="color: rgb(0, 0, 0);">Unggah file CSV Anda ke tempat yang dapat diakses secara publik (misalnya, GitHub Gist atau web server Anda).</span>
2.  <span style="color: rgb(0, 0, 0);">Di Grafana, tambahkan datasource **Infinity**.</span>
    - <span style="color: rgb(0, 0, 0);">Pilih **URL** sebagai sumber.</span>
    - <span style="color: rgb(0, 0, 0);">Masukkan URL file CSV Anda.</span>
    - <span style="color: rgb(0, 0, 0);">Atur **Format** sebagai CSV.</span>
3.  <span style="color: rgb(0, 0, 0);">Pada panel, gunakan query untuk memilih kolom dan buat visualisasi.</span>

<span style="color: rgb(0, 0, 0);">Dengan cara ini, Anda dapat mengubah data Excel statis menjadi dashboard visual yang dinamis di Grafana.</span>