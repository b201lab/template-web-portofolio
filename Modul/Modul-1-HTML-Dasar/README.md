# Modul 1: Pengenalan dan Dasar-Dasar HTML

Selamat datang di **Modul 1: Pengenalan dan Dasar-Dasar HTML**! Modul ini dirancang secara sistematis mengikuti kurikulum dan materi presentasi workshop multimedia, memandu Anda dari konsep fundamental markup web hingga penyusunan struktur halaman yang semantik, interaktif, dan rapi.

---

## 1. Tujuan Praktikum
Setelah menyelesaikan modul praktikum ini, mahasiswa diharapkan mampu:
1. Memahami konsep HyperText Markup Language (HTML) dan peran tripartit web (**HTML** sebagai kerangka, **CSS** sebagai tampilan/gaya, dan **JavaScript** sebagai interaktivitas/perilaku).
2. Memahami cara kerja browser merender berkas HTML secara lokal maupun via web server (Live Server).
3. Menguasai anatomi elemen HTML: *opening tag*, *content*, *closing tag*, *attributes*, dan *comments*.
4. Mengimplementasikan tag-tag pemformatan teks: hierarki *heading* (`<h1>` s/d `<h6>`), paragraf (`<p>`), hyperlink (`<a>`), elemen inline (`<span>`), serta penekanan teks (`<b>` dan `<i>`).
5. Menyajikan daftar terstruktur menggunakan *Unordered List* (`<ul>`) dan *Ordered List* (`<ol>`).
6. Mengintegrasikan media visual dan konten luar ke dalam halaman web menggunakan tag `<img>` (lengkap dengan penanganan atribut `alt`) dan `<iframe>`.
7. Merancang penyajian data tabular terstruktur menggunakan elemen tabel modern (`<table>`, `<thead>`, `<tbody>`, `<tr>`, `<th>`, `<td>`).
8. Memahami konsep *layout container* menggunakan `<div>` dan membandingkan struktur lawas HTML4 dengan tag semantik modern HTML5 (`<header>`, `<nav>`, `<section>`, `<article>`, `<footer>`).

---

## 2. Teori Dasar

### 2.1 Pengenalan HTML & Analogi 3 Pilar Web
**HTML** (*HyperText Markup Language*) adalah bahasa markah standar industri yang digunakan untuk menyusun kerangka dan struktur sebuah halaman web.

Untuk memahami bagaimana sebuah website modern dibangun, perhatikan analogi tiga komponen utama:
* 🦴 **HTML (Skeleton / Kerangka Tulang)**: Bertugas menentukan struktur dasar, penempatan kepala (*header*), badan (*body*), teks, gambar, dan tombol. Tanpa HTML, tidak ada pondasi yang dapat ditampilkan.
* 👗 **CSS (Skin & Fashion / Kulit & Pakaian)**: Memberikan keindahan visual, warna, jenis huruf (*typography*), spasi, garis batas, dan tata letak artistik.
* 💃 **JavaScript (Muscles & Brain / Otot & Gerakan)**: Memberikan daya dinamis, logika interaksi pengguna, animasi, pengiriman data formulir, dan perilaku responsif.

> **Contoh Cara Kerja Bersama:**
> Berkas HTML mendefinisikan teks `<h1>Welcome to MAGE workshop</h1>` dan `<p>Halo dunia</p>`. File CSS menambahkan aturan:
> ```css
> h1 {
>   font-family: courier;
>   font-size: 20pt;
>   color: blue;
>   border-bottom: 2px solid blue;
> }
> p {
>   font-family: arial;
>   font-size: 12pt;
>   color: #6B6BD7;
> }
> .red_txt {
>   color: red;
> }
> ```
> Lalu JavaScript dapat dipasang untuk mengubah teks tersebut saat tombol diklik.

---

### 2.2 Anatomi Tag dan Elemen HTML
Elemen HTML pada umumnya tersusun dari tiga komponen utama:

```html
<p>My first paragraph</p>
```

1. **Opening Tag (Tag Pembuka)**: `<p>`
   * `<` : Kurung sudut buka (*open angle bracket*)
   * `p` : Nama tag (*tag name*)
   * `>` : Kurung sudut tutup (*close angle bracket*)
2. **HTML Content (Konten)**: Teks atau elemen bersarang di dalamnya (`My first paragraph`).
3. **Closing Tag (Tag Penutup)**: `</p>`
   * `<` : Kurung sudut buka
   * `/` : Garis miring penutup (*forward slash*)
   * `p` : Nama tag yang sama dengan pembuka
   * `>` : Kurung sudut tutup

