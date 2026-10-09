# Modul Git & GitHub: Panduan Praktis Version Control & Kolaborasi Tim

Selamat datang di **Modul Git & GitHub: Panduan Praktis untuk Kolaborasi Kode**! Modul ini dirancang untuk membekali Anda dengan keterampilan fundamental dalam mengelola versi kode (*Version Control System*), bekerja dengan percabangan (*branching*), mengatasi konflik kode (*merge conflict*), hingga berkolaborasi dalam tim menggunakan GitHub melalui alur kerja industri modern.

---

## 1. Tujuan Praktikum
Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:
1. Memahami perbedaan mendasar antara **Git** (alat lokal) dan **GitHub** (layanan kolaborasi cloud).
2. Memahami konsep tiga area kerja Git: *Working Directory*, *Staging Area*, dan *Local Repository*.
3. Melakukan inisialisasi repositori, pelacakan berkas, *staging*, dan perekaman riwayat (*commit*).
4. Memeriksa status dan perbedaan baris kode (*diff*) serta menavigasi riwayat perubahan (*log*, *checkout*, *reset*, *revert*).
5. Mengelola cabang (*branch*), melakukan penggabungan (*merge*), dan menyelesaikan konflik kode (*merge conflict*).
6. Menghubungkan repositori lokal ke repositori jarak jauh (*remote repository*) di GitHub (`push`, `pull`, `clone`).
7. Memahami siklus kolaborasi profesional menggunakan *Fork*, *Branch*, dan *Pull Request (PR)*.
8. Menerapkan alur kerja harian developer (*Daily Git Workflow*) dan praktik terbaik (*best practices*) penulisan commit.

---

## 2. Teori Dasar

### 2.1 Apa Itu Git dan GitHub?

```
+-------------------------------------------------------+
|  GIT (Local Machine)                                  |
|  - Sistem Kontrol Versi Terdistribusi (DVCS)          |
|  - Bekerja secara luring (offline) di komputer Anda   |
|  - Melacak setiap baris riwayat perubahan berkas      |
+-------------------------------------------------------+
                           |
                     git push / pull
                           v
+-------------------------------------------------------+
|  GITHUB (Cloud Platform)                              |
|  - Layanan hosting daring untuk repositori Git        |
|  - Tempat kolaborasi tim (Pull Requests, Code Review) |
|  - Portofolio publik & automasi CI/CD                 |
+-------------------------------------------------------+
```

* **Git**: Alat/perangkat lunak *Version Control System* (VCS) terdistribusi yang berjalan di komputer lokal untuk melacak perubahan berkas, memungkinkan kita kembali ke versi masa lalu (*time-travel*), dan memfasilitasi penggabungan kode tanpa saling menimpa.
* **GitHub**: Platform berbasis web milik Microsoft yang menjadi tempat menyimpan repositori Git di cloud, memungkinkan kolaborasi multi-developer, pelacakan isu (*issues*), dan pengajuan kontribusi kode (*Pull Requests*).

---

### 2.2 Tiga Area Kerja Git (The Three Trees)
Git mengelola berkas dalam tiga status lingkungan:

```
+--------------------+       git add       +--------------------+      git commit      +--------------------+
| WORKING DIRECTORY  |  ---------------->  |    STAGING AREA    |  ----------------->  |  LOCAL REPOSITORY  |
| (Folder Proyek     |                     |   (Ruang Tunggu    |                      |   (.git database   |
|  tempat mengedit)  |  <----------------  |  Persiapan Commit) |  <-----------------  |  snapshot riwayat) |
+--------------------+      git restore    +--------------------+       git reset      +--------------------+
```

1. **Working Directory (Ruang Kerja)**: Direktori fisik tempat Anda membuat, mengedit, atau menghapus berkas kode.
2. **Staging Area / Index (Ruang Persiapan)**: Area perantara tempat berkas didaftarkan sebelum disimpan permanen. Anda dapat memilih berkas mana saja yang sudah siap dimasukkan ke commit berikutnya.
3. **Local Repository (.git)**: Basis data lokal tempat Git menyimpan snapshot riwayat proyek secara permanen bersama metadata pengarang, waktu, dan pesan commit.

---

### 2.3 Perintah Dasar Penyimpanan

