# The Knight That Remains

**The Knight That Remains** adalah sebuah game **2D action platformer**.  
Pemain mengendalikan seorang ksatria yang menjelajahi dungeon terkutuk dengan berbagai fitur utama, antara lain:
- Sistem pertarungan (menyerang, bertahan, dan menghindar)
- Kecerdasan buatan musuh (Skeleton dan pertarungan Boss)
- Dialog interaktif
- Cutscene sinematik
- Sistem penyimpanan dan pemuatan permainan (Save & Load)

---

## Cara Menjalankan Aplikasi

### Persyaratan Sistem
- Java Development Kit (JDK) versi **21** atau lebih baru
- Sistem operasi yang mendukung Java:
  - Windows
  - macOS
  - Linux

---

### Menjalankan dari File `.jar`

1. Pastikan **Java Development Kit (JDK) versi 21** telah terpasang.
2. Temukan file `TheKnightThatRemains.jar`.
3. Buka **Command Prompt**, **Terminal**, atau antarmuka baris perintah lainnya.
4. Masuk ke direktori tempat file `.jar` berada.
5. Jalankan file `.jar` menggunakan Java Runtime Environment.
6. Setelah dijalankan, jendela game akan terbuka dan permainan dimulai secara otomatis.

#### Catatan Tambahan
- Jika aplikasi tidak dapat dijalankan, kemungkinan Java belum terpasang atau versinya tidak sesuai.
- Aplikasi tidak memerlukan koneksi internet.
- Tidak diperlukan pustaka eksternal tambahan.
- Game bersifat lintas platform selama sistem mendukung Java.

---

### Menjalankan dari Source Code

1. Pastikan **Java Development Kit (JDK) versi 21** telah terpasang.
2. Buka IDE Java yang digunakan (IntelliJ IDEA, Eclipse, NetBeans, dll.).
3. Impor atau buka folder proyek **The Knight That Remains** sebagai proyek Java.
4. Pastikan struktur package dan file sumber berada pada direktori yang benar.
5. Cari kelas `MainClass` pada package `main`.
6. Jalankan metode `main()` pada kelas tersebut.
7. Game akan berjalan dan menampilkan jendela permainan secara otomatis.

#### Catatan Tambahan
- Pastikan seluruh resource (gambar, tileset, dan file TMX) berada pada direktori yang sesuai.
- Tidak diperlukan pustaka eksternal di luar Java standar.
- Jika terjadi error kompilasi, pastikan versi Java di IDE adalah Java 21.

---

## Daftar Kelas dan Fungsinya

### Package `main`

- **MainClass**
  - Titik masuk (entry point) aplikasi
  - Membuat objek `Game` dan menjalankan permainan

- **Game**
  - Pengendali utama aplikasi
  - Menginisialisasi state game, manager, dan resource
  - Mengatur game loop (update dan render)

- **GamePanel**
  - Turunan dari `JPanel`
  - Bertanggung jawab untuk rendering dan input
  - Memanggil metode update dan render dari `Game`

- **GameWindow**
  - Membungkus `JFrame`
  - Mengatur ukuran, judul, dan operasi penutupan window
  - Menambahkan `GamePanel` ke dalam window

- **Gamestate (Enum)**
  - Mendefinisikan state permainan (MENU, PLAYING, PAUSED, dll.)
  - Mengontrol alur permainan dan input

- **Menu**
  - Menangani logika dan tampilan menu utama
  - Memproses input pengguna

- **PauseOverlay**
  - Menampilkan UI saat game dijeda
  - Menangani interaksi ketika pause

---

### Package `inputs`

- **KeyboardInputs**
  - Menangani event input keyboard
  - Menerjemahkan input menjadi aksi dalam game

- **MouseInput**
  - Menangani klik dan pergerakan mouse
  - Digunakan untuk navigasi UI

---

### Package `entities`

- **Entity** (kelas dasar)
  - Merepresentasikan semua karakter yang dapat bergerak
  - Menyimpan posisi, hitbox, health, dan logika pergerakan

- **Player**
  - Turunan dari `Entity`
  - Menangani pergerakan, animasi, dan pertarungan pemain

- **Enemy**
  - Turunan dari `Entity`
  - Kelas dasar semua musuh
  - Menyediakan logika umum AI dan damage

- **Skeleton**
  - Turunan dari `Enemy`
  - Musuh dengan perilaku dan animasi khusus

- **KnightBoss**
  - Turunan dari `Enemy`
  - Musuh boss dengan pola serangan khusus

- **EnemyManager**
  - Mengelola semua musuh dalam level
  - Update, render, spawn, dan penghapusan musuh

---

### Package `levels`

- **Level**
  - Merepresentasikan satu level permainan
  - Menyimpan data tile, musuh, dan objek

- **LevelManager**
  - Memuat level dari file TMX
  - Mengelola level aktif
  - Menyediakan data collision dan render

---

### Package `objects`

- **ObjectManager**
  - Mengelola objek interaktif (item, jebakan, dll.)
  - Update dan render objek
  - Menangani interaksi dengan player

---

### Package `ui`

- **CreditsOverlay**
  - Menampilkan kredit aset dan pengembang

- **DialogueOverlay**
  - Menampilkan dialog di layar
  - Digunakan untuk cerita dan interaksi NPC

- **GameOverOverlay**
  - Menampilkan layar game over
  - Menangani restart atau keluar

- **Menu**
  - Menangani tampilan dan navigasi menu UI

- **PauseOverlay**
  - Overlay UI saat game dijeda

---

### Package `utils`

- **Constants**
  - Menyimpan nilai konstanta statis
  - Ukuran tile, status player, dan parameter game

- **HelpMethods**
  - Kumpulan metode bantu
  - Digunakan untuk collision detection dan perhitungan umum

- **TMXLoader**
  - Memuat map TMX (Tiled Map Editor)
  - Parsing tileset dan data tile

- **LoadSave**
  - Memuat resource dari penyimpanan
  - Menyimpan dan memuat data save game
  - Menyimpan health player dan checkpoint

---

## Konsep OOP yang Digunakan

### Enkapsulasi (Encapsulation)
- Data seperti posisi, health, animasi, dan hitbox disembunyikan dalam kelas
- Akses dilakukan melalui metode yang terkontrol
- Contoh: `Player` mengelola pergerakan dan animasinya sendiri

### Pewarisan (Inheritance)
- `Entity` sebagai kelas induk
- `Player` dan `Enemy` mewarisi `Entity`
- `Skeleton` dan `KnightBoss` mewarisi `Enemy`

### Polimorfisme (Polymorphism)
- Semua musuh diperlakukan sebagai `Enemy`
- Perilaku berbeda diimplementasikan melalui method override
- `EnemyManager` tidak bergantung pada detail tiap musuh

### Abstraksi (Abstraction)
- Logika tingkat tinggi tidak bergantung pada detail implementasi
- Sistem kompleks seperti collision dan TMX loading disembunyikan dalam kelas utilitas

### Separation of Concerns
- Logika game, rendering, input, dan loading data dipisahkan ke package berbeda
- Mempermudah pemeliharaan dan pengembangan

### Penggunaan Enum
- `Gamestate` memastikan state game valid dan konsisten
- Menghindari penggunaan string untuk pengaturan state