#### Atribut HTML
Atribut adalah parameter tambahan yang diletakkan di dalam **tag pembuka** untuk memodifikasi atau memberikan informasi spesifik pada elemen:
```html
<p style="color:red">My first paragraph</p>
<a href="https://www.wikipedia.org">Hello Wikipedia</a>
<img src="foto.jpg" width="80%" alt="Deskripsi gambar" />
```
* Terdiri dari **Nama Atribut** (misal: `style`, `href`, `width`, `alt`) dan **Nilai Atribut** di dalam tanda petik (misal: `"color:red"`).

#### Komentar HTML (Comment)
Komentar digunakan developer untuk memberikan penjelasan catatan pada kode. Kode komentar diabaikan sepenuhnya oleh browser dan tidak ditampilkan di layar:
```html
<!-- place where only developer and god know -->
```

---

### 2.3 Struktur Dasar Dokumen HTML5
Struktur dokumen HTML memiliki konsep kotak bersarang (*nested box hierarchy*):

```html
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>MAGE Workshop</title>
</head>
<body>
  <h1>Welcome to MAGE workshop</h1>
  <p>My first paragraph</p>
</body>
</html>
```

* `<!DOCTYPE html>`: Deklarasi standar browser bahwa dokumen menggunakan standar HTML5.
* `<html>`: Wadah induk terluar (*root element*) yang membungkus seluruh isi web.
* `<head>`: Wadah informasi meta, judul tab (`<title>`), pemanggilan file CSS, dan konfigurasi dokumen yang tidak tampak langsung di halaman.
* `<body>`: Wadah semua elemen yang secara visual tampil di layar pengunjung (*headings*, paragraf, gambar, tombol, link, tabel).

---

### 2.4 Elemen Pemformatan Teks

#### 1. Heading (`<h1>` s/d `<h6>`)
Digunakan untuk membuat judul dan sub-judul secara hierarkis (mirip pengaturan Heading 1 sampai Heading 6 pada dokumen Google Docs/MS Word):
* `<h1>`: Judul utama (tingkat paling penting, sebaiknya hanya ada 1 per halaman untuk SEO).
* `<h2>` hingga `<h6>`: Sub-judul dengan ukuran dan bobot yang bertingkat semakin mengecil.

```html
<!-- heading.html -->
<h1>MAGE WORKSHOP 2026 | HEADING 1</h1>
<h2>MAGE WORKSHOP 2026 | HEADING 2</h2>
<h3>MAGE WORKSHOP 2026 | HEADING 3</h3>
<h4>MAGE WORKSHOP 2026 | HEADING 4</h4>
<h5>MAGE WORKSHOP 2026 | HEADING 5</h5>
<h6>MAGE WORKSHOP 2026 | HEADING 6</h6>
```

#### 2. Paragraf (`<p>`)
Digunakan untuk menulis blok teks atau artikel naratif:
```html
<!-- paragraf.html -->
<p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod 
  tempor incididunt ut labore et dolore magna aliqua.
</p>
```

#### 3. Hyperlink Anchor (`<a>`)
Digunakan untuk menavigasikan pengunjung ke halaman web lain atau tautan eksternal menggunakan atribut `href`:
```html
<!-- anchor.html -->
<a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ">ini adalah link, klik aja kalau mau lihat</a>
```

#### 4. Span (`<span>`)
Elemen *inline container* yang digunakan untuk membungkus dan menargetkan sebagian teks tertentu tanpa membuat baris baru:
```html
<!-- span.html -->
<p>sang jago merah sedang melahap rumah warga, sehingga rumah warga jadi <span style="color: red">MENYALA</span></p>
```

#### 5. Format Tebal (`<b>`) dan Miring (`<i>`)
Digunakan untuk memberikan penekanan gaya pada teks:
```html
<!-- bold.html -->
<b>Ini adalah tulisan bold</b>
<br>
<i>Ini adalah tulisan italic</i>
<br>
<b><i>Ini adalah tulisa bold dan italic</i></b>
```

#### 6. List / Daftar (`<ul>` & `<ol>`)
Digunakan untuk menampilkan poin-poin daftar data:
* `<ul>` (*Unordered List*): Menampilkan daftar berpoin (*bullet points*).
* `<ol>` (*Ordered List*): Menampilkan daftar bernomor angka berurutan (*numbered points*).
* `<li>` (*List Item*): Setiap butir item di dalam daftar.

```html
<!-- list.html -->
<!-- 1. Unordered List -->
<ul>
  <li>kopi</li>
  <li>teh</li>
  <li>susu</li>
</ul>

<!-- 2. Ordered List -->
<ol>
  <li>kucing</li>
  <li>anjing</li>
  <li>ikan</li>
</ol>
```

