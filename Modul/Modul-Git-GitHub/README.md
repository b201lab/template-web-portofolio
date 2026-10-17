# 🚀 Panduan Praktis Git & GitHub untuk Pemula

Selamat datang di modul **Git & GitHub**! Modul ini dirancang dengan pendekatan praktis dan ramah pemula agar kamu bisa langsung menguasai cara menyimpan versi kodingan, mencadangkan proyek ke cloud, dan berkolaborasi tanpa takut kodingan rusak atau hilang.

---

## 💡 1. Analogi Sederhana: Apa Itu Git & GitHub?

Sering kali pemula bingung membedakan antara **Git** dan **GitHub**. Cara termudah memahaminya:

```
+-------------------------------------------------------------+
| 💻 GIT (Di Komputer Lokal)                                  |
| Seperti "KAMERA SNAPSHOT" / Mesin Waktu.                    |
| - Bekerja secara offline di komputermu.                     |
| - Merekam riwayat perubahan kodingan baris demi baris.      |
| - Memungkinkan kamu kembali ke masa lalu jika ada error.    |
+-------------------------------------------------------------+
                              |
               Diunggah lewat: git push
                              v
+-------------------------------------------------------------+
| ☁️ GITHUB (Di Internet / Cloud)                             |
| Seperti "GOOGLE DRIVE / MEDIA SOSIAL KHUSUS KODING".        |
| - Tempat menyimpan cadangan proyekmu secara online.         |
| - Tempat memamerkan portofolio koding ke perekrut/klien.    |
| - Tempat bekerja sama dalam satu tim tanpa saling menimpa.  |
+-------------------------------------------------------------+
```

---

## 📦 2. Pahami "Alur 3 Meja Kerja" Git

Sebelum mengetik perintah, pahami alur kerja Git yang mirip dengan proses **mengepak barang untuk dikirim**:

```
+--------------------+        git add        +--------------------+      git commit      +--------------------+
| WORKING DIRECTORY  |  -------------------> |    STAGING AREA    |  ----------------->  |     REPOSITORY     |
|   (Meja Kerja)     |                       |  (Kardus Paket)    |                      |   (Gudang Arsip)   |
| Tempat kamu edit   |  <------------------- | Tempat persiapan   |  <-----------------  | Tersimpan permanen |
| file HTML/CSS/JS   |       git restore     | file yang dipilih  |       git reset      | riwayat commit-nya |
+--------------------+                       +--------------------+                      +--------------------+
                                                                                                    |
                                                                                             git push origin main
                                                                                                    v
                                                                                         +--------------------+
                                                                                         |       GITHUB       |
                                                                                         |   (Awan Cloud)     |
                                                                                         +--------------------+
```

1. **Working Directory (Meja Kerja):** Tempat kamu mengetik kodingan di VS Code.
2. **Staging Area (Kardus Paket):** Tempat mengumpulkan file-file yang sudah selesai dan siap dibungkus.
3. **Repository (Gudang Penyimpanan):** Tempat snapshot riwayat proyek disimpan permanen dengan label pesan (*commit*).
4. **GitHub (Cloud):** Salinan gudang penyimpanan yang diunggah ke internet.

---

## ⚡ 3. Empat "Mantra Sakti" Git (Dipakai 90% Waktu Koding)

Dalam aktivitas koding sehari-hari, kamu hanya perlu mengingat **4 langkah berurutan** ini:

| Urutan | Perintah | Fungsi | Analogi Sehari-hari |
| :---: | :--- | :--- | :--- |
| **1** | `git status` | Melihat file mana yang baru diubah atau belum disimpan | Mengecek barang apa saja di meja kerja |
| **2** | `git add .` | Mendaftarkan semua perubahan ke Staging Area | Memasukkan semua barang ke dalam kardus |
| **3** | `git commit -m "pesan"` | Menyimpan permanen perubahan dengan catatan | Melakban kardus dan menuliskan label nama paket |
| **4** | `git push origin main` | Mengirim commit lokal ke repositori GitHub | Mengirimkan paket ke ekspedisi/cloud |

---

## 🛠️ 4. Praktik Langsung: Dari Komputer ke GitHub

Ikuti 3 misi praktikum berikut untuk langsung mempraktikkan materi hari ini:

### 🎯 Misi 1: Kenalkan Dirimu ke Git (Cukup 1x di Laptop)
Sebelum membuat commit, Git harus tahu siapa penulis kodenya:
```bash
git config --global user.name "Nama Lengkap Anda"
git config --global user.email "email-anda@gmail.com"
```
> 🔍 **Cek apakah sudah berhasil:** Ketik `git config --list`.

---

### 🎯 Misi 2: Upload Proyek Portofolio ke GitHub Pribadi

Jika kamu punya folder portofolio di laptop dan ingin mengunggahnya ke akun GitHub pribadimu:

