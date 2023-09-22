### Kelompok B-13 dengan anggota:
| **No** | **Nama** | **NRP** | 
| ------------- | ------------- | --------- |
| 1 | Andrian Tambunan  | 5025211018 | 
| 2 | Sandhika Surya Ardyanto | 5025211022 |

### Daftar Isi
- [Soal 1](#soal-1)
- [User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.](#user-melakukan-berbagai-aktivitas-dengan-menggunakan-protokol-ftp-salah-satunya-adalah-mengunggah-suatu-file)
- [](#)
- [](#-1)
- [Soal 2](#soal-2)
- [](#-2)
- [Soal 3](#soal-3)
- [Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:](#dapin-sedang-belajar-analisis-jaringan-bantulah-dapin-untuk-mengerjakan-soal-berikut)
- [Soal 4](#soal-4)
- [Soal 5](#soal-5)
- [Soal 9](#soal-9)

## Soal 1
User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.
---
---
- Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut? 

Pada soal1.pcapng dengan display filter "ftp" untuk menampilkan packet dengan protokol FTP. Mencari perintah untuk mengunggah file ke FTP Server dengan "STOR" yaitu pada packet 147 yang merupakan request. 
sequence number (raw) pada packet adalah 258040667

---
- Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut? 
  
Pada packet 147 yang merupakan request dengan acknowledge number (raw) adalah 1044861039

---
![alt text](https://github.com/Sandhika21/Jaringan-Komputer-D/blob/main/Praktikum1/Soal%201/1a_b.png)
---
---
- Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
  
Pada packet 149 yang merupakan response dengan sequence number (raw) adalah 1044861039

---
- Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?

Pada packet 149 yang merupakan response dengan acknowledge number (raw) adalah 258040696

---
![alt text](https://github.com/Sandhika21/Jaringan-Komputer-D/blob/main/Praktikum1/Soal%201/1c_d.png)
---
---

## Soal 2
Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!

IP portal praktikum Jaringan Komputer adalah 10.21.78.111 maka mencari packet dengan source address adalah 10.21.78.111 dan protokol HTTP sehingga display filternya `ip.src == 10.21.78.111 && http`.
Pada bagian header terlihat web server yang digunakan adalah gunicorn

![alt text](https://github.com/Sandhika21/Jaringan-Komputer-D/blob/main/Praktikum1/Soal%202.png)
---

## Soal 3
Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:
---
- Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702?

Port 3702 adalah nomor port yang digunakan dalam konteks protokol WS-Discovery (Web Services Discovery) yang merupakan bagian dari Universal Plug and Play (UPnP) dan Web Services on Devices (WSD). Port 3702 dapat digunakan baik untuk TCP dan UDP tergantung pada implementasi protokol. 

Display filter packet dengan IP source maupun destination address adalah 239.255.255.250 menggunakan `ip.addr == 239.255.255.250`. Jika display filter `ip.addr == 239.255.255.250 && tcp` maka tidak ada hasil yang muncul sehingga hanya ada protokol UDP.

Maka untuk display filter packet dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702 adalah `ip.addr == 239.255.255.250 && udp.port == 3702`

Banyak paket yang tercapture adalah 21

---
- Protokol layer transport apa yang digunakan?

Protokol layer transport yang digunakan adalah UDP

---

![alt text](https://github.com/Sandhika21/Jaringan-Komputer-D/blob/main/Praktikum1/Soal%203.png)

---

## Soal 4
Berapa nilai checksum yang didapat dari header pada paket nomor 130?

---

Untuk mencari nomor packet dengan memilih Edit Menu lalu klik `Find Packet`. Setelah itu pada Go Menu pilih `Go to Packet` lalu isikan nomor 130 pada `packet`. Maka akan menuju packet nomor 130 dan dapat melihat header yang berisi nilai checksum yaitu 0x18e5

![alt text](https://github.com/Sandhika21/Jaringan-Komputer-D/blob/main/Praktikum1/Soal%204.png)

---

## Soal 5
Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.

---
- Berapa banyak packet yang berhasil di capture dari file pcap tersebut?

Dapat dilihat dengan memilih `Capture File Properties` pada Statistics Menu maka menunjukkan jumlah packet sebanyak 60

![alt text](https://github.com/Sandhika21/Jaringan-Komputer-D/blob/main/Praktikum1/Soal%205/5a.png)

---
- Port berapakah pada server yang digunakan untuk service SMTP?
  
Pada display filter berisi `smtp` yang akan menghasilkan packet dengan protokol SMTP lalu memilih adanya `S` pada bagian info untuk dilihat header nya. `S` menandakan bahwa merupakan response dari server. Setelah itu mencari bagian source port pada header dan didapat adalah 25

![alt text](https://github.com/Sandhika21/Jaringan-Komputer-D/blob/main/Praktikum1/Soal%205/5b.png)

---
- Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?


Private IP address yaitu 
- 10.0.0.0 sampai dengan 10.255.255.255
- 172.16.0.0 sampai dengan 172.31.255.255
- 192.168.0.0 sampai dengan 192.168.255.255

Untuk mencari public IP maka dengan mencari IP address yang tidak merupakan private IP dengan menggunakan salah satu sisi source atau destination address. Maka display filter `ip.src != 192.168.0.0/16 && ip.src != 172.16.0.0/12 && ip.src != 10.0.0.0/8`. Pada bagian source address hanya ada 1 yaitu 74.53.140.153. 

Pada 172.16.0.0/12 untuk membuat range IP address antara 172.16.0.0 sampai dengan 172.31.255.255. Pada bagian oktet pertama sebanyak 8 bit dan bagian oktet kedua hanya setengahnya sebanyak 4 bit karena 16 dari 32. Jumlahnya adalah 12 bit 

![alt text](https://github.com/Sandhika21/Jaringan-Komputer-D/blob/main/Praktikum1/Soal%205/5c.png)

---

## Soal 9
Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!

---

Display filter untuk paket yang berasal dari alamat 10.51.40.1 adalah `ip.src == 10.51.40.1`

Display filter untuk paket yang tidak menuju ke alamat 10.39.55.34 adalah `ip.dst != 10.39.55.34`

Untuk menyelesaikan soal dengan menggabungkan keduanya dengan logical operator && sehingga menjadi `ip.src == 10.51.40.1 &&  ip.dst != 10.39.55.34`

![alt text](https://github.com/Sandhika21/Jaringan-Komputer-D/blob/main/Praktikum1/Soal%209.png)

---
