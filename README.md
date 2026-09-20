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

<br/>

Bukti di Wireshark<br/>
Isolasi DISCOVER<br/>
<img width="1136" height="1017" alt="image" src="https://github.com/user-attachments/assets/e80b2d76-967c-4d82-9f84-70e1cac9bbf8" /><br/>
Cek jumlah MAC address unik (bukti spoofing)
<img width="1147" height="905" alt="image" src="https://github.com/user-attachments/assets/9edb21d5-0272-447b-b41c-83cf2845e994" /><br/>
Isolasi OFFER<br/>
<img width="1135" height="1015" alt="image" src="https://github.com/user-attachments/assets/df9581a7-e00a-47a9-bb8f-f2335cfc9abb" /><br/><br/>

#### 5. Temuan
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

