# Praktikum Jaringan Komputer Modul 1
## Anggota Kelompok D02
| NRP | Nama | Kontribusi |
| :---:        |     :---:           | :---: |
| 5025201082   | Farrel Emerson      | 1,2,3     |
| 5025201087   | Daniel Hermawan     | 4,5,6,7      |
| 5025201003   | Rahmat Faris Akbar  |   8,9,10    |

## Soal 1
Sebutkan web server yang digunakan pada "monta.if.its.ac.id"! 
### Jawab
* #### Filter
```http.host eq monta.if.its.ac.id```
* #### Penjelasan
Display filter ```http.host eq monta.if.its.ac.id``` digunakan untuk menampilkan paket http yang memiliki host ```monta.if.its.ac.id```

![image](https://user-images.githubusercontent.com/82019030/192073904-3da8684d-31e8-4198-ad1c-d3ac298965a6.png)

## Soal 2
Ishaq sedang bingung mencari topik ta untuk semester ini , lalu ia datang ke website monta dan menemukan detail topik pada website “monta.if.its.ac.id” , judul TA apa yang dibuka oleh ishaq ?
### Jawab
* #### Filter
```http.host eq monta.if.its.ac.id```
* #### Penjelasan
Gunakan filter yang digunakan pada soal 1, lalu export object sebagai http pada paket yang mengandung **detail topik**

![image](https://user-images.githubusercontent.com/82019030/192074082-9b37cf59-0fd9-42f2-8862-ad6c3be53a48.png)

Setelah kita export, kita ganti jenis file tersebut menjadi html dengan menambahkan ```.html``` pada nama file tersebut

![image](https://user-images.githubusercontent.com/82019030/192074113-84682dfb-6a03-433b-a731-bc65bf42356b.png)

Setelah itu dibuka dan kita bisa melihat bahwa Ishaq membuka **Evaluasi unjuk kerja User Space Filesystem (FUSE) oleh WAHYU SUADI**

![image](https://user-images.githubusercontent.com/82019030/192074155-20385a43-aa92-40c7-965a-ddf7e4e5d46a.png)

## Soal 3
Filter sehingga wireshark hanya menampilkan paket yang menuju port 80! 
### Jawab
* #### Filter
`tcp.dstport == 80`
* #### Penjelasan
Dengan membuka file soal3-6.pcapng lalu melakukan filter dengan syntax `tcp.dstport == 80` maka akan muncul tampilan seperti di bawah.

![image](https://user-images.githubusercontent.com/99629909/192102488-1ddb0b43-d4cf-434a-846f-733b79218875.png)

## Soal 4
Filter sehingga wireshark hanya mengambil paket yang berasal dari port 21!
### Jawab
* #### Filter
`tcp.srcport == 21`
* #### Penjelasan
Untuk mengambil paket yang hanya berasal dari port 20, dilakukan display filter seperti di bawah:

![image](https://user-images.githubusercontent.com/99629909/192102567-e589e18e-c773-415b-9741-1ca1b045bc77.png)

## Soal 5
Filter sehingga wireshark hanya mengambil paket yang berasal dari port 443!
### Jawab
* #### Filter
`tcp.srcport == 443`
* #### Penjelasan
Untuk mengambil paket yang berasal dari port 443, dilakukan display filter seperti di bawah:

![image](https://user-images.githubusercontent.com/99629909/192102641-e0731356-f7a9-4266-a798-9a484dddd669.png)

## Soal 6
Filter sehingga wireshark hanya menampilkan paket yang menuju ke lipi.go.id !
### Jawab
* #### Filter
[cara 1]: `ip.dst == 203.160.128.158`

[cara 2]: `ip.dst ==  lipi.go.id`
* #### Penjelasan
[cara 1]

Kita terlebih dahulu mencari alamat ip dari lipi.go.id dengan menggunakan cmd dengan menggunakan perintah tracert yang membuahkan alamat ip 203.160.128.158 . Kemudian kita melakukan filter menggunakan alamat ip tersebut dengan menuliskan `ip.dst == 203.160.128.158`

![image](https://user-images.githubusercontent.com/99629909/192102947-52481842-f000-4b36-9d71-9173f5516cb8.png)

[cara 2]

pertama kita centang semua view

![image](https://user-images.githubusercontent.com/99629909/192102975-75c2281a-c09f-4b07-9760-2af84dbde7a3.png)

lalu kita ketik `ip.dst ==  lipi.go.id` pada display filter

![image](https://user-images.githubusercontent.com/99629909/192102986-038318b3-3de6-4e35-9eb4-a61a560587fd.png)

## Soal 7
Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
### Jawab
* #### Filter
`ip.src_host eq 192.168.1.31`
* #### Penjelasan
Untuk mencari ip kita sendiri kita dapat membuka cmd dan menulis syntax `ipconfig`

![image](https://user-images.githubusercontent.com/99629909/192103024-fe05c8ff-43e9-41df-997b-82ea26238f49.png)

Lalu kita scroll ke wifi untuk mendapatkan ip kita.

![image](https://user-images.githubusercontent.com/99629909/192103072-ece8a58d-58f9-4303-8ea1-8a5812d42e71.png)

Lalu menggunakan wireshark kita menggunakan `ip.src_host eq 192.168.1.31` untuk memfilter paket yang berasal dari ip kita.


## Soal 8
Telusuri aliran paket dalam file .pcap yang diberikan, cari informasi berguna berupa percakapan antara dua mahasiswa terkait tindakan kecurangan pada kegiatan praktikum. Percakapan tersebut dilaporkan menggunakan protokol jaringan dengan tingkat keandalan yang tinggi dalam pertukaran datanya sehingga kalian perlu menerapkan filter dengan protokol yang tersebut.
### Jawab
* #### Filter
`ip.src ==127.0.0.1 && ip.dst == 127.0.1.1`
atau
`ip.src ==127.0.1.1 && ip.dst == 127.0.0.1`

(sama saja, karena ketika kita follow, maka akan menampilkan percakapan dari alamat ip yang berhubungan secara vice versa)
* #### Penjelasan
Karena percakapan terjadi antara 2 mahasiswa, maka pasti ada 2 alamat ip yang saling
bertukar pesan dua arah. Sehingga kita harus menganalisis pasangan alamat ip yang
memiliki riwayat transport source – destination dan destination – source. Misalkan ada
alamat ip x dan ip y. Maka kita harus mencari yang sepertin berikut:
| Source  | Destination |
| :---: | :--: |
| ip x  | ip y  |
| ip y  | ip x  |

Tampilan awal di wireshark:
![image](https://user-images.githubusercontent.com/99629909/192072256-e8ef47c6-847f-4a62-9947-f9405f2ac72d.png)

Dari 20 nomor pertama dapat dilihat yang memenuhi kriteria hanyalah alamat ip 127.0.0.1 dan ip 127.0.1.1. Lebih jelasnya dapat dilihat di tabel di bawah:

<img width="159" alt="image" src="https://user-images.githubusercontent.com/99629909/192072333-d99bbade-baeb-473b-9c46-92a8f7567f8d.png">

Sehingga kita tahu bahwa alamat ip dari 2 mahasiswa itu adalah 127.0.0.1 dan 127.0.1.1

Dari sini kita dapat melakukan display filter dengan syntax seperti di atas.

![image](https://user-images.githubusercontent.com/99629909/192072380-bf58f193-0700-409f-95e8-735be7834d10.png)

Setelah itu klik kanan > follow > TCP Stream untuk 5 paket. Dan ternyata ada 3 paket yang berisi percakapan 2 mahasiswa tersebut :

![image](https://user-images.githubusercontent.com/99629909/192072396-28c37953-b0ef-4c4e-85b1-0fc5af1088ce.png)
![image](https://user-images.githubusercontent.com/99629909/192072403-d38022c5-216d-4c08-b680-1c6b0e866d2c.png)
![image](https://user-images.githubusercontent.com/99629909/192072410-65d4e890-cc30-45ec-b3f6-30f9915b811b.png)
* #### Kendala
Pada awalnya kami melakukan pencarian percakapan tersebut dengan cara kuli, yaitu melakukan follow setiap stream satu per satu sampai mendapatkan percakapan-percakapan itu sehingga hal tersebut tidak efisien.
## Soal 9
Terdapat laporan adanya pertukaran file yang dilakukan oleh kedua mahasiswa dalam percakapan yang diperoleh, carilah file yang dimaksud! Untuk memudahkan laporan kepada atasan, beri nama file yang ditemukan dengan format [nama_kelompok].des3 dan simpan output file dengan nama “flag.txt”.
### Jawab
* #### Filter
`tcp.port == 9002`
* #### Syntax decrypt di cmd
`openssl des3 -d -salt -in D02.des3 -out flag.txt`
* #### Penjelasan
<img width="353" alt="image" src="https://user-images.githubusercontent.com/99629909/192073177-b57a40e5-aa39-4522-bcb2-09ceca43f30e.png">

Berdasarkan percakapan diatas, terdapat clue yang melampirkan angka 9002 dan
kami mencurigai itu adalah angka yang mengacu pada sebuah port, sehingga kami
melakukan display filter untuk menampilkan port 9002.

Selanjutnya, kita bisa melihat bahwa dengan melakukan klik kanan > follow > TCP Stream, didapatkan hasil sebagai berikut :

![image](https://user-images.githubusercontent.com/99629909/192073233-d2c21bf5-da14-4578-a5f8-2b9be517c399.png)

Setelah itu kita harus merubahnya menjadi raw dahulu sebelum melakukan save dengan
format D02.des3 agar mudah di decrypt dengan bantuan openssl:

![image](https://user-images.githubusercontent.com/99629909/192073271-8e508a02-a252-4531-af53-332d7a0c136a.png)

Selanjutnya, kita akan melakukan decrypt dengan menggunakan openssl metode
des3.

<img width="528" alt="image" src="https://user-images.githubusercontent.com/99629909/192073535-674db9f1-8967-4749-8120-523ab4b289fa.png">

* #### Kendala
Kesulitan untuk melakukan decrypt file, karena ternyata file .des3 -nya harus di show dalam bentuk raw terlebih dahulu supaya bisa dilakukan decrypt menggunakan bantuan open ssl.

## Soal 10
Temukan password rahasia (flag) dari organisasi bawah tanah yang disebutkan di atas!
### Jawab
* #### Penjelasan
<img width="416" alt="image" src="https://user-images.githubusercontent.com/99629909/192072900-abfeb031-5cc1-43ff-a472-3bccd2b9b188.png">
Dari percakapan no.8 di atas, kita melakukan pencarian di google tentang siapa nama karakter anime kembar 5. Sehingga didapatkan nama "nakano" sebagai password decrypt.

<img width="521" alt="image" src="https://user-images.githubusercontent.com/99629909/192073593-1361866a-cd9a-4f23-9e7f-b325b9e134bc.png">

Setelah itu dapat kita lihat isi dari file flag.txt alias password rahasianya:

<img width="345" alt="image" src="https://user-images.githubusercontent.com/99629909/192073619-585846b7-a064-41d7-a4ff-1d31b4ce9360.png">