---

### 2.5 Media: Gambar dan iFrame

#### 1. Gambar (`<img>`)
Tag `<img>` digunakan untuk menampilkan gambar. Tag ini tidak memerlukan tag penutup terpisah (*void / self-closing tag*).
* Atribut `src`: Menentukan sumber lokasi berkas gambar (relatif atau URL).
* Atribut `alt` (*Alternative Text*): Teks cadangan yang akan ditampilkan di layar jika gambar gagal dimuat (misal file hilang atau koneksi terputus), serta sangat krusial untuk aksesibilitas *screen reader*.

```html
<!-- media/image.html -->
<img src="images.jpg" alt="ini adalah alt" />
```

> **Pembuktian Fungsi Atribut `alt`:**
> Apabila `src=""` dibiarkan kosong atau nama berkas salah, browser akan menampilkan ikon *broken image* disertai teks yang tertulis pada atribut `alt`, yaitu `"ini adalah alt"`.

#### 2. iFrame (`<iframe>`)
Tag `<iframe>` (*Inline Frame*) digunakan untuk menyematkan halaman web lain atau dokumen eksternal secara langsung ke dalam halaman Anda:
```html
<!-- media/iframe.html -->
<iframe src="https://www.wikipedia.org" width="300" height="240"></iframe>
```

---

### 2.6 Penyajian Data Menggunakan Tabel (`<table>`)
Tabel digunakan untuk menyajikan data tabular yang rapi ke dalam baris dan kolom:
* `<table>`: Elemen pembungkus tabel.
* `<thead>`: Bagian kepala tabel (*table header group*).
* `<tbody>`: Bagian badan data tabel (*table body group*).
* `<tr>` (*Table Row*): Baris tabel.
* `<th>` (*Table Header*): Sel judul kolom (otomatis dicetak tebal dan rata tengah).
* `<td>` (*Table Data*): Sel data biasa pada baris tabel.

```html
<!-- table.html -->
<table>
  <thead>
    <tr>
      <th>No</th>
      <th>Nama</th>
      <th>Status</th>
      <th>Umur</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>Fern</td>
      <td>Hidup</td>
      <td>25</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Stark</td>
      <td>Hidup</td>
      <td>25</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Nenek Frieren</td>
      <td>Hidup(?)</td>
      <td>1000</td>
    </tr>
  </tbody>
</table>
```

---

### 2.7 Tata Letak Web: `<div>` & Semantik HTML5

#### 1. Pembungkus Komponen (`<div>`)
`<div>` (*Division*) adalah wadah netral (*block container*) yang bertindak seperti kardus pembungkus untuk menyatukan beberapa elemen (gambar, judul, deskripsi, tombol) menjadi satu kesatuan kartu komponen (*card component*) agar dapat ditata bersama oleh CSS:

```html
<!-- div.html: Contoh Card Profil Komponen -->
<div class="kartu-profil">
  <!-- Komponen 1: Gambar -->
  <img src="https://via.placeholder.com/100" alt="Foto Frieren" class="foto-profil" />

  <!-- Komponen 2: Judul (Heading) -->
  <h2 class="nama">Nenek Frieren</h2>

  <!-- Komponen 3: Paragraf -->
  <p class="deskripsi">
    Seorang Elf penyihir yang sudah hidup lebih dari 1000 tahun.
  </p>

  <!-- Komponen 4: Tombol -->
  <button class="tombol-sapa">Kirim Pesan</button>
</div>
```

#### 2. Perbandingan Layout: HTML4 vs HTML5 Semantic
Pada era HTML4, seluruh pembagian tata letak halaman dibuat menggunakan `<div>` yang dibedakan hanya melalui `id` atau `class`. Standar modern HTML5 memperkenalkan **Semantic Elements** yang memiliki makna struktur yang jelas bagi browser, mesin pencari (SEO), dan developer:

| Tata Letak Konvensional (Typical HTML4) | Tata Letak Modern (Typical HTML5) | Fungsi dan Penempatan pada Web |
| :--- | :--- | :--- |
| `<div id="header">` | `<header>` | Bagian kepala web, menampung logo, judul utama, atau banner |
| `<div id="menu">` | `<nav>` | Bagian navigasi tautan menu (`Beranda`, `Kompetisi`, `Acara`, dll) |
| `<div id="content">` | `<section>` | Bagian seksi konten spesifik atau seksi utama |
| `<div class="article">` | `<article>` | Bagian konten mandiri (postingan, artikel berita, testimoni) |
| `<div id="footer">` | `<footer>` | Bagian kaki web (hak cipta, tautan sosial media Instagram/TikTok) |

