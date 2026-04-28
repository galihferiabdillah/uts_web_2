# uts_web_2

PENJELASAN TENTANG ANALISIS KERENTANAN SQL IJECTION PADA AUNTENTIKAASI APLIAKSI WEB:EKPRIMEN DAN MITIGASI 

Secara teknis, artikel tersebut menjelaskan bagaimana sebuah kesalahan dalam penulisan kode (kodingan) dapat menyebabkan keamanan aplikasi web runtuh. Berikut adalah rinciannya:

1. Masalah Utama: Kueri SQL yang Tidak Aman
   
Artikel menjelaskan bahwa file PHP yang kamu buat (misalnya untuk halaman login atau pencarian) memiliki celah karena menggabungkan input dari pengguna langsung ke dalam perintah database.

Contoh Kodingan Rentan: SELECT * FROM akun_pengguna WHERE username = '$username'.

Karena variabel $username langsung diambil dari apa yang diketik user tanpa diperiksa, sistem jadi bisa "ditipu".

2. Cara Kerja Serangan (Exploitation)

Penulis menunjukkan bahwa dengan mengetik kode khusus atau payload seperti ' OR '1'='1, logika database akan berubah.

Logika Normal: Mencari user yang namanya sesuai.

Logika Setelah Diserang: Mencari user yang namanya sesuai ATAU jika 1 sama dengan 1.

Karena "1=1" itu selalu benar, database akan menganggap perintah tersebut valid dan memberikan akses masuk (pada kasus login) atau menampilkan semua data (pada kasus inventaris), meskipun penyerang tidak tahu data aslinya.

3. Langkah Pembuktian (Eksperimen)
   
Di dalam dokumen, terdapat tautan yang mengarah ke langkah-langkah praktis yang dilakukan:

Persiapan Database: Membuat tabel di phpMyAdmin untuk menyimpan data contoh.

Pengujian: Memasukkan kode serangan ke dalam kotak input di browser untuk melihat apakah sistem akan bocor atau tidak.

4. Solusi (Mitigasi)
   
Ini adalah bagian terpenting untuk nilai UTS kamu. Artikel menyarankan penggunaan Prepared Statements atau Parameterized Queries.

Cara Kerjanya: Input dari pengguna tidak lagi dianggap sebagai "perintah" oleh database, melainkan hanya dianggap sebagai "teks biasa".

Dengan cara ini, meskipun penyerang mengetik ' OR '1'='1, database tidak akan menjalankannya sebagai perintah pencurian data.

Kesimpulan:

Artikel tersebut berfungsi sebagai laporan laboratorium yang menunjukkan bahwa keamanan sebuah website bukan hanya soal tampilan, tapi sangat bergantung pada cara kita menulis kode program agar tidak bisa dimanipulasi oleh input luar.

Apakah ada bagian teknis tertentu dari kodingan tersebut yang ingin kamu bahas lebih dalam?

