# Jarkom-Modul-4-D29-2023
| Nama           | NRP            |
| ---------------| ---------------|
| Christian Kevin Emor      | 5025211153      |
| Ferza Noveri     | 5025211097      |

Soal shift dikerjakan pada Cisco Packet Tracer dan GNS3 menggunakan metode perhitungan CLASSLESS yang berbeda.
Kelompok kami menggunakan perhitungan VLSM untuk CSP dan CIDR untuk GNS3

# Cisco Packet Tracer
langkah pertama yang dilakukan yaitu membuat topologi seperti yang diberikan oleh soal

![image](https://github.com/Chrstnkevin/Jarkom-Modul-4-D29-2023/assets/97864068/0126435e-45ad-4fad-9f68-ae2c4e82defb)

Setelah berhasil membuat topologi, selanjutnya akan dikelompokkan subnet yang ada dengan pembagian seperti berikut

![Group 19](https://github.com/Chrstnkevin/Jarkom-Modul-4-D29-2023/assets/97864068/749fdb5f-660f-4400-8c23-084f7b143822)

| Nama Subnet | Rute | Jumlah IP (Terbanyak ke Tersedikit) | Netmask |
|-------------|------|-------------------------------------|---------|
| A6          | Fern - Switch4 - LaubHills - Switch4 - AppetitRegion | 1023 | /21 |
| A3          | Flamme - Switch5 - RohrRoad | 1001 | /22 |
| A15         | Lugner - Switch10 - TurkRegion | 1001 | /22 |
| A21         | Heiter - Switch8 - Sein - Switch8 - RiegelCanyon | 512 | /22 |
| A18         | Linie - Switch11 - GranzChannel | 255 | /23 |
| A16         | Lugner - Switch9 - GrobeForest | 251 | /24 |
| A10         | Denken - Switch2 - RoyalCapital - Switch2 - WilleRegion | 127 | /24 |
| A20         | Lawine - Switch7 - BredtRegion - switch7 - heitter | 31 | /26 |
| A4          | Frieren - Switch3 - LakeKorridor | 25 | /27 |
| A8          | Himmel - Switch6 - SchwerMountains | 6 | /29 |
| A12         | Eisen - Switch1 - Richter - Switch1 - Revolte | 3 | /29 |
| A1          | Aura - Frieren | 2 | /30 |
| A2          | Frieren - Flamme | 2 | /30 |
| A5          | Flamme - Ferm | 2 | /30 |
| A7          | Flamme - Himmel | 2 | /30 |
| A11         | Aura - Eisen | 2 | /30 |
| A13         | Eisen - Switch0 - Stark | 2 | /30 |
| A14         | Eisen - Lugner | 2 | /30 |
| A17         | Eisen - Linie | 2 | /30 |
| A19         | Linie - Lawine | 2 | /30 |
| A9          | Aura - Denken | 2 | /30 |
| **Total**   |      | **4253** | **/19** |


Setelah mengetahui pembagian subnet serta mendapatkan Netmask yang diperlukan, langkah selanjutnya adalah membuat tree untuk mengetahui IP yang akan dimasukkan ke CPT

![Frame 32](https://github.com/Chrstnkevin/Jarkom-Modul-4-D29-2023/assets/97864068/8180ba44-b2ac-4224-b430-359b75615152)

Selanjutnya hitung NID dan Broadcast dan didapatkan hasil sebagai berikut

| Subnet | Network ID   | Netmask          | Broadcast      |
|--------|--------------|------------------|----------------|
| A6     | 10.36.0.0    | /21 (255.255.248.0) | 10.36.7.255    |
| A3     | 10.36.8.0    | /22 (255.255.252.0) | 10.36.11.255   |
| A15    | 10.36.12.0   | /22 (255.255.252.0) | 10.36.15.255   |
| A21    | 10.36.16.0   | /22 (255.255.252.0) | 10.36.19.255   |
| A18    | 10.36.20.0   | /23 (255.255.254.0) | 10.36.21.255   |
| A16    | 10.36.22.0   | /24 (255.255.255.0) | 10.36.22.255   |
| A10    | 10.36.23.0   | /24 (255.255.255.0) | 10.36.23.255   |
| A20    | 10.36.24.0   | /26 (255.255.255.192) | 10.36.24.63    |
| A4     | 10.36.24.64  | /27 (255.255.255.224) | 10.36.24.95    |
| A8     | 10.36.24.96  | /29 (255.255.255.248) | 10.36.24.103   |
| A12    | 10.36.24.104 | /29 (255.255.255.248) | 10.36.24.111   |
| A1     | 10.36.24.112 | /30 (255.255.255.252) | 10.36.24.115   |
| A2     | 10.36.24.116 | /30 (255.255.255.252) | 10.36.24.119   |
| A5     | 10.36.24.120 | /30 (255.255.255.252) | 10.36.24.123   |
| A7     | 10.36.24.124 | /30 (255.255.255.252) | 10.36.24.127   |
| A11    | 10.36.24.128 | /30 (255.255.255.252) | 10.36.24.131   |
| A13    | 10.36.24.132 | /30 (255.255.255.252) | 10.36.24.135   |
| A14    | 10.36.24.136 | /30 (255.255.255.252) | 10.36.24.139   |
| A17    | 10.36.24.140 | /30 (255.255.255.252) | 10.36.24.143   |
| A19    | 10.36.24.144 | /30 (255.255.255.252) | 10.36.24.147   |
| A9     | 10.36.24.148 | /30 (255.255.255.252) | 10.36.24.151   |

Setelah mendapatkan semua yang dibutuhkan, langkah selanjutnya yaitu melakukan konfigurasi pada router CPT

| Router  | Interface | IPV4          | Subnet Mask         | Tujuan     |
|---------|-----------|---------------|---------------------|------------|
| **Aura**| FE 0/1    | 10.36.24.149  | 255.255.255.252     | Denken     |
|         | FE 1/0    | 10.36.24.129  | 255.255.255.252     | Eisen      |
|         | FE 1/1    | 10.36.24.113  | 255.255.255.252     | Frieren    |
|         |           |               |                     |            |
| **Frieren** | FE 0/0    | 10.36.24.65   | 255.255.255.224 | Switch     |
|         | FE 0/1    | 10.36.24.117  | 255.255.255.252     | Flamme     |
|         | FE 1/0    | 10.36.24.114  | 255.255.255.252     | Aura       |
|         |           |               |                     |            |
| **Flamme** | FE 0/0    | 10.36.24.118  | 255.255.255.252     | Frieren    |
|         | FE 0/1    | 10.36.24.121  | 255.255.255.252     | Fern       |
|         | E 1/0     | 10.36.24.125  | 255.255.255.252     | Himmel     |
|         | E 1/1     | 10.36.8.1     | 255.255.252.0       | Switch     |
|         |           |               |                     |            |
| **Fern** | FE 0/0    | 10.36.24.122  | 255.255.255.252     | Flamme     |
|         | FE 0/1    | 10.36.0.1     | 255.255.248.0       | Switch     |
|         |           |               |                     |            |
| **Himmel** | FE 0/0  | 10.36.24.97   | 255.255.255.248     | Switch     |
|         | FE 0/1    | 10.36.24.126  | 255.255.255.252     | Flamme     |
|         |           |               |                     |            |
| **Denken** | FE 0/0  | 10.36.24.150  | 255.255.255.252     | Aura       |
|         | FE 0/1    | 10.36.23.1    | 255.255.255.0       | Switch     |
|         |           |               |                     |            |
| **Eisen** | FE 0/0   | 10.36.24.133  | 255.255.255.252     | Switch 0   |
|         | FE 0/1    | 10.36.24.137  | 255.255.255.252     | Lugner     |
|         | E 1/0     | 10.36.24.130  | 255.255.255.252     | Aura       |
|         | E 1/1     | 10.36.24.141  | 255.255.255.252     | Linie      |
|         | E 1/2     | 10.36.24.105  | 255.255.255.248     | Switch 1   |
|         |           |               |                     |            |
| **Lugner** | FE 0/0  | 10.36.24.138  | 255.255.255.252     | Eisen      |
|         | FE 0/1    | 10.36.12.1    | 255.255.252.0       | Switch 10  |
|         | E 1/0     | 10.36.22.1    | 255.255.255.0       | Switch 9   |
|         |           |               |                     |            |
| **Linie** | FE 0/0   | 10.36.20.1    | 255.255.254.0       | Switch 11  |
|         | FE 0/1    | 10.36.24.145  | 255.255.255.252     | Lawine     |
|         | FE 1/0    | 10.36.24.142  | 255.255.255.252     | Eisen      |
|         |           |               |                     |            |
| **Lawine** | FE 0/0 | 10.36.24.1    | 255.255.255.192     | Switch     |
|         | FE 0/1    | 10.36.24.146  | 255.255.255.252     | Linie      |
|         |           |               |                     |            |
| **Heiter** | FE 0/0 | 10.36.16.1    | 255.255.252.0       | Switch     |
|         | FE 0/1    | 10.36.24.3    | 255.255.255.192     | Switch 7   |

untuk cara melakukannya adalah sebagai berikut:
1. Masuk kesalah satu router yang ingin di setting (Ex: Aura)

   ![image](https://github.com/Chrstnkevin/Jarkom-Modul-4-D29-2023/assets/97864068/ebc910a8-13d4-4401-b73c-fcf008d0a248)

2. Pada Interface, masukkan IPv4 serta netmask yang telah diperoleh

   ![image](https://github.com/Chrstnkevin/Jarkom-Modul-4-D29-2023/assets/97864068/fb2dad3e-3249-4ea6-9566-ecaea5c91da5)

3. Setelah selesai, ulangi hal yang sama terhadap semua router

Setelah router berhasil disettiing semua langkah selanjutnya yaitu melakukan setting di client/server

| Client/Server  | DefGateway   | Router  | IPv4         | Subnet Mask       |
|----------------|--------------|---------|--------------|-------------------|
| **LakeKorridor** | 10.36.24.65  | Frieren | 10.36.24.66 | 255.255.255.224  |
|                |              |         |              |                   |
| **RohrRoad**    | 10.36.8.1    | Flamme  | 10.36.8.2   | 255.255.252.0    |
|                |              |         |              |                   |
| **LaubHills**   | 10.36.0.1    | Fern    | 10.36.0.2   | 255.255.248.0    |
| **AppetitRegion**|             | Fern    | 10.36.0.3   | 255.255.248.0    |
|                |              |         |              |                   |
| **SchwerMountains** | 10.36.24.97 | Himmel  | 10.36.24.98 | 255.255.255.248  |
|                |              |         |              |                   |
| **RoyalCapital** | 10.36.23.1   | Denken  | 10.36.23.2  | 255.255.255.0    |
| **WilleRegion**  |             | Denken  | 10.36.23.3  | 255.255.255.0    |
|                |              |         |              |                   |
| **Richter**     | 10.36.24.105 | Eisen   | 10.36.24.106| 255.255.255.248  |
| **Revolter**    |              | Eisen   | 10.36.24.107| 255.255.255.248  |
|                |              |         |              |                   |
| **Stark**       | 10.36.24.133 | Eisen   | 10.36.24.134| 255.255.255.252  |
|                |              |         |              |                   |
| **TurkRegion**  | 10.36.12.1   | Lugner  | 10.36.12.2  | 255.255.252.0    |
| **GrobeForest** | 10.36.22.1   |         | 10.36.22.2  | 255.255.255.0    |
|                |              |         |              |                   |
| **GranzChannel**| 10.36.20.1   | Linie   | 10.36.20.2  | 255.255.254.0    |
|                |              |         |              |                   |
| **BredtRegion** | 10.36.24.1   | Lawine  | 10.36.24.2  | 255.255.255.192  |
|                |              |         |              |                   |
| **Sein**       | 10.36.16.1   | Heiter  | 10.36.16.2  | 255.255.252.0    |
| **RiegelCanyon**| 10.36.16.1  |         | 10.36.16.3  | 255.255.252.0    |

cara melakukan konfigurasi di client/server yaitu buka client yang dituju -> Desktop -> IP Configuration -> masukkan ip yang didapatkan
![image](https://github.com/Chrstnkevin/Jarkom-Modul-4-D29-2023/assets/97864068/d80dcb9b-0dfe-400c-ab24-a71e7fd9793e)





# GNS3
langkah pertama yang harus dilakukan adalah melakukan subnetting.

### Penggabungan Pertama
![1](https://github.com/Chrstnkevin/Jarkom-Modul-4-D29-2023/assets/110340182/d5fa5218-3613-414e-aed2-e0f192f30753)

### Penggabungan Kedua
![2](https://github.com/Chrstnkevin/Jarkom-Modul-4-D29-2023/assets/110340182/89f8daaa-b45c-49e6-b0f4-914d7d5727ee)

### Penggabungan Ketiga
![3](https://github.com/Chrstnkevin/Jarkom-Modul-4-D29-2023/assets/110340182/12200854-0bb8-4943-8028-c09ed43cb204)

### Penggabungan Keempat
![4](https://github.com/Chrstnkevin/Jarkom-Modul-4-D29-2023/assets/110340182/727e811e-60f5-4d2c-b29c-e5619ed36ad8)

### Penggabungan Kelima
![5](https://github.com/Chrstnkevin/Jarkom-Modul-4-D29-2023/assets/110340182/e8f318f6-3c0f-40e0-918e-2c7b7c5813a8)

### Penggabungan Keenam
![6](https://github.com/Chrstnkevin/Jarkom-Modul-4-D29-2023/assets/110340182/86545f4f-a7a7-490e-acf6-da14915d9e8a)

### Penggabungan Ketujuh
![7](https://github.com/Chrstnkevin/Jarkom-Modul-4-D29-2023/assets/110340182/dafc4a1c-6dd1-45fe-8cf1-bfd4cc5629e4)

### Penggabungan Kedelapan
![8](https://github.com/Chrstnkevin/Jarkom-Modul-4-D29-2023/assets/110340182/6eabd3d3-7450-40cc-bb3f-f0c5bb786ccc)

### Penggabungan Kesembilan
![9](https://github.com/Chrstnkevin/Jarkom-Modul-4-D29-2023/assets/110340182/f0fa5a9c-008b-4485-8779-b9f2eba81ff2)

### TREE
<img width="1272" alt="TREE" src="https://github.com/Chrstnkevin/Jarkom-Modul-4-D29-2023/assets/110340182/760ba2dd-8e1f-42af-908d-799fa72a8719">























