# Modul 2: Pengenalan dan Dasar-Dasar CSS

Selamat datang di **Modul 2: Pengenalan dan Dasar-Dasar CSS**! Setelah menyusun kerangka dokumen dengan HTML pada Modul 1, sekarang Anda akan mempelajari cara mempercantik, menata tata letak (*layout*), serta membuat halaman web menjadi responsif di berbagai perangkat menggunakan **Cascading Style Sheets (CSS)**.

---

## 1. Tujuan Praktikum
Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:
1. Memahami konsep dasar CSS dan perannya dalam memisahkan konten (HTML) dari penyajian visual.
2. Membedakan dan mengimplementasikan 3 metode penerapan CSS (*Inline*, *Internal*, dan *External*).
3. Menguasai sintaks dasar CSS, selektor elemen, selektor class, selektor ID, dan selektor universal (`*`).
4. Mengimplementasikan *pseudo-element* (`::before`, `::after`, `::first-letter`, `::selection`).
5. Memahami dan mengonfigurasi konsep **CSS Box Model** (*Content*, *Padding*, *Border*, *Margin*).
6. Mengatur alur tampilan elemen menggunakan properti `display` (*block*, *inline*, *inline-block*, *flex*, *grid*, *none*).
7. Mengontrol peletakan elemen dengan properti `position` (*static*, *relative*, *absolute*, *fixed*, *sticky*).
8. Menerapkan prinsip dasar desain web responsif (*Responsive Web Design*) menggunakan *flexible units* dan *media queries*.

---

## 2. Teori Dasar

### 2.1 Apa Itu CSS dan Mengapa Dibutuhkan?
**CSS** (*Cascading Style Sheets*) adalah bahasa lembar gaya yang digunakan untuk mengatur tampilan visual dan tata letak halaman web.

**Nilai Tambah & Alasan Penggunaan CSS:**
* **Pemisahan Logika & Estetika**: Kode HTML tetap bersih hanya untuk data/struktur, sementara tampilan diatur terpusat di berkas CSS.
* **Konsistensi Desain**: Satu berkas CSS eksternal dapat digunakan oleh puluhan halaman sekaligus.
* **Pengalaman Pengguna (UX) Multi-Perangkat**: Menyesuaikan tampilan situs di layar smartphone, tablet, laptop, dan monitor desktop.
* **Fondasi Framework Modern**: Menguasai CSS dasar sangat penting sebelum melangkah ke framework seperti Tailwind CSS, Bootstrap, maupun styling pada React/Vue.

---

### 2.2 Tiga Cara Menambahkan CSS ke Dokumen HTML

| Metode | Sintaks Contoh | Kelebihan | Kekurangan | Kapan Digunakan |
| :--- | :--- | :--- | :--- | :--- |
| **Inline CSS** | `<h1 style="color: blue;">Judul</h1>` | Cepat untuk uji coba instan pada 1 elemen tertentu. | Kode HTML menjadi berantakan, sulit dirawat, tidak efisien. | Pengujian kilat atau styling dinamis spesifik dari script. |
| **Internal CSS** | `<style>` di dalam tag `<head>` | Mandiri dalam 1 berkas, tidak membutuhkan file eksternal tambahan. | Aturan gaya tidak dapat digunakan oleh halaman HTML lain. | Halaman tunggal (*single landing page*) dengan styling unik. |
| **External CSS** | `<link rel="stylesheet" href="style.css">` | Sangat rapi, modular, mudah dirawat, di-cache oleh browser sehingga memuat lebih cepat. | Membutuhkan berkas terpisah dan request HTTP tambahan. | **Standar Industri** untuk seluruh proyek web nyata. |

---

### 2.3 Struktur Sintaks CSS
Aturan penulisan CSS terdiri dari **Selector** dan **Declaration Block**:

```css
selector {
  property: value;
  property: value;
}
```

