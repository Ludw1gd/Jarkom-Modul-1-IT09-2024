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

## Soal 8 (FTP Login)

![image](https://github.com/user-attachments/assets/a1b60047-63eb-4209-9a87-332505b4cc43)

Pertama, Username untuk login dapat ditemukan pada packet yang menyatakan berhasil login seperti gambar di atas dan dengan mem filter packet menjadi TCP saja.

![image](https://github.com/user-attachments/assets/e53fd77c-d10c-462e-864d-aabf3172f651)

Selanjutnya, password dapat kita lihat di bawah packet yang menyatakan username berhasil.

![image](https://github.com/user-attachments/assets/6c9fe0e4-608f-4913-8f1f-eda4a07dc5a6)

Selesai, flag didapatkan

## Soal 9 (Suprise)

![image](https://github.com/user-attachments/assets/3620cd80-2156-467d-9ac9-f24e37eb90e3)

Dengan file yang sama dengan nomer sebelumnya, kita bisa menemukan nama service yang digunakan di Packet paling awal.

![image](https://github.com/user-attachments/assets/730f395f-b84c-460e-a4d9-f4a04f31e0c6)

File yang dikirim dapat kita lihat di packet yang menunjukkan pengiriman file.

![image](https://github.com/user-attachments/assets/78389709-059c-4fc0-a9d9-bedb104224ea)

![image](https://github.com/user-attachments/assets/6e498d2d-f490-490f-9041-33975f1b262b)

Kita bisa menemukan string yang tersembunyi dengan membuka file cpp yang dikirim oleh attacker dan bisa kita compile seperti di atas

![image](https://github.com/user-attachments/assets/16a74004-e1a1-4bcb-b49b-5c0177f34fe5)

Selesai, flag ditemukan

## Soal 10 (22 Nightmare)

![image](https://github.com/user-attachments/assets/b949ad42-5c36-4580-af62-069b863e95d3)

Pada soal pertama, kita diminta untuk menemukan file yang dikirim penyerang. Kita dapat menemukannya dengan memberi filter ftp terlebih dahulu, lalu mencari packet yang memiliki kata STOR

![image](https://github.com/user-attachments/assets/d28b14e2-c623-44b0-b6e2-5d75a340bc3a)

Lalu, untuk soal kedua, kita perlu men download file yang dikirim tersebut dengan cara memberi tambahan filter OR ftp-data karena disinilah packet-packet file berada. 

![image](https://github.com/user-attachments/assets/a96409e6-0b45-47af-9b66-db88ef35a33b)

Setelah itu, kita bisa follow tcp packet tersebut lalu mengubahnya menjadi raw terlebih dahulu, lalu disimpan dengan ekstensi jpg agar bisa dibuka

![image](https://github.com/user-attachments/assets/abf0c7e0-c4a5-43fa-a3d2-2cdcd9c0a4d3)

Disini kita menemukan sebuah gambar dengan tulisan NUN, yang mana merupakan jawaban dari pertanyaan ke 2 ini

![image](https://github.com/user-attachments/assets/35efeae9-d843-4dcf-bbf0-88a16825572e)

Selanjutnya, untuk soal ke 3, kita dapat menemukan nomor stream dari file kedua yaitu kono.py dengan klik kanan dan follow stream tcp file tersebut, yang mana dalam case ini adalah 141.

![image](https://github.com/user-attachments/assets/a4e47be7-23e7-4868-9ad0-45b03eb1c275)

Terakhir, untuk mencari nama asli pengirim, kita dapat copas python script dalam packet yang dikirim, dan melakukan sedikit modifikasi pada kodenya seperti berikut

```
def string_to_bin(s):
    return ''.join(format(ord(char), '08b') for char in s)

def bin_to_string(b):
    chars = [chr(int(b[i:i+8], 2)) for i in range(0, len(b), 8)]
    return ''.join(chars)

def xor_with_key(input, key):
    key_bin = string_to_bin(key)
    key_bin_repeated = (key_bin * ((len(input) // len(key_bin)) + 1))[:len(input)]
    value = ''.join(str(int(a) ^ int(b)) for a, b in zip(input, key_bin_repeated))
    return value

input = "001001100011010000100010001000100011101001101110001001110011100001101110000110100011101000111100001011110011111000100001011011100001111000100001001111010011110100100111"
key = "NUN"

value = xor_with_key(input, key)
ascii_value = bin_to_string(value)

print(ascii_value)
```
Dengan sedikit bantuan Google, disini kita bisa merubah python code tersebut sehingga dapat melakukan operasi XOR dengan kunci dari gambar yang telah kita dapat tadi, sehingga kita perlu mengubah kata "NUN" tersebut menjadi sebuah binary, lalu melakukan operasi XOR pada input yang telah diberikan dan mengubahnya kembali menjadi ASCII text, dimana output dari operasi tersebut merupakan "hallo im *Torako Koshi*". Dari output tersebut, kita mendapatkan nama yang dimaksud beserta flag nya

![image](https://github.com/user-attachments/assets/29753faf-14f0-4b90-9a02-58468306364c)

