# Jarkom-Modul-1-IT09-2024

## Anggota

| Nama                  | NRP        |
| :-------------------- | :--------- |
| Michael Kenneth Salim | 5027231008 |
| Tio Axellino Irin     | 5027231065 |

## Soal 1 (Advance Sanity Check)

![Advance Sanity Check](https://github.com/user-attachments/assets/2628f40e-38d9-4423-9edd-f9704ba5d9d9)

Dilakukan filtering `frame contains "username"` dan Follow HTTP Stream sehingga ditemukan User yang dicari. Lalu `frame contains "."` dan Follow HTTP Streams mencari 1 file yang benar. Kemudian diikuti petunjuk yang ada di peraturan shift modul dan didecrypt kode yang dienkripsi menggunakan **ROT13** sehingga didapatkan flagnya.

## Soal 2 (Pegawai Negeri Sebelah)

![Pegawan Negeri Sebelah](https://github.com/user-attachments/assets/1d60fa2d-09be-43d8-ac4f-6e32fe26307a)

Dilakukan filtering `frame contains "nNnM%coQuF"` dan Follow TCP Stream sehingga ditemukan nama yang menggunakan password tersebut dengan `Find` atau `CTRL + F`. Lalu didapatkan jabatan yang sesuai dengan nama `Taufan Kuswandari` dengan `Find`. Kemudian didapatkan nama yang paling awal di list dan juga ditemukan password yang paling akhir di list sehingga didapatkan flagnya.

## Soal 3 (EZ)

![EZ](https://github.com/user-attachments/assets/3e6153cb-9962-42b6-9956-43ad57aea98a)

Follow HTTP Stream salah satu stream dengan protokol `TCP` sehingga didapatkan jawaban log. Didapatkan port yang dicari dengan membuka detail paket yang dipilih kemudian membuka dropdown `Transmission Control Protocol` sehingga didapatkan flagnya.

## Soal 4 (Malicious Code)

![Malicious Code](https://github.com/user-attachments/assets/defe65d2-01b4-4e7b-8fc2-7037d9bd5a3f)

Dilakukan filtering `frame contains "login"` dan Follow TCP Stream sehingga ditemukan petunjuk endpoint `./login.php` dan `Not Found` sehingga filtering lagi `frame contains "Not Found" && http`. 

![image](https://github.com/user-attachments/assets/b4a5c59d-d392-470d-8b03-daf568c6ff1e)

Karena ada banyak, lakukan sorting dengan `Time` sehingga dapat melihat perbedaan informasi time dengan kelima paket tersebut. Ada 57 paket dan dikurangi dengan 5 paket berbeda tersebut sehingga didapatkan **52** attempt dir listing. 

![image](https://github.com/user-attachments/assets/e78a3d3b-ce34-4c8d-b9cf-2f862396ef07)

Kemudian dilakukan filtering dengan "http.request" dan analisis sehingga didapatkan endpoint `/index.php` karena dari banyaknya `GET`, yang berhasil `POST` hanya `/index.php`.

![image](https://github.com/user-attachments/assets/953dcf0e-bcae-485b-8385-cc6c66fd8092)

Selanjutnya, dilakukan filtering dengan `http.request.method == "POST"` dan analisis ditemukan 1 dengan length yang beda sendiri. Lalu hitung attempt nya sampai awal dia mencoba menemukan email dan password yang benar sehingga didapatkan **153** attempt.

![image](https://github.com/user-attachments/assets/0535170f-81c1-4ffa-a0de-84e7e46d37f9)

Lalu, analisis 5 paket `POST` terakhir yang ada di list dan Follow HTTP Stream sehingga ditemukan pertanyaan dari si penyerang dalam bentuk kumpulan numerik. Kemudian didecrypt dengan menggunakan ASCII decoder sehingga didapatkan jawaban. Dari itu, didapatkan flagnya.

## Soal 5 (Packets Barrage)

![image](https://github.com/user-attachments/assets/9b6817b4-ecef-4ed9-b68a-03988bf157b0)

Dilakukan filtering "http" dan analisa bahwa terdapat banyak paket dengan `POST` tetapi tidak dengan `GET`, dapat dilihat **ip** attacker nya dari kolom `source`. Filtering `frame contains "Not Found"` untuk melihat dan mendapatkan total attempt bruteforce. Filtering `frame contains "GET"` untuk melihat paket yang statusnya bruteforce berhasil. Kemudian, Follow HTTP Stream paket tersebut dan didapatkan nama file yang didownload oleh attacker setelah berhasil login. Didapatkan juga isi dari file yang disisipkan oleh attacker.

## Soal 6 (Corporate Breach)

![image](https://github.com/user-attachments/assets/55a30801-8f2b-4bb6-a1d7-7f984f369074)

Nama attacker dapat ditemukan dari packet pertama yaitu Nakhamov

![image](https://github.com/user-attachments/assets/cf406406-c4f8-4a2e-b659-3aff99e1921e)

Selanjutnya untuk menemukan email yang digunakan untuk masuk, kita bisa filter http dan packet yang tidak mengandung kata invalid email. Dari langkah langkah tersebut kita bisa menemukan packet yang menandakan OK atau benar, sehingga ditemukan email dan pass nya yaitu jarkomsupport@gmail.com  dan j4rk0mg4c0rbg 

![image](https://github.com/user-attachments/assets/1eeaf39e-81e3-467a-9cb7-f880b0bd4ca7)

Flag berhasil didapatkan

## Soal 7 (Illegal Breakthrough)

![image](https://github.com/user-attachments/assets/2d93b78b-a4fa-4a46-bcee-5d0f8d41ed70)

Pertama, kita bisa menemukan IP korban dengan memberikan filter http dan melihat destinasi dari sang attacker yaitu 172.21.88.207

![image](https://github.com/user-attachments/assets/0a05813d-1c70-41ac-a734-9500712362ef)

Kedua, Portnya dapat kita temukan di destination port yaitu 1917

![image](https://github.com/user-attachments/assets/1d7f59d7-ef64-43dc-b22c-895481ac2b9a)

Ketiga, endpointnya untuk login dapat kita lihat di full URL nya yaitu /ww1.php

![image](https://github.com/user-attachments/assets/e1b42d01-d696-477a-ab52-79560047f900)

Selanjutnya, user agent nya dapat kita temukan disini dan dapat kita singkat menjadi uufh-v2.1.0-dev

![image](https://github.com/user-attachments/assets/14a20126-23ad-47de-9afb-62dc1a0e5464)

Untuk mencari username dan password yang digunakan, kita dapat melihat dimana packet dari request loginnya berupa OK atau berhasil sehingga didapatkan username dan passwornya yaitu Redbaron dan fly1ng4c3 

![image](https://github.com/user-attachments/assets/eeb94cd2-52f0-4213-a63e-c3310640a9f8)

Selesai, Flag didapatkan