---

## 3. Alat dan Persiapan Praktikum
1. **Kode Editor**: Visual Studio Code (direkomendasikan).
2. **Web Browser**: Google Chrome, Mozilla Firefox, atau Microsoft Edge.
3. **Ekstensi VS Code**: **Live Server** (oleh Ritwick Dey) agar halaman otomatis termuat ulang saat berkas disimpan.
4. **Folder Kerja**: Arahkan terminal/editor Anda ke `template-web-portofolio/Modul/Modul-1-HTML-Dasar/`.

---

## 4. Langkah-Langkah Praktikum (Hands-on)

### Langkah 1: Membuka Berkas Latihan
Buka folder `Modul/Modul-1-HTML-Dasar/` pada VS Code. Perhatikan berkas:
* [`index.html`](file:///C:/Users/justl/.gemini/antigravity/scratch/template-web-portofolio/Modul/Modul-1-HTML-Dasar/index.html)

Klik kanan pada `index.html` lalu pilih **Open with Live Server** (atau buka langsung pada browser Anda di alamat `http://127.0.0.1:5500/...`).

### Langkah 2: Menguji Tag Heading dan Paragraf
1. Buat hierarki judul menggunakan `<h1>` hingga `<h6>`.
2. Tambahkan paragraf `<p>` yang memuat teks perkenalan Anda.
3. Sisipkan tag `<b>`, `<i>`, dan `<span>` dengan warna khusus untuk menandai kata-kata penting.

### Langkah 3: Menambahkan Daftar (List) & Tautan (Anchor)
1. Buat daftar minat/hobi Anda menggunakan `<ul>` (*Unordered List*).
2. Buat daftar tahapan belajar pemrograman menggunakan `<ol>` (*Ordered List*).
3. Tambahkan tag tautan `<a>` dengan atribut `href="https://github.com/..."` untuk menghubungkan ke profil GitHub Anda.

### Langkah 4: Menyisipkan Media Gambar dan iFrame
1. Masukkan file gambar pada folder atau gunakan URL gambar valid.
2. Pasang tag `<img src="foto.jpg" alt="Foto Mahasiswa" width="180">`.
3. Uji hapus nama file gambar di atribut `src` untuk memverifikasi apakah teks atribut `alt` muncul di layar browser.
4. Sisipkan elemen `<iframe src="https://www.wikipedia.org" width="350" height="250"></iframe>`.

### Langkah 5: Membuat Tabel Data Karakter / Mahasiswa
Susun tabel data menggunakan elemen semantik tabel (`<table>`, `<thead>`, `<tbody>`, `<tr>`, `<th>`, `<td>`):
* Kolom terdiri dari `No`, `Nama`, `Status`, dan `Umur`.
* Isi minimal 3 baris data.

### Langkah 6: Mengorganisir Layout Semantik HTML5
Ganti pembungkus generik halaman Anda dengan struktur semantik:
* Bungkus bagian atas dengan `<header>` dan `<nav>`.
* Bungkus bagian isi profil dan tabel dengan `<section>`.
* Bungkus bagian bawah dengan `<footer>` lengkap dengan teks hak cipta.

---

## 5. Tugas Modul / Praktikum
Buatlah berkas baru bernama `tugas-modul1.html` di dalam folder ini yang memuat:
1. Struktur lengkap HTML5 (`<!DOCTYPE html>`, `<html>`, `<head>`, `<body>`).
2. Penggunaan layout semantik: `<header>`, `<nav>`, minimal dua `<section>`, dan `<footer>`.
3. Foto profil menggunakan `<img src="..." alt="..." width="...">`.
4. Komponen kartu profil (`<div class="kartu-profil">`) yang memuat foto, nama, deskripsi singkat, dan tombol sapa.
5. Tabel daftar mata kuliah atau keahlian menggunakan `<table>`, `<thead>`, `<tbody>`, `<tr>`, `<th>`, dan `<td>`.
6. Daftar list hobi/minat menggunakan `<ul>` dan daftar tahapan belajar menggunakan `<ol>`.
7. Tautan `<a>` ke akun sosial media atau repositori GitHub Anda.
8. Penyematan 1 elemen `<iframe>` (misal Google Maps kampus atau halaman referensi).
9. Minimal 2 komentar HTML (`<!-- komentar -->`) untuk dokumentasi kode.

---

## 6. Referensi
* Slide Workshop Multimedia: *HTML (1).pdf*
* [MDN Web Docs - HTML: HyperText Markup Language](https://developer.mozilla.org/en-US/docs/Web/HTML)
* [W3Schools - HTML Tutorial & References](https://www.w3schools.com/html/)