* **Selector**: Menunjuk elemen HTML mana yang ingin ditata gayanya.
* **Property**: Karakteristik visual yang ingin diubah (contoh: `color`, `background-color`, `font-size`).
* **Value**: Nilai atau spesifikasi yang diberikan untuk properti tersebut (contoh: `blue`, `#333`, `16px`).
* **Titik Koma (`;`)**: Digunakan untuk memisahkan setiap deklarasi properti.

---

### 2.4 CSS Selectors
1. **Element Selector**: Memilih elemen berdasarkan nama tag HTML.
   ```css
   p {
     color: #444;
     line-height: 1.6;
   }
   ```
2. **Class Selector** (Diawali tanda titik `.`): Dapat digunakan berulang kali pada elemen mana pun.
   ```css
   .card {
     background-color: #ffffff;
     border-radius: 8px;
   }
   ```
3. **ID Selector** (Diawali tanda pagar `#`): Bersifat unik, hanya untuk satu elemen spesifik dalam satu halaman.
   ```css
   #navbar-utama {
     background-color: #1a1a1a;
   }
   ```
4. **Universal Selector** (`*`): Memilih seluruh elemen di dokumen (sering digunakan untuk CSS Reset):
   ```css
   * {
     margin: 0;
     padding: 0;
     box-sizing: border-box;
   }
   ```

---

### 2.5 Pseudo-Element
*Pseudo-element* digunakan untuk menargetkan bagian khusus dari suatu elemen:

* `::before` & `::after`: Menyisipkan konten dekoratif sebelum atau sesudah konten elemen asli (wajib menyertakan properti `content`).
  ```css
  .badge::before {
    content: "★ ";
    color: gold;
  }
  ```
* `::first-letter`: Memberi gaya khusus pada huruf pertama sebuah paragraf (efek *drop cap*).
  ```css
  .artikel::first-letter {
    font-size: 200%;
    font-weight: bold;
    color: #0066cc;
  }
  ```
* `::selection`: Mengatur warna teks dan warna sorotan ketika teks dipilih/diblok oleh kursor pengguna.
  ```css
  ::selection {
    background-color: #3b82f6;
    color: #ffffff;
  }
  ```

---

### 2.6 CSS Box Model
Setiap elemen di halaman web diperlakukan sebagai sebuah "kotak" empat lapis:

```
+-----------------------------------------------+
|                    MARGIN                     |  <- Ruang kosong terluar antar elemen
|   +---------------------------------------+   |
|   |                BORDER                 |   |  <- Garis batas tepi elemen
|   |   +-------------------------------+   |   |
|   |   |            PADDING            |   |   |  <- Ruang antara garis border dan konten
|   |   |   +-----------------------+   |   |   |
|   |   |   |        CONTENT        |   |   |   |  <- Teks / gambar inti
|   |   |   +-----------------------+   |   |   |
|   |   +-------------------------------+   |   |
|   +---------------------------------------+   |
+-----------------------------------------------+
```

* **Content**: Area inti tempat teks, gambar, atau media berada.
* **Padding**: Ruang bantalan dalam yang memisahkan konten dari garis tepi (*border*).
* **Border**: Garis pembatas yang membingkai elemen.
* **Margin**: Jarak transparan di luar garis batas untuk memisahkan kotak tersebut dari elemen tetangganya.
* **`box-sizing: border-box;`**: Menginstruksikan browser agar perhitungan `width` dan `height` sudah mencakup padding dan border, sehingga layout tidak mudah rusak atau melebar keluar layar.

---

### 2.7 Properti Display
Menentukan bagaimana elemen ditampilkan dan menempati ruang pada alur dokumen:

* `display: block`: Memakan lebar horizontal 100% penuh dan selalu memulai baris baru (contoh default: `<div>`, `<p>`, `<h1>`).
* `display: inline`: Hanya selebar kontennya, tidak membuat baris baru, serta tidak bisa diatur nilai `width` dan `height`-nya (contoh default: `<span>`, `<a>`, `<strong>`).
* `display: inline-block`: Mengalir sebaris seperti inline, tetapi kita dapat mengatur `width`, `height`, margin, dan padding-nya seperti block.
* `display: flex`: Mengaktifkan model Flexbox 1 dimensi untuk penataan dinamis, perataan horizontal/vertikal yang sangat mudah.
* `display: grid`: Mengaktifkan model Grid 2 dimensi untuk baris dan kolom yang kompleks.
* `display: none`: Menyembunyikan elemen sepenuhnya dari tampilan layar dan alur dokumen.