| Perintah | Deskripsi Fungsi |
| :--- | :--- |
| `git init` | Menginisialisasi folder biasa menjadi repositori Git lokal (membuat folder tersembunyi `.git`). |
| `git status` | Melihat kondisi berkas saat ini (apakah *Untracked*, *Modified*, atau *Staged*). |
| `git add <nama-file>` | Memindahkan berkas tertentu dari *Working Directory* ke *Staging Area*. |
| `git add .` | Memindahkan seluruh berkas baru dan berkas yang dimodifikasi ke *Staging Area*. |
| `git commit -m "pesan"` | Menyimpan permanen seluruh berkas di *Staging Area* sebagai riwayat (*commit* baru). |

---

### 2.4 Memeriksa Perubahan dan Navigasi Riwayat

#### 1. Memeriksa Riwayat & Perbedaan Baris
* **`git log`**: Menampilkan daftar riwayat commit (Hash ID, Author, Tanggal, dan Pesan).
  * Opsi praktis: `git log --oneline --graph --decorate`
* **`git diff`**: Memeriksa perubahan baris per baris yang belum di-stage (warna merah `-` untuk baris terhapus, hijau `+` untuk baris baru).
* **`git diff --staged`**: Memeriksa perubahan baris yang sudah berada di Staging Area.

#### 2. Navigasi & Pembatalan Riwayat (Time Travel)
* **`git checkout <commit-hash>`**: Berpindah sementara untuk melihat kondisi kode di titik masa lampau tertentu (*detached HEAD*).
* **`git revert <commit-hash>`**: Membatalkan perubahan dari commit tertentu dengan **membuat commit baru yang membalikkan efeknya**. Sangat aman digunakan pada branch publik/kolaborasi tim.
* **`git reset`**: Menggeser pointer HEAD ke commit sebelumnya:
  * `--soft`: Membatalkan commit, namun kode yang diubah tetap berada di Staging Area.
  * `--mixed` (default): Membatalkan commit dan unstage, kode tetap ada di Working Directory.
  * `--hard`: **Perhatian!** Menghapus seluruh commit dan mengembalikan berkas ke titik sebelumnya secara permanen.

---

### 2.5 Bekerja dengan Percabangan (Branching)

**Mengapa Branch Sangat Penting?**
Percabangan memungkinkan pengembang mengerjakan fitur baru atau eksperimen secara terisolasi tanpa mengacaukan kode utama (`main`) yang sedang stabil di lingkungan produksi.

```
       (fitur-navbar)  [Commit A] ---> [Commit B]
                            /                         \ (git merge)
                           /                           v
(main) [Commit 1] ----> [Commit 2] ----------------> [Commit 3]
```

* **`git branch`**: Melihat daftar cabang yang ada di repositori lokal.
* **`git branch <nama-branch>`**: Membuat cabang baru tanpa langsung berpindah.
* **`git checkout <nama-branch>`** atau **`git switch <nama-branch>`**: Berpindah ke cabang yang dituju.
* **`git checkout -b <nama-branch>`**: Membuat cabang baru sekaligus langsung berpindah ke cabang tersebut.
* **`git merge <nama-branch>`**: Menggabungkan perubahan dari cabang target ke cabang aktif saat ini.
* **`git branch -d <nama-branch>`**: Menghapus cabang lokal yang sudah selesai digabungkan.

---

### 2.6 Mengatasi Konflik Penggabungan (Merge Conflict)

Konflik terjadi apabila dua cabang yang berbeda mengubah **baris kode yang sama persis** pada berkas yang sama, lalu digabungkan (*merge*). Git tidak dapat menebak kode mana yang benar sehingga memerlukan keputusan manusia.

Saat konflik terjadi, Git akan menyisipkan penanda konflik pada berkas:

```html
<<<<<<< HEAD
<h1>Portofolio Milik Budi Santoso</h1>
=======
<h1>Portofolio Resmi Budi - Web Developer</h1>
>>>>>>> feature-title
```

* `<<<<<<< HEAD`: Kode versi cabang aktif saat ini.
* `=======`: Garis pemisah antara kedua versi.
* `>>>>>>> feature-title`: Kode versi cabang yang sedang digabungkan masuk.

