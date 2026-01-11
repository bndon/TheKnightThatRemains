#The Knight That Remains

The Knight That Remains adalah sebuah game 2D action platformer. Pemain mengendalikan seorang ksatria yang menjelajahi dungeon terkutuk dengan berbagai fitur utama, seperti sistem pertarungan (menyerang, bertahan, dan menghindar), kecerdasan buatan musuh (skeleton dan pertarungan boss), dialog interaktif, cutscene sinematik, serta sistem penyimpanan dan pemuatan permainan (save/load).

-----------------------------------------------------------------------------------------------------------------------------

Cara Menjalankan Aplikasi

Persyaratan Sistem
- Java Development Kit (JDK) versi 21 atau lebih baru
- Sistem operasi yang mendukung Java (Windows, macOS, atau Linux)

Langkah Menjalankan dari .jar
1. Pastikan Java Development Kit (JDK) versi 21 telah terpasang pada sistem.
2. Temukan file TheKnightThatRemains.jar.
3. Buka Command Prompt, Terminal, atau antarmuka baris perintah lain pada direktori tempat file berada.
4. Jalankan file .jar menggunakan Java Runtime Environment.
5. Setelah dijalankan, jendela game akan terbuka dan permainan akan dimulai secara otomatis.

Catatan Tambahan
- Jika aplikasi tidak dapat dijalankan, kemungkinan Java belum terpasang atau versi Java tidak sesuai.
- Aplikasi tidak memerlukan koneksi internet maupun pustaka eksternal tambahan.
- Game bersifat lintas platform dan dapat dijalankan pada berbagai sistem operasi yang mendukung Java.

Langkah Menjalankan dari Source Code
1. Pastikan Java Development Kit (JDK) versi 21 telah terpasang pada sistem.
2. Buka IDE Java yang digunakan.
3. Impor atau buka folder proyek The Knight That Remains sebagai proyek Java.
4. Pastikan struktur package dan file sumber berada pada direktori yang benar.
5. Cari kelas MainClass pada package main.
6. Jalankan metode main pada kelas MainClass.
7. Setelah dijalankan, jendela game akan terbuka dan permainan dimulai secara otomatis.

Catatan Tambahan
- Pastikan seluruh resource (gambar, tile map, dan file TMX) berada pada direktori yang sesuai agar dapat dimuat dengan benar.
- Tidak diperlukan pustaka eksternal tambahan di luar Java standar.
- Jika terjadi error saat kompilasi, pastikan pengaturan bahasa Java di IDE menggunakan versi Java 21.

-----------------------------------------------------------------------------------------------------------------------------

Daftar Kelas dan Fungsinya
- Package main
	- MainClass
		-Titik masuk (entry point) dari program.
	- Membuat objek Game dan menjalankan permainan.
-- Game
	- Pengendali utama aplikasi.
	- Menginisialisasi state game, manager, dan resource bersama.
	- Mengatur game loop (update dan render).
-- GamePanel
	- Turunan dari JPanel.
	- Bertanggung jawab untuk menggambar grafik dan menerima input.
	- Memanggil metode update dan render dari Game.
-- GameWindow
	- Membungkus JFrame.
	- Mengatur properti window (ukuran, judul, operasi penutupan).
	- Menambahkan GamePanel ke dalam window.
-- Gamestate (enum)
	- Mendefinisikan state permainan (MENU, PLAYING, PAUSED, dll.).
	- Digunakan untuk mengontrol alur permainan dan input.
-- Menu
	- Menangani logika dan tampilan menu utama.
	- Memproses input pengguna pada menu.
-- PauseOverlay
	- Menampilkan UI saat game dijeda.
	- Menangani interaksi ketika game dalam keadaan pause.

- Package inputs
-- KeyboardInputs
	- Menangani event input dari keyboard.
	- Menerjemahkan penekanan tombol menjadi aksi dalam game.
-- MouseInput
	- Menangani klik dan pergerakan mouse.
	- Digunakan terutama untuk interaksi UI (menu, tombol).

