# Panduan Persiapan Pelatihan Web Development

Selamat datang di Pelatihan Web Development! Sebelum kita bertemu di sesi *Live Coding*, ada beberapa hal yang WAJIB kalian siapkan dan pelajari.

---

## Tahap 1: Persiapan Alat
Tolong install aplikasi berikut di laptop kalian sebelum hari H pelatihan untuk meminimalisir error:

1. **Text Editor: Visual Studio Code (VS Code)**
   - Download di: https://code.visualstudio.com/
   - **Wajib Install Ekstensi VS Code berikut:**
     - `Live Server` (Agar web otomatis refresh saat kode disave).
     - `Tailwind CSS IntelliSense` (Membantu auto-complete kode Tailwind).
     - `Prettier - Code formatter` (Agar kode otomatis rapi).

2. **Git & Akun GitHub**
   - Download Git: https://git-scm.com/downloads (Install dengan pengaturan *Next-Next* saja).
   - Buat akun GitHub: https://github.com/ (Gunakan email aktif).

3. **Web Browser**
   - Disarankan menggunakan Google Chrome atau Microsoft Edge terbaru.

---

## Tahap 2: Materi Pra-Pelatihan
Di dalam folder `Modul/` terdapat 3 file. Buka file tersebut di VS Code dan **BACA KOMENTARNYA**. Kami sudah menjelaskan fungsi dari tag `<div>`, `<h1>`, margin, dll di dalam kodenya.
- `01-html-dasar.html` (Belajar kerangka)
- `02-css-dasar.css` (Belajar desain murni)
- `03-tailwind-dasar.html` (Belajar cara cepat styling modern)

---

## Tahap 3: Solusi Error yang Sering Terjadi

- **Masalah 1: "Live Server tidak mau jalan / error tidak ada tombol Go Live"**
  *Solusi:* Pastikan kalian membuka VS Code dengan cara `File > Open Folder` (Buka seluruh foldernya), bukan `File > Open File`.
- **Masalah 2: "Kode Tailwind saya tidak berubah warnanya"**
  *Solusi:* Pastikan laptopmu terkoneksi internet, karena kita menggunakan Tailwind CDN (menarik script dari internet). Pastikan juga tidak ada *typo* pada class, contoh: `bg-blue-500`, bukan `bg-blue 500`.
- **Masalah 3: "Error saat git push: Authentication failed"**
  *Solusi:* GitHub sekarang mengharuskan login via browser saat pertama kali push. Pastikan kalian memilih *Sign in with Browser* saat pop-up muncul, atau buat *Personal Access Token (PAT)* di pengaturan GitHub.

---