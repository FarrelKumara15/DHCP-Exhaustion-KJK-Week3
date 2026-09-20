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

#### 1. Analisis 
