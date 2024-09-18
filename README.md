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