#### Langkah A: Buat Repositori Kosong di Website GitHub
1. Buka [github.com](https://github.com) dan login.
2. Klik ikon **`+`** di pojok kanan atas $\rightarrow$ pilih **New repository**.
3. Beri nama repositori: `portofolio-web`.
4. Pilih **Public**.
5. ⚠️ **Penting:** **JANGAN centang** *"Add a README file"* (biarkan kosong).
6. Klik **Create repository**, lalu salin link URL-nya (contoh: `https://github.com/username/portofolio-web.git`).

#### Langkah B: Hubungkan dan Kirim dari VS Code
Buka terminal VS Code di folder proyekmu (`Ctrl + ~`), lalu ketik:
```bash
# 1. Jadikan folder ini repositori Git (jika belum)
git init

# 2. Hubungkan ke alamat repositori GitHub milikmu
git remote add origin https://github.com/username-kamu/portofolio-web.git

# 3. Kumpulkan semua file dan simpan
git add .
git commit -m "feat: inisialisasi proyek portofolio web"

# 4. Pastikan branch utama bernama main, lalu kirim!
git branch -M main
git push -u origin main
```
> *Jika muncul pop-up login, pilih **"Sign in with your browser"** dan izinkan akses.*

---

### 🎯 Misi 3: Siklus Menyimpan Kodingan Selanjutnya
Setelah repo terhubung, setiap kali kamu selesai mengedit file (misalnya mengganti warna di CSS atau menambah fitur di Tailwind):
```bash
git status               # 1. Intip file apa yang berubah
git add .                # 2. Siapkan semua file
git commit -m "feat: ubah warna tema jadi hijau botol"  # 3. Simpan catatan
git push origin main     # 4. Kirim ke GitHub
```

---

## 🌿 5. Bekerja Aman dengan Cabang (Branching)

Bayangkan **Branch** seperti membuat lembar fotokopi dari kode utama (`main`):
Kamu bebas mencorat-coret fitur baru di lembar fotokopi tersebut. Jika hasilnya bagus, gabungkan ke dokumen asli. Jika gagal/rusak, buang saja fotokopinya tanpa merusak dokumen utama!

```
                    (fitur-tailwind)  [Commit A] ---> [Commit B]
                                           /                       \ (git merge)
                                          /                         v
(main / kode stabil) [Commit 1] ----> [Commit 2] ----------------> [Commit 3]
```

### Perintah Penting Branch:
```bash
# Membuat cabang eksperimen baru dan langsung pindah ke sana
git checkout -b coba-tailwind

# Melihat kamu sedang berada di cabang mana
git branch

# Kembali ke cabang utama
git checkout main

# Menggabungkan hasil dari cabang eksperimen ke cabang utama
git merge coba-tailwind

# Menghapus cabang eksperimen yang sudah selesai digabung
git branch -d coba-tailwind
```

---

## 📖 6. Kamus Cepat Perintah Git Pemula

Simpan tabel ini sebagai contekan cepat saat belajar:

| Kebutuhan | Perintah Git | Penjelasan Singkat |
| :--- | :--- | :--- |
| **Mulai Proyek** | `git init` | Mengaktifkan Git di folder saat ini |
| **Download Proyek** | `git clone <url>` | Mendownload seluruh proyek dari GitHub ke komputer |
| **Cek Kondisi** | `git status` | Melihat status file (merah = belum distage, hijau = siap commit) |
| **Pilih File** | `git add <nama-file>` | Memilih 1 file spesifik untuk disimpan |
| **Pilih Semua** | `git add .` | Memilih seluruh file yang berubah sekaligus |
| **Simpan Riwayat** | `git commit -m "pesan"` | Menyimpan permanen dengan catatan perubahan |
| **Lihat Riwayat** | `git log --oneline` | Melihat daftar riwayat commit ringkas 1 baris |
| **Kirim ke Cloud** | `git push origin main` | Mengirim commit dari komputer ke GitHub |
| **Ambil Update** | `git pull origin main` | Menarik kodingan terbaru dari GitHub ke komputer |
| **Ambil 1 Folder** | `git checkout origin/main -- "path"` | Mengambil satu folder tertentu saja dari GitHub |
| **Batalkan Edit** | `git restore <nama-file>` | Membatalkan ketikan sebelum di-add (kembali ke posisi awal) |

---

## ❓ 7. Pertolongan Pertama pada Masalah Git Pemula

### 1. Masalah: "fatal: remote origin already exists"
* **Penyebab:** Folder kamu sudah punya alamat remote GitHub lama.
* **Solusi:** Ubah alamatnya ke repo barumu menggunakan perintah:
  ```bash
  git remote set-url origin https://github.com/username-kamu/nama-repo.git
  ```

### 2. Masalah: "error: failed to push some refs"
* **Penyebab:** Ada file baru di GitHub yang belum ada di komputermu (misal kamu mencentang README saat buat repo di web).
* **Solusi:** Tarik dulu file dari GitHub baru lakukan push:
  ```bash
  git pull origin main --rebase
  git push origin main
  ```

### 3. Masalah: "Salah ketik pesan commit"
* **Solusi:** Selama belum di-push, perbaiki pesan commit terakhir dengan:
  ```bash
  git commit --amend -m "pesan baru yang benar"
  ```

---

## 📝 Tips Menulis Pesan Commit yang Rapi (Conventional Commits)
Gunakan awalan berikut agar riwayat proyekmu terlihat profesional:
* `feat:` untuk fitur/tampilan baru (contoh: `feat: buat halaman hero responsif`)
* `fix:` untuk perbaikan bug/error (contoh: `fix: perbaiki posisi foto profil`)
* `style:` untuk perubahan visual/CSS tanpa ubah logika (contoh: `style: ganti warna badge skill`)
* `docs:` untuk update berkas dokumentasi/README (contoh: `docs: perbarui panduan praktikum`)
