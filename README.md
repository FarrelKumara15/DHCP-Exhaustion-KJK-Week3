# DHCP-Exhaustion-KJK-Week3

|Nama|NRP|
|---|---|
|Farrel Arteya Kumara|5027251020|
|Reyhan Adi Satrio|5027251080|
|Dafa Ridho Zhafif|5027251129|

#### DHCP
DHCP Starvation adalah serangan terhadap server DHCP dengan permintaan discover berkali-kali menggunakan alamat IP dan MAC, serta transaction ID palsu. <br/>

Dampaknya, server akan mengira ada banyak klien atau perangkat baru yang mengakses server, lalu server akan mereservasi IP untuk setiap permintaan dari perangkat tersebut sampai pool-nya habis. <br/>

Sehingga, ketika perangkat asli ingin mengakses server, mereka akan kehabisan alamat IP dan terjadi denial of service. <br/>

Karena Pool sudah habis dan perangkat asli tidak mendapatkan alamat IP, maka biasanya penyerang akan melakukan DHCP Spoofing. <br/>

Situasi ketika penyerang menjalankan server DHCP palsu untuk mengelabui para pengguna dengan membagikan konfigurasi yang menyesatkan. <br/>

Dampaknya, trafik para pengguna akan melewati DNS atau Gateway milik penyerang terlebih dahulu yang mana ini berpotensi penyadapan, pemblokiran, dan mengarahkan ke halaman phishing. <br/><br/>

#### 4. Filter Wireshark 
|Filter|Kegunaan|
|---|---|
|'dhcp'|Menampilkan seluruh trafik DHCP|
|dhcp.option.dhcp == 1|Isolasi paket DHCPDISCOVER|
|dhcp.option.dhcp == 2|Isolasi paket DHCPOFFER|
|dhcp.option.dhcp == 5|Isolasi paket DHCPACK|
|dhcp.option.dhcp==1 && frame.time_relative>=3 && frame.time_relative<=7|Isolasi jendela waktu puncak serangan|
|eth.src == 00:1a:2b:0e:bc:83|Melacak MAC korban yang gagal mendapat IP|

<br/><br/>
#### Temuan
| Indikator | Temuan |
|---|---|
| Jenis serangan | DHCP Starvation / DHCP Exhaustion Attack |
| Total paket DHCP dianalisis | 410 |
| Durasi capture | 20.71 detik |
| Total DHCPDISCOVER | 257 |
| MAC address unik pengirim DISCOVER | 254 |
| Total DHCPOFFER | 51 |
| Total DHCPREQUEST | 51 |
| Total DHCPACK (IP ter-lease) | 51 |
| Alamat IP pool terpakai | 51 / 51 (100% habis) |
| Puncak intensitas serangan | Detik ke-5 (99 DISCOVER/detik) |
| Client gagal mendapat IP (korban potensial) | 203 |
| MAC korban terkonfirmasi (retry berulang) | 00:1a:2b:0e:bc:83 |