**Langkah Menyelesaikan Konflik:**
1. Buka berkas yang berkonflik di VS Code.
2. Diskusikan dan pilih kode yang benar (atau gunakan tombol *Accept Current Change*, *Accept Incoming Change*, atau *Accept Both Changes* di editor).
3. Hapus seluruh tanda `<<<<<<<`, `=======`, dan `>>>>>>>`.
4. Simpan berkas tersebut.
5. Jalankan perintah `git add <berkas>` lalu `git commit -m "fix: resolve merge conflict on index.html"`.

---

### 2.7 Terhubung dengan Repositori Jarak Jauh (GitHub Remote)

```bash
# Menautkan repositori lokal ke GitHub
git remote add origin https://github.com/username/nama-repo.git

# Mengubah nama default branch menjadi main
git branch -M main

# Mengunggah commit lokal ke GitHub pertama kali
git push -u origin main

# Mengambil dan menggabungkan perubahan terbaru dari GitHub
git pull origin main

# Mengunduh salinan repositori publik yang sudah ada di internet ke komputer
git clone https://github.com/username/nama-repo.git
```

---

### 2.8 Alur Kerja Kolaborasi (Fork, Clone, Pull Request)

```
[Repositori Asli / Organisasi]
            |
            | (Fork via web GitHub)
            v
[Fork Repositori di Akun Anda]
            |
            | (git clone ke lokal)
            v
[Komputer Lokal Pengembang]
            |
            | (git checkout -b feature/fitur-baru)
            | (git add . && git commit -m "...")
            | (git push origin feature/fitur-baru)
            v
[Fork Repositori di Akun Anda]
            |
            | (Buat Pull Request / PR)
            v
[Review Kode & Merge ke Repositori Asli]
```

1. **Fork**: Membuat duplikat repositori orang lain ke akun GitHub pribadi.
2. **Clone**: Mengunduh repositori hasil fork ke komputer lokal.
3. **Branch**: Selalu buat cabang baru untuk setiap tugas/fitur spesifik.
4. **Push**: Unggah cabang lokal Anda ke GitHub.
5. **Pull Request (PR)**: Mengajukan permintaan agar perubahan Anda ditinjau (*code review*) dan digabungkan ke cabang utama repositori induk.

---

### 2.9 Alur Kerja Harian Developer (Daily 4-Step Workflow)

Dalam lingkungan kerja profesional, terapkan 4 langkah standar berikut setiap hari:

1. **Langkah 1: Sinkronisasi Kode Terbaru**
   ```bash
   git checkout main
   git pull origin main
   ```
2. **Langkah 2: Buat Cabang Baru untuk Fitur/Bugfix**
   ```bash
   git checkout -b feature/halaman-kontak
   ```
3. **Langkah 3: Bekerja, Lakukan Staging, Commit, dan Push**
   ```bash
   git add .
   git commit -m "feat(kontak): tambahkan form kontak dan validasi input"
   git push -u origin feature/halaman-kontak
   ```
4. **Langkah 4: Buka GitHub & Buat Pull Request**
   * Buat PR, jelaskan perubahan yang Anda buat, tunggu tinjauan rekan tim, lalu lakukan *Merge*.

---

### 2.10 Praktik Terbaik (Best Practices)
* **Atomic Commits**: Buat commit secara berkala untuk unit perubahan kecil yang logis. Hindari menumpuk 50 perubahan file dalam 1 commit raksasa.
* **Pesan Commit yang Jelas**: Gunakan pola deskriptif seperti konvensi *Conventional Commits*:
  * `feat:` untuk fitur baru (contoh: `feat: tambahkan navigasi responsif`)
  * `fix:` untuk perbaikan bug (contoh: `fix: perbaiki tata letak kartu pada layar mobile`)
  * `docs:` untuk dokumentasi (contoh: `docs: perbarui panduan instalasi`)
* **Gunakan Berkas `.gitignore`**: Selalu abaikan file rahasia (`.env`), file dependensi berukuran raksasa (`node_modules/`, `vendor/`), dan file sistem operasi (`.DS_Store`, `Thumbs.db`).
* **Jangan Commit Langsung ke `main`**: Di proyek tim, selalu gunakan branch dan Pull Request agar kode tetap teruji.

---

