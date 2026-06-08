# Meteor Panic! — 2D Retro Space Shooter

Selamat datang di repositori resmi **Meteor Panic!**, sebuah game *arcade space shooter* 2D klasik bergaya retro yang dikembangkan menggunakan **Unity 6**. Proyek ini dirancang khusus untuk memenuhi tugas besar mata pelajaran Produktif PPLG (Pengembangan Perangkat Lunak dan Gim) oleh siswa kelas XI PPLG 5 SMK Telkom Purwokerto.

Game ini menantang pemain untuk mengendalikan pesawat roket di luar angkasa dan bertahan hidup dari hujan meteor yang semakin agresif seiring meningkatnya level permainan.

---

## 🚀 Profil Developer
* **Nama:** Prabowo Adi Sanjaya
* **Kelas:** XI PPLG 5
* **Jurusan:** Pengembangan Perangkat Lunak dan Gim (PPLG)
* **Institusi:** SMK Telkom Purwokerto
* **Guru Pengampu:** Bu Firda S.Kom

---

## 🎮 Fitur Utama Game

1.  **Sistem Leveling & Difficulty Scaling (3 Tingkat Kesulitan)**
    Game ini memiliki 3 level dengan mekanik intensitas yang meningkat secara otomatis:
    * **Level 1 (Pemanasan):** Waktu bertahan 30 detik, jeda *spawn* meteor berkisar antara 0.5 hingga 2.0 detik.
    * **Level 2 (Keringetan):** Waktu bertahan 45 detik, jeda *spawn* meteor diperketat menjadi 0.4 hingga 1.2 detik.
    * **Level 3 (Super Gila / Final):** Waktu bertahan 60 detik, hujan meteor brutal dengan jeda *spawn* super rapat yaitu 0.2 hingga 0.7 detik.

2.  **Sistem Nyawa & UI Health Container**
    Pemain dibekali dengan **3 poin nyawa** yang diwakili oleh ikon hati pixel art di pojok kiri atas layar. Setiap kali roket menabrak meteor, nyawa berkurang satu dan ikon hati akan padam secara runtut melalui sistem *array image component*.

3.  **Mekanik Pembekuan Waktu (Pause Menu System)**
    Fitur interaktif menggunakan tombol `ESC` untuk memicu `PauseManager`. Menggunakan manipulasi runtime `Time.timeScale = 0f` untuk membekukan seluruh pergerakan objek (*freeze*) dan memunculkan panel UI *Pause* secara *seamless*, serta mengembalikannya ke `Time.timeScale = 1f` untuk melanjutkan permainan.

4.  **Audio & Ambient Imersif**
    Integrasi *backsound* retro berformat `.mp3` (`backsoundgame.mp3`) yang berjalan secara otomatis sejak scene dimulai (*Play On Awake*) dan diatur berputar tanpa putus (*Looping*) dengan penyesuaian volume linear (0.3) agar tidak merusak kenyamanan audio pemain.

5.  **State Management (Win/Loss UI)**
    * **PanelGameOver:** Muncul seketika saat nyawa habis (0), mematikan *spawner*, dan membersihkan sisa meteor di layar.
    * **PanelLevelClear:** Muncul otomatis saat *timer* hitung mundur mencapai angka 0, memberikan opsi untuk transisi ke level berikutnya secara berurutan hingga kembali ke `MainMenu` pada level akhir.

---

## 🛠️ Spesifikasi Teknis & Aset

* **Game Engine:** Unity 6 LTS (6000.3.3f1)
* **Bahasa Pemrograman:** C# (C-Sharp)
* **Render Pipeline:** Universal Render Pipeline (URP)
* **UI System:** Unity TextMeshPro (TMP) untuk font bergaya pixel art tajam.
* **Aset Grafis & Audio:** Modifikasi aset luar angkasa retro gratis dari *Kenney.nl* dengan konfigurasi tekstur *Point (No Filter)* untuk menjaga estetika pixel tetap padat dan tidak buram.

---

## 🎹 Kontrol Permainan

| Tombol Keyboard | Aksi / Fungsi |
| :--- | :--- |
| **W / Panah Atas** | Menggerakkan Roket ke Atas |
| **S / Panah Bawah** | Menggerakkan Roket ke Bawah |
| **A / Panah Kiri** | Menggerakkan Roket ke Kiri |
| **D / Panah Kanan** | Menggerakkan Roket ke Kanan |
| **ESC** | Membuka / Menutup Pause Menu (Freeze Game) |

---

## ⚙️ Struktur Arsitektur Kode (C# Scripts)

Proyek ini dibangun di atas fondasi tiga script utama yang saling berkomunikasi:

1.  **`PlayerController.cs`**
    Mengatur pergerakan transform roket berdasarkan input horizontal/vertical aksis serta mendeteksi *trigger collision* dengan objek ber-tag `"Meteor"`.
2.  **`GameManager.cs`**
    Otak utama permainan yang mengelola siklus hidup game (*game loop*), menghitung mundur waktu bermain, melacak sisa nyawa, mematikan komponen objek saat kalah/menang, dan menampilkan UI panel yang sesuai.
3.  **`PauseManager.cs`**
    Script khusus yang menangkap input `KeyCode.Escape` secara global untuk menghentikan kalkulasi fisika runtime dan memunculkan opsi menu navigasi kembali ke `MainMenu`.

---

## 📂 Cara Menjalankan Game (Build Version)

1.  Unduh folder hasil build ekstraksi bernama `Build_MeteorPanic_Prabowo`.
2.  Buka folder tersebut dan cari file eksekusi utama bernama **`Meteor Panic.exe`**.
3.  Klik dua kali pada file `.exe` tersebut.
4.  Game akan langsung berjalan secara mandiri tanpa memerlukan instalasi Unity Editor.