---

### 2.8 Properti Position
Mengontrol koordinat posisi fisik elemen pada halaman web:

1. `position: static` (Default): Mengikuti urutan normal dokumen HTML (properti `top`, `bottom`, `left`, `right`, dan `z-index` tidak berlaku).
2. `position: relative`: Menggeser elemen dari posisi normalnya tanpa memengaruhi posisi elemen lain di sekitarnya. Sering digunakan sebagai wadah acuan (*reference frame*) untuk child element yang berstatus `absolute`.
3. `position: absolute`: Melepaskan elemen dari alur dokumen normal dan menempatkannya persis berdasarkan koordinat elemen induk terdekat yang non-static.
4. `position: fixed`: Mengunci posisi elemen relatif terhadap jendela layar (*viewport*). Elemen tetap berada di posisi yang sama meskipun halaman di-scroll ke atas maupun ke bawah (biasanya untuk navbar mengambang atau tombol *chat* WhatsApp).
5. `position: sticky`: Perpaduan antara relative dan fixed. Elemen bersikap normal hingga batas scroll tertentu tercapai, kemudian mengunci posisinya di layar.

---

### 2.9 Responsive Web Design (RWD) & Media Queries
Halaman web harus ramah pengguna baik diakses melalui smartphone layar kecil maupun monitor komputer besar.

#### 1. Satuan Fleksibel (*Flexible Units*)
Hindari menggunakan satuan piksel tetap (`px`) untuk seluruh layout. Gunakan satuan relatif:
* `%`: Persentase terhadap ukuran elemen induk (*parent*).
* `vw` & `vh`: Persentase terhadap lebar (*Viewport Width*) dan tinggi (*Viewport Height*) layar.
* `rem`: Ukuran relatif terhadap ukuran font akar (`<html>`).

#### 2. Gambar Responsif (*Responsive Images*)
Agar gambar tidak melebar melebihi lebar layar smartphone:
```css
img {
  max-width: 100%;
  height: auto;
}
```

#### 3. Media Queries
Teknik CSS untuk menerapkan styling khusus saat kriteria layar tertentu terpenuhi:
```css
/* Aturan dasar untuk layar komputer/desktop */
.container {
  display: flex;
  flex-direction: row;
}

/* Jika lebar layar 768px atau lebih kecil (tablet & ponsel) */
@media (max-width: 768px) {
  .container {
    flex-direction: column; /* Mengubah susunan menjadi bertumpuk vertikal */
  }
}
```

---