- Package entities
-- Entity (kelas dasar)
	- Merepresentasikan semua karakter yang dapat bergerak.
	- Menyimpan posisi, hitbox, health, dan logika pergerakan.
	- Menjadi kelas induk bagi Player dan Enemy.
-- Player
	- Turunan dari Entity.
	- Menangani pergerakan pemain, animasi, dan pertarungan.
	- Mengelola state pemain (idle, berjalan, menyerang, dll.).
-- Enemy
	- Turunan dari Entity.
	- Kelas dasar untuk semua musuh.
	- Menyediakan logika umum musuh (AI, damage, pergerakan).
-- Skeleton
	- Turunan dari Enemy.
	- Mengimplementasikan perilaku dan animasi khusus Skeleton.
-- KnightBoss
	- Turunan dari Enemy.
	- Musuh boss dengan pola serangan dan perilaku khusus.
-- EnemyManager
	- Mengelola semua musuh dalam level.
	- Melakukan update dan render musuh.
	- Menangani spawn dan penghapusan musuh.

- Package levels
-- Level
	- Merepresentasikan satu level permainan.
	- Menyimpan data tile, musuh, dan objek.
-- LevelManager
	- Memuat level dari file TMX.
	- Mengelola level yang sedang aktif.
	- Menyediakan data level untuk sistem lain (collision, render).

- Package objects
-- ObjectManager
	- Mengelola objek interaktif (item, jebakan, dll.).
	- Melakukan update dan render objek.
	- Menangani interaksi antara pemain dan objek.

- Package ui
-- CreditsOverlay
	- Menampilkan kredit aset dan pengembang.
-- DialogueOverlay
Menampilkan dialog di layar.
	- Digunakan untuk cerita atau interaksi NPC.
-- GameOverOverlay
	- Menampilkan layar game over.
	- Menangani input untuk restart atau keluar.
-- Menu
	- Menangani tampilan dan interaksi menu UI.
-- PauseOverlay
	- Overlay UI untuk kondisi pause.	

- Package utils
-- Constants
	- Menyimpan nilai konstanta statis.
	- Berisi ukuran tile, status pemain, dan parameter game lainnya.
-- HelpMethods
	- Kumpulan metode bantu.
	- Digunakan untuk collision detection dan perhitungan umum.
-- TMXLoader
	- Memuat map TMX (Tiled Map Editor).
	- Menangani parsing tileset dan data tile.
-- LoadSave
	- Memuat gambar dan resource dari penyimpanan
	- Memusatkan logika pemuatan aset.
	- Menyimpan save data dari player



2. Konsep OOP yang Digunakan
a. Enkapsulasi (Encapsulation)
	- Data seperti posisi, health, animasi, dan hitbox disembunyikan di dalam kelas.
	- Akses dilakukan melalui metode yang terkontrol.
	- Contoh: Player mengelola pergerakan dan animasinya sendiri.

b. Pewarisan (Inheritance)
- Entity berfungsi sebagai kelas induk.
- Player dan Enemy mewarisi Entity.
- Skeleton dan KnightBoss mewarisi Enemy.
- Mengurangi duplikasi kode dan membentuk hierarki yang jelas.

c. Polimorfisme (Polymorphism)
- Semua musuh diperlakukan sebagai Enemy.
- Setiap musuh dapat memiliki perilaku berbeda melalui override method.
- EnemyManager tidak perlu mengetahui detail implementasi tiap musuh.

d. Abstraksi (Abstraction)
- Logika tingkat tinggi tidak bergantung pada detail implementasi.
- Sistem kompleks seperti collision dan TMX loading disembunyikan dalam kelas utilitas.


Separation of Concerns (Tambahan Info)
- Logika game, rendering, input, dan loading data dipisahkan ke package berbeda.
- Mempermudah pemeliharaan dan pengembangan.

Penggunaan Enum
- Gamestate memastikan state game valid dan konsisten.
- Menghindari penggunaan string untuk pengaturan state.
