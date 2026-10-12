# Modul Vercel & Deployment: Publikasikan Portofolio ke Internet

Selamat datang di **Modul Vercel & Deployment**! Pada modul ini, Anda akan memublikasikan website portofolio yang sudah dibuat menggunakan HTML, CSS, dan JavaScript agar dapat diakses melalui internet. Kita akan menghubungkan repositori GitHub ke Vercel, mengatur folder proyek, lalu menguji hasil deployment.

---

## Teori Dasar

### 1. Apa Itu Deployment?

**Deployment** adalah proses menempatkan aplikasi atau website pada server agar dapat diakses oleh pengguna melalui internet. File yang berjalan di komputer sendiri belum otomatis dapat dibuka oleh orang lain; file tersebut perlu diunggah ke layanan hosting.

### 2. Apa Itu Vercel?

**Vercel** adalah platform untuk membangun dan men-deploy website. Untuk proyek portofolio statis seperti HTML, CSS, dan JavaScript, Vercel dapat menyajikan file website tanpa server aplikasi khusus. Vercel juga dapat terhubung ke GitHub untuk menjalankan deployment setiap kali perubahan diunggah.

### 3. Alur GitHub dan Vercel

```text
Komputer lokal
	| git add, git commit, git push
	v
Repositori GitHub
	| perubahan pada branch yang terhubung
	v
Vercel melakukan deployment
	|
	v
Website dapat dibuka melalui URL publik
```

Setiap deployment memiliki URL. Vercel juga membuat **Preview Deployment** untuk perubahan pada branch atau Pull Request, sedangkan perubahan pada branch produksi yang dipilih (umumnya `main`) akan memperbarui **Production Deployment**.

### 4. Struktur Proyek yang Digunakan

Repositori latihan ini berisi beberapa modul, sedangkan website yang akan dipublikasikan berada di folder `Template-Web/`:

```text
Template-Web/
├── index.html
├── css/
├── images/
└── js/
```

Karena `index.html` berada di dalam `Template-Web/`, folder tersebut harus ditetapkan sebagai **Root Directory** pada pengaturan proyek Vercel. Dengan begitu, path relatif seperti `css/style.css` dan `images/ning2.jpg` tetap mengarah ke file yang benar.

---

## Alat dan Persiapan

1. Website portofolio siap dijalankan secara lokal.
2. Akun [GitHub](https://github.com/) dan [Vercel](https://vercel.com/).
3. Kode proyek sudah berada di repositori GitHub dan perubahan terakhir sudah di-*push*.
4. Browser modern dan koneksi internet.

Sebelum melanjutkan, buka `Template-Web/index.html` secara lokal atau gunakan Live Server. Pastikan halaman, stylesheet, gambar, dan tautan yang diperlukan tampil sesuai harapan.

---

## Langkah-Langkah Deployment

### Langkah 1: Simpan dan Unggah Perubahan ke GitHub

Buka terminal pada folder repositori, lalu jalankan:

```bash
git status
git add .
git commit -m "feat: siapkan website portofolio untuk deployment"
git push origin main
```

Jika branch utama Anda bukan `main`, ganti `main` pada perintah terakhir dengan nama branch tersebut. Pastikan perubahan terlihat di halaman repositori GitHub sebelum mengimpor proyek.

### Langkah 2: Hubungkan GitHub ke Vercel

1. Buka [vercel.com](https://vercel.com/) dan masuk atau buat akun.
2. Pilih **Add New...** lalu **Project**.
3. Hubungkan akun GitHub jika diminta, dan berikan akses ke repositori yang akan digunakan.
4. Cari repositori portofolio, lalu pilih **Import**.

### Langkah 3: Atur Konfigurasi Proyek

Pada halaman konfigurasi sebelum deployment, gunakan pengaturan berikut:

| Pengaturan | Nilai |
| --- | --- |
| **Project Name** | Nama proyek yang Anda inginkan |
| **Root Directory** | `Template-Web` |
| **Framework Preset** | `Other` |
| **Build Command** | Kosongkan; proyek ini tidak memerlukan proses build |
| **Output Directory** | `.` agar file di dalam `Template-Web` disajikan langsung |
| **Install Command** | Kosongkan; proyek ini tidak menggunakan package manager |

Jika Vercel menampilkan pilihan **Root Directory**, pilih folder `Template-Web`, bukan folder modul atau direktori repositori paling luar. Pastikan konfigurasi tersebut benar sebelum menekan **Deploy**.

### Langkah 4: Jalankan dan Periksa Deployment

1. Klik **Deploy** dan tunggu sampai proses selesai.
2. Setelah status deployment berhasil, buka URL yang diberikan Vercel.
3. Pastikan halaman utama tampil dan periksa CSS, gambar, navigasi, serta tautan.
4. Uji juga tampilan pada ukuran layar ponsel.

URL tersebut dapat dibagikan sebagai tautan portofolio publik. Anda dapat melihat daftar deployment dan status build dari dashboard proyek Vercel.

### Langkah 5: Perbarui Website

Setelah integrasi GitHub aktif, perubahan pada branch yang terhubung akan memicu deployment baru. Contoh alur memperbarui website:

```bash
git add .
git commit -m "content: perbarui informasi portofolio"
git push origin main
```

Vercel akan membuat deployment setelah menerima perubahan. Tunggu sampai statusnya berhasil, kemudian muat ulang URL website untuk memeriksa hasilnya. Perubahan pada branch lain dapat menghasilkan URL preview yang terpisah dari website produksi.

---

## Tugas Modul

Deploy website portofolio Anda ke Vercel, lalu lengkapi tugas berikut:
1. Pastikan **Root Directory** proyek mengarah ke folder website yang berisi `index.html`.
2. Periksa website dari URL publik pada browser desktop dan ponsel.
3. Ubah satu bagian konten portofolio, lalu lakukan commit dan push ke branch produksi.
4. Pastikan perubahan muncul setelah deployment baru berhasil.
5. Catat URL deployment dan lampirkan pada pengumpulan tugas.

---

## Troubleshooting

| Masalah | Kemungkinan penyebab dan solusi |
| --- | --- |
| Halaman menampilkan 404 atau tidak ditemukan | Pastikan **Root Directory** mengarah ke folder yang memiliki `index.html`. Untuk proyek ini, pilih `Template-Web`. |
| Halaman terbuka tetapi tanpa styling | Periksa path stylesheet di HTML dan pastikan folder `css/` ikut berada di dalam direktori proyek yang di-deploy. |
| Gambar tidak muncul | Periksa ejaan nama file, huruf besar-kecil, dan path relatif pada atribut `src`. Nama file di hosting harus sama persis dengan yang ditulis di HTML. |
| Perubahan belum terlihat | Periksa apakah perubahan sudah di-*push* ke branch yang terhubung, lalu cek status deployment terbaru di dashboard Vercel. |
| Deployment gagal | Buka detail deployment dan periksa bagian **Build Logs** untuk mengetahui pesan error. Proyek HTML statis tidak memerlukan instalasi dependensi atau build command. |

---

## Referensi

* [Dokumentasi Vercel](https://vercel.com/docs)
* [Dokumentasi Vercel: Git Integrations](https://vercel.com/docs/deployments/git)
* [Dokumentasi Vercel: Project Configuration](https://vercel.com/docs/projects/project-configuration)
* [GitHub Docs](https://docs.github.com/)

---