## 3. Alat dan Persiapan
1. **Text Editor**: Visual Studio Code.
2. **Web Browser**: Google Chrome, Mozilla Firefox, atau Microsoft Edge (dengan fitur **DevTools / Inspect Element** via `F12`).
3. **Berkas yang Digunakan**:
   * Halaman latihan HTML: [`index.html`](file:///C:/Users/justl/.gemini/antigravity/scratch/template-web-portofolio/Modul/Modul-2-CSS-Dasar/index.html) *(Lanjutan dari struktur Modul 1)*
   * Lembar gaya CSS: [`style.css`](file:///C:/Users/justl/.gemini/antigravity/scratch/template-web-portofolio/Modul/Modul-2-CSS-Dasar/style.css)

---

## 4. Langkah-Langkah Praktikum (Hands-on)

### Langkah 1: Memeriksa Integrasi File CSS
Buka berkas `index.html` pada VS Code. Perhatikan baris penghubung ke berkas CSS eksternal di dalam tag `<head>`:
```html
<link rel="stylesheet" href="style.css">
```
Jalankan **Live Server** (klik kanan `index.html` &gt; *Open with Live Server*). Bandingkan keindahan tampilannya dengan halaman polos Modul 1!

### Langkah 2: Mengamati Penggunaan 3 Metode CSS
1. Temukan contoh **Internal CSS** di tag `<head>` pada class `.badge-internal`.
2. Temukan contoh **Inline CSS** pada teks keterangan di bawah judul banner.
3. Amati bagaimana sebagian besar styling utama dikelola secara bersih di dalam `style.css` (**External CSS**).

### Langkah 3: Eksperimen dengan Box Model di DevTools
1. Di browser, klik kanan pada bagian kartu profil (`.profil-card`) lalu pilih **Inspect (F12)**.
2. Buka tab **Computed** atau diagram Box Model di panel kanan.
3. Amati nilai piksel dari **Content**, **Padding**, **Border**, dan **Margin**.
4. Coba ubah nilai `padding: 20px;` di file `style.css` menjadi `padding: 40px;` dan simpan. Amati perubahannya.

### Langkah 4: Memahami Positioning
1. Scroll halaman ke bawah. Perhatikan bagaimana bilah navigasi (`.header-fixed`) tetap menempel di atas karena menggunakan `position: fixed;`.
2. Amati tombol panah ke atas (`.btn-floating-top`) di pojok kanan bawah yang juga menggunakan `position: fixed;`.
3. Amati lencana hijau "Online" (`.status-badge`) yang ditaruh melayang persis di pojok foto profil menggunakan kombinasi `position: relative` (pada pembungkus foto) dan `position: absolute` (pada lencana).

### Langkah 5: Mempercantik Tabel dengan CSS
Bandingkan tabel keahlian Modul 1 yang sebelumnya menggunakan atribut bawaan `border="1"`. Di Modul 2, tabel tersebut kini menggunakan:
* `border-collapse: collapse;` untuk merapatkan garis batas.
* `tr:nth-child(even)` untuk memberikan efek selang-seling warna abu-abu muda (*zebra striping*).
* `tr:hover` untuk memberikan sorotan warna lembut saat kursor mouse melintasi baris tabel.

### Langkah 6: Menguji Desain Responsif
1. Perkecil jendela browser Anda, atau tekan `Ctrl + Shift + M` pada panel DevTools untuk mengaktifkan simulasi layar smartphone.
2. Amati bagaimana tata letak kartu profil otomatis bertransformasi dari susunan horizontal (menyamping) menjadi bertumpuk vertikal yang rapi.

---

## 5. Tugas Modul / Praktikum
Buatlah halaman tugas mandiri bernama `tugas-modul2.html` dan `tugas-style.css` yang melanjutkan halaman tugas Modul 1 Anda (`tugas-modul1.html`) dengan spesifikasi:
1. Hubungkan dokumen HTML dengan lembar gaya eksternal `tugas-style.css`.
2. Tambahkan bilah navigasi tetap (*fixed navbar*) di bagian atas layar menggunakan `position: fixed`.
3. Tata komponen profil atau portofolio menggunakan **Flexbox** (`display: flex`) lengkap dengan pengaturan `padding`, `margin`, `border`, dan sudut melengkung (`border-radius`).
4. Beri gaya pada tabel data Anda sehingga memiliki *header* berwarna kontras, garis batas tipis bersih, dan efek warna selang-seling (*zebra-striping*).
5. Buat minimal satu tombol CTA yang memiliki efek interaktif saat kursor mouse diarahkan (`:hover` dengan transisi warna dan transformasi tombol terangkat).
6. Terapkan satu aturan **Media Query** (`@media screen and (max-width: 768px)`) agar tata letak halaman berubah rapi menjadi satu kolom saat dibuka di layar ponsel.

---

## 6. Referensi
* Materi Presentasi Workshop Multimedia: *CSS (1).pdf*
* [MDN Web Docs - CSS Box Model](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model)
* [MDN Web Docs - CSS Layout and Positioning](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout)
* [W3Schools - CSS Media Queries](https://www.w3schools.com/css/css_rwd_mediaqueries.asp)