## 3. Alat dan Persiapan
1. **Git CLI**: Terpasang di komputer (dapat dicek dengan `git --version`).
2. **Akun GitHub**: Memiliki akun aktif di [GitHub.com](https://github.com).
3. **Konfigurasi Identitas Git Global** (Wajib dilakukan satu kali di awal):
   ```bash
   git config --global user.name "Nama Lengkap Anda"
   git config --global user.email "email-anda@domain.com"
   ```
4. **Visual Studio Code** dengan terminal terintegrasi (`Ctrl + ~`).

---

## 4. Langkah-Langkah Praktikum (Hands-on)

### Skenario 1: Memeriksa Status & Melakukan Commit Lokal
1. Buka terminal di folder proyek ini.
2. Ketik perintah:
   ```bash
   git status
   ```
3. Perhatikan daftar file yang berstatus *Changes not staged for commit* atau *Untracked files*.
4. Masukkan perubahan ke Staging Area:
   ```bash
   git add .
   ```
5. Simpan commit lokal Anda:
   ```bash
   git commit -m "feat(modul): pelajari dasar git dan pelacakan versi"
   ```

### Skenario 2: Simulasi Percabangan (Branching)
1. Buat cabang baru bernama `fitur-eksperimen`:
   ```bash
   git checkout -b fitur-eksperimen
   ```
2. Buat atau ubah sebuah berkas catatan kecil, misalnya `catatan.txt`.
3. Lakukan commit pada cabang tersebut:
   ```bash
   git add catatan.txt
   git commit -m "docs: tambah catatan uji coba branch"
   ```
4. Kembali ke cabang `main`:
   ```bash
   git checkout main
   ```
5. Gabungkan (*merge*) perubahan dari cabang eksperimen:
   ```bash
   git merge fitur-eksperimen
   ```

### Skenario 3: Simulasi Merge Conflict & Penyelesaiannya
1. Ubah baris ke-1 di `catatan.txt` pada branch `main` menjadi:
   `Catatan Versi Main: Penting dipelajari.`
   Lakukan commit di `main`.
2. Pindah ke branch `fitur-eksperimen`:
   `git checkout fitur-eksperimen`
3. Ubah baris ke-1 di `catatan.txt` menjadi kalimat yang berbeda:
   `Catatan Versi Eksperimen: Menjelajahi fitur baru.`
   Lakukan commit di `fitur-eksperimen`.
4. Kembali ke `main` lalu coba lakukan `git merge fitur-eksperimen`.
5. Git akan menampilkan pesan `CONFLICT (content): Merge conflict in catatan.txt`.
6. Buka `catatan.txt` di VS Code, telaah penanda konflik `<<<<<<<`, pilih kalimat yang dikehendaki, hapus penanda konflik, lalu selesaikan dengan `git add catatan.txt` dan `git commit -m "fix: resolve conflict on catatan.txt"`.

---

## 5. Tugas Modul
Kerjakan tugas praktikum Git & GitHub berikut:
1. Pastikan komputer Anda telah terkonfigurasi dengan nama dan email GitHub Anda (`git config --list`).
2. Buat sebuah branch baru di repositori lokal Anda dengan format nama `tugas-git/nama-panggilan-anda`.
3. Buat sebuah file baru bernama `laporan-git.md` di dalam direktori `Modul/Modul-Git-GitHub/` yang berisi:
   - Identitas diri (Nama, NIM/NRP, Program Studi).
   - Penjelasan singkat mengenai perbedaan *Working Directory*, *Staging Area*, dan *Local Repository* menurut pemahaman Anda.
   - Tangkapan layar (*screenshot*) atau salinan teks dari perintah `git log --oneline` yang menunjukkan riwayat commit yang pernah Anda buat.
4. Lakukan `git add` dan `git commit` dengan pesan commit yang mengikuti aturan *Conventional Commits* (misal: `docs: buat laporan praktikum git`).
5. Gabungkan (*merge*) branch tersebut kembali ke branch `main`.

---

## 6. Referensi
* Materi Presentasi Workshop Multimedia: *Menguasai Git & GitHub (1).pdf*
* [Dokumentasi Resmi Git (Pro Git Book)](https://git-scm.com/book/id/v2)
* [GitHub Skills - Latihan Interaktif Resmi](https://skills.github.com/)
* [Conventional Commits Specification](https://www.conventionalcommits.org/en/v1.0.0/)
