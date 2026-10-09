# Panduan Pelatihan Web Development & Workshop Multimedia

Selamat datang di repositori Pelatihan Web Development dan Workshop Multimedia! Repositori ini menyediakan panduan praktikum, template proyek portofolio, serta modul-modul pembelajaran yang telah diselaraskan dengan materi kurikulum workshop (HTML, CSS, Tailwind CSS, serta Git & GitHub).

---

## 📁 Struktur Repositori

```
template-web-portofolio/
├── Modul/
│   ├── Modul-Git-GitHub/        # Panduan version control, branching, merge conflict, & GitHub
│   ├── Modul-1-HTML-Dasar/      # Struktur kerangka HTML5, teks, tabel, media, & tag semantik
│   ├── Modul-2-CSS-Dasar/       # Tata letak, CSS Box Model, pseudo-element, positioning, & media query
│   ├── Modul-3-Tailwind-Dasar/  # Utility-first styling modern dengan Tailwind CSS CDN
│   └── Template-Modul/          # Kerangka standar praktikum untuk penambahan modul baru
├── Template-Web/                # Template starter portofolio siap pakai (HTML, CSS, JS, Images)
└── README.md                    # Panduan utama pelatihan
```

---

## 🛠️ Tahap 1: Persiapan Alat & Lingkungan

Sebelum mengikuti sesi praktikum / *Live Coding*, pastikan aplikasi berikut telah terpasang di komputer Anda:

1. **Text Editor: Visual Studio Code (VS Code)**
   - Unduh di: [https://code.visualstudio.com/](https://code.visualstudio.com/)
   - **Ekstensi yang direkomendasikan:**
     - `Live Server` oleh Ritwick Dey (untuk reload otomatis saat berkas disimpan).
     - `Tailwind CSS IntelliSense` (auto-complete class utility Tailwind).
     - `Prettier - Code formatter` (perapian format kode otomatis).

2. **Git & Akun GitHub**
   - Unduh Git: [https://git-scm.com/downloads](https://git-scm.com/downloads)
   - Daftarkan akun aktif di: [https://github.com/](https://github.com/)
   - Konfigurasi nama & email lokal:
     ```bash
     git config --global user.name "Nama Lengkap"
     git config --global user.email "email-anda@domain.com"
     ```

3. **Web Browser Modern**
   - Google Chrome, Mozilla Firefox, atau Microsoft Edge (versi terbaru dengan Developer Tools / `F12`).

---

## 📚 Tahap 2: Daftar Modul Pembelajaran

Setiap modul di bawah ini dilengkapi dengan buku petunjuk praktikum (`README.md`), aset gambar (`images/`), serta berkas kode contoh yang dapat langsung dijalankan:

1. 🚀 **[Modul Git & GitHub](Modul/Modul-Git-GitHub/README.md)**  
   *Mempelajari Distributed Version Control System (DVCS), Three Trees (Working Directory, Staging Area, Local Repo), Branching, Resolusi Merge Conflict, GitHub Remote, Pull Request, dan Daily Git Workflow.*

2. 🧱 **[Modul 1: HTML Dasar](Modul/Modul-1-HTML-Dasar/README.md)**  
   *Mempelajari analogi kerangka web, anatomi tag/elemen/atribut, pemformatan teks, media gambar & iFrame, data tabel terstruktur (`thead`, `tbody`), wadah `div`, serta tag semantik HTML5 (`header`, `nav`, `section`, `footer`).*

3. 🎨 **[Modul 2: CSS Dasar](Modul/Modul-2-CSS-Dasar/README.md)**  
   *Mempelajari pemisahan konten & visual, 3 metode CSS (Inline, Internal, External), selektor & pseudo-elements (`::before`, `::selection`), CSS Box Model, properti display, positioning (`fixed`, `relative`, `absolute`), serta Responsive Web Design menggunakan Media Query.*

4. ⚡ **[Modul 3: Tailwind CSS Dasar](Modul/Modul-3-Tailwind-Dasar/README.md)**  
   *Mempelajari konsep Utility-First CSS Framework, instalasi instan via CDN, perancangan tata letak responsif berbasis kelas, serta pembuatan antarmuka portofolio interaktif.*

5. 🌐 **[Template Web Portofolio](Template-Web/index.html)**  
   *Template dasar halaman portofolio mandiri dengan susunan `css/`, `js/`, dan `images/` yang siap dimodifikasi dan diunggah ke GitHub Pages.*

---

## ❓ Tahap 3: Solusi Error yang Sering Terjadi

* **Masalah 1: "Live Server tidak mau jalan / tidak ada tombol Go Live"**  
  *Solusi:* Buka VS Code menggunakan menu **File > Open Folder** dan pilih folder induk proyek `template-web-portofolio`, bukan membuka satu berkas file saja secara terisolasi.

* **Masalah 2: "Kode Tailwind saya tidak berubah warnanya / styling tidak aktif"**  
  *Solusi:* Pastikan komputer terhubung ke internet saat memuat tag Tailwind CDN (`<script src="https://cdn.tailwindcss.com"></script>`). Periksa juga apakah terdapat saltik (*typo*) pada nama kelas (misal: gunakan `bg-blue-500`, bukan `bg-blue 500`).

* **Masalah 3: "Error saat git push: Authentication failed"**  
  *Solusi:* Pilih opsi *Sign in with Browser* ketika jendela otentikasi Git Credential Manager muncul, atau buat *Personal Access Token (PAT)* di pengaturan keamanan akun GitHub Anda.

---
&copy; 2026 Laboratorium Praktikum Web & Multimedia.