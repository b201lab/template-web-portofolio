# Modul 3: Styling Cepat & Modern dengan Tailwind CSS

## 1. Tujuan 
1. Memahami konsep Utility-First CSS Framework menggunakan Tailwind CSS.
2. Mampu mengintegrasikan Tailwind CSS melalui CDN pada file HTML.
3. Menguasai class-class utilitas populer untuk typography, spacing (margin/padding), flexbox/grid, background, rounded, dan shadow.
4. Menerapkan pseudo-class modifier (seperti `hover:`, `focus:`) langsung pada atribut class HTML.
5. Membangun antarmuka portofolio web modern yang responsif menggunakan template siap pakai.

---

## 2. Teori Dasar

Tailwind CSS adalah framework CSS berparadigma **Utility-First**. Berbeda dengan pendekatan tradisional yang mengharuskan pembuatan file `.css` terpisah dan penamaan class kustom, Tailwind menyediakan ribuan kelas utilitas siap pakai (misal: `flex`, `pt-4`, `text-center`, `rotate-90`) yang dapat digabungkan langsung di dalam atribut `class="..."`.

### 2.1 Mengapa Tailwind CSS?
* **Pengembangan Lebih Cepat**: Tidak perlu berpindah bolak-balik antara file HTML dan CSS.
* **Konsistensi Desain**: Nilai spasi, warna, dan font sudah terstandarisasi.
* **Maintainable**: Mengubah desain satu elemen tidak akan merusak tampilan elemen di bagian lain website.
* **Bebas Pusing Nama Class**: Tidak perlu memikirkan nama class rumit seperti `.hero-card-inner-container-wrapper`.

### 2.2 Rumus Pola Pikir Tailwind untuk Pemula
Sebelum menghafal class, pahami rumus singkat Tailwind berikut:
1. **Skala Spacing (Kelipatan 4px):**  
   Angka di Tailwind dikalikan dengan 4px:
   * `p-1` = 4px | `p-2` = 8px | `p-4` = 16px | `p-6` = 24px | `p-10` = 40px
2. **Nilai Khusus / Arbitrary Value `[...]`:**  
   Jika butuh warna heksadesimal atau ukuran spesifik di luar palet bawaan, bungkus dengan kurung siku:
   * Warna: `bg-[#f6f7f3]`, `text-[#376b55]`
   * Ukuran: `max-w-[960px]`, `text-[0.95rem]`
3. **Sistem Responsif Mobile-First:**  
   Gaya tanpa awalan berlaku untuk layar HP ($0px+$). Awalan berlaku saat layar membesar:
   * `sm:` $\rightarrow$ Layar $\ge 640px$ (tablet kecil)
   * `md:` $\rightarrow$ Layar $\ge 768px$ (tablet / laptop)
   * `lg:` $\rightarrow$ Layar $\ge 1024px$ (desktop)

---

## 3. Contoh Penggunaan Tailwind dan Perbandingannya dengan CSS

Berikut adalah perbandingan langsung cara membuat komponen umum antarmuka web menggunakan CSS konvensional dibandingkan dengan Tailwind CSS:

### 3.1 Tombol Interaktif (Button & Hover)

#### A. Menggunakan CSS Biasa:
Memerlukan penamaan class baru dan aturan selector terpisah di file `.css`:
```css
.btn-primary {
  background-color: #2563eb;
  color: #ffffff;
  padding: 8px 16px;
  border-radius: 8px;
  font-weight: 700;
  border: none;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

.btn-primary:hover {
  background-color: #1d4ed8;
}
```
Penerapan di HTML:
```html
<button class="btn-primary">Kirim Pesan</button>
```

#### B. Menggunakan Tailwind CSS:
Cukup dituliskan langsung pada atribut class elemen HTML:
```html
<button class="bg-blue-600 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-lg transition-colors">
  Kirim Pesan
</button>
```

---

### 3.2 Kartu Profil (Card, Padding, & Shadow)

#### A. Menggunakan CSS Biasa:
```css
.card {
  max-width: 384px;
  margin-left: auto;
  margin-right: auto;
  background-color: #ffffff;
  padding: 24px;
  border-radius: 12px;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  border: 1px solid #f3f4f6;
}
```
Penerapan di HTML:
```html
<div class="card">
  <h3>Nama Anda</h3>
  <p>Deskripsi profil singkat.</p>
</div>
```

#### B. Menggunakan Tailwind CSS:
```html
<div class="max-w-sm mx-auto bg-white p-6 rounded-xl shadow-md border border-gray-100">
  <h3 class="text-xl font-bold text-gray-800">Nama Anda</h3>
  <p class="text-gray-600 mt-2 text-sm">Deskripsi profil singkat.</p>
</div>
```

---

### 3.3 Foto Profil Bulat Sempurna (Avatar)

#### A. Menggunakan CSS Biasa:
```css
.avatar {
  width: 128px;
  height: 128px;
  border-radius: 50%;
  object-fit: cover;
  flex-shrink: 0;
}
```
Penerapan di HTML:
```html
<img src="images/ning2.jpg" alt="Foto Profil" class="avatar">
```

#### B. Menggunakan Tailwind CSS:
```html
<img src="images/ning2.jpg" alt="Foto Profil" class="w-32 h-32 rounded-full object-cover shrink-0">
```

---

### 3.4 Bilah Navigasi Sejajar (Flexbox)

#### A. Menggunakan CSS Biasa:
```css
.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 24px;
  background-color: #ffffff;
  border-bottom: 1px solid #e5e7eb;
}

.nav-links {
  display: flex;
  gap: 16px;
}
```
Penerapan di HTML:
```html
<nav class="navbar">
  <a href="#" class="brand">Portofolio</a>
  <div class="nav-links">
    <a href="#about">About</a>
    <a href="#skills">Skills</a>
  </div>
</nav>
```

#### B. Menggunakan Tailwind CSS:
```html
<nav class="flex items-center justify-between px-6 py-4 bg-white border-b border-gray-200">
  <a href="#" class="font-bold text-gray-900">Portofolio</a>
  <div class="flex gap-4 text-sm text-gray-600">
    <a href="#about" class="hover:text-blue-600">About</a>
    <a href="#skills" class="hover:text-blue-600">Skills</a>
  </div>
</nav>
```

---

### 3.5 Tata Letak Responsif (Mobile-First Breakpoint)

#### A. Menggunakan CSS Biasa:
Harus membuat aturan media query terpisah di bagian bawah file CSS:
```css
.container-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 24px;
  padding: 24px;
}

@media (min-width: 768px) {
  .container-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
```
Penerapan di HTML:
```html
<div class="container-grid">
  <div>Kolom 1</div>
  <div>Kolom 2</div>
</div>
```

#### B. Menggunakan Tailwind CSS:
Cukup gunakan awalan breakpoint `md:` langsung pada tag container:
```html
<div class="grid grid-cols-1 md:grid-cols-2 gap-6 p-6">
  <div>Kolom 1</div>
  <div>Kolom 2</div>
</div>
```

---

## 4. Kamus Lengkap Class Tailwind (Portofolio Edition)

Berikut adalah kamus lengkap seluruh class Tailwind yang kita gunakan dalam pembuatan Web Portofolio:

### A. Tata Letak & Ukuran (Layout & Sizing)

| Class Tailwind | Padanan CSS | Fungsi & Penggunaan pada Portofolio |
| :--- | :--- | :--- |
| `max-w-[960px]` | `max-width: 960px;` | Membatasi lebar konten maksimal 960px agar rapi di monitor lebar |
| `min-h-[68px]` | `min-height: 68px;` | Menetapkan tinggi minimal bilah navigasi (navbar) |
| `min-h-screen` | `min-height: 100vh;` | Memastikan tinggi halaman minimal setinggi satu layar penuh |
| `w-36 h-36` | `width: 9rem; height: 9rem;` | Ukuran foto profil di layar HP (144px x 144px) |
| `sm:w-44 sm:h-44` | `@media ... { width: 11rem; height: 11rem; }` | Ukuran foto profil membesar menjadi 176px di layar $\ge 640px$ |
| `w-full` | `width: 100%;` | Mengisi lebar 100% penuh wadah induk |
| `shrink-0` | `flex-shrink: 0;` | Mencegah foto profil mengecil/gepeng jika teks di sampingnya panjang |

---

### B. Jarak & Ruang (Margin, Padding, Gap)

| Class Tailwind | Padanan CSS | Fungsi & Penggunaan pada Portofolio |
| :--- | :--- | :--- |
| `mx-auto` | `margin-left: auto; margin-right: auto;` | Memposisikan kontainer tepat di tengah horizontal |
| `px-6` | `padding-left: 24px; padding-right: 24px;` | Memberi margin aman di sisi kiri dan kanan layar |
| `py-10` | `padding-top: 40px; padding-bottom: 40px;` | Jarak dalam atas-bawah pada section About dan Skills |
| `py-14 sm:py-16` | Responsif padding vertikal (56px $\rightarrow$ 64px) | Ruang lega pada bagian atas dan bawah Hero section |
| `px-3.5 py-1.5` | `padding: 6px 14px;` | Bantalan dalam kotak lencana (badge) keterampilan |
| `mt-1` | `margin-top: 4px;` | Jarak kecil ke atas untuk judul |
| `mb-2` | `margin-bottom: 8px;` | Jarak kecil ke bawah untuk judul nama H1 |
| `gap-2.5` | `gap: 10px;` | Jarak antar kartu badge skill |
| `gap-4` | `gap: 16px;` | Jarak antar elemen navigasi saat membungkus |
| `gap-6` | `gap: 24px;` | Jarak spasi antar tautan menu di navbar |
| `gap-8 sm:gap-10` | `gap: 32px;` $\rightarrow$ `gap: 40px;` | Jarak antara foto profil dan teks perkenalan |

---

### C. Flexbox (Tata Letak 1 Dimensi)

| Class Tailwind | Padanan CSS | Fungsi & Penggunaan pada Portofolio |
| :--- | :--- | :--- |
| `flex` | `display: flex;` | Mengaktifkan flexbox pada kontainer |
| `flex-col` | `flex-direction: column;` | Menyusun elemen berbaris vertikal (dari atas ke bawah) |
| `flex-row` | `flex-direction: row;` | Menyusun elemen berjejer horizontal (ke samping) |
| `sm:flex-row` | Responsive flex direction | Di HP tersusun vertikal, di layar lebar berubah menjadi horizontal |
| `items-center` | `align-items: center;` | Meratakan elemen tepat di tengah secara vertikal |
| `items-start` | `align-items: flex-start;` | Menyelaraskan elemen rapat ke atas |
| `justify-between` | `justify-content: space-between;` | Memisahkan logo ke ujung kiri dan menu ke ujung kanan |
| `flex-wrap` | `flex-wrap: wrap;` | Otomatis melipat elemen ke baris baru jika ruang tidak cukup |

---

### D. CSS Grid (Tata Letak 2 Dimensi Kolom)

| Class Tailwind | Padanan CSS | Fungsi & Penggunaan pada Portofolio |
| :--- | :--- | :--- |
| `grid` | `display: grid;` | Mengaktifkan sistem layout grid |
| `grid-cols-1` | `grid-template-columns: repeat(1, minmax(0, 1fr));` | Menampilkan 1 kolom penuh di layar HP (judul di atas isi) |
| `md:grid-cols-[220px_1fr]` | `grid-template-columns: 220px 1fr;` | Pada layar laptop ($\ge 768px$), bagi 2 kolom: kiri 220px, kanan sisa ruang |

---

### E. Tipografi (Teks & Tulisan)

| Class Tailwind | Padanan CSS | Fungsi & Penggunaan pada Portofolio |
| :--- | :--- | :--- |
| `font-sans` | `font-family: ui-sans-serif, system-ui, ...;` | Menggunakan font keluarga modern tanpa kait (*sans-serif*) |
| `font-bold` | `font-weight: 700;` | Menebalkan teks |
| `text-xs` | `font-size: 0.75rem; (12px)` | Teks ekstra kecil untuk status eyebrow |
| `text-base` | `font-size: 1rem; (16px)` | Ukuran teks normal untuk paragraf dan link |
| `text-2xl` | `font-size: 1.5rem; (24px)` | Ukuran judul sub-bab H2 (About Me, Skills) |
| `text-4xl` | `font-size: 2.25rem; (36px)` | Ukuran judul nama H1 di layar ponsel |
| `sm:text-[2.6rem]` | `font-size: 2.6rem; (41.6px)` | Ukuran judul nama H1 membesar di monitor lebar |
| `text-[0.95rem]` | `font-size: 0.95rem; (15.2px)` | Ukuran proporsional teks menu dan kartu badge skill |
| `uppercase` | `text-transform: uppercase;` | Mengubah teks menjadi huruf kapital semua secara otomatis |
| `tracking-[0.08em]` | `letter-spacing: 0.08em;` | Menambah spasi renggang antar karakter huruf agar elegan |
| `leading-tight` | `line-height: 1.25;` | Merapatkan spasi baris teks pada judul besar |
| `leading-relaxed` | `line-height: 1.625;` | Memberi spasi baris yang renggang dan nyaman untuk paragraf |

---

### F. Warna & Latar Belakang (Color & Background)

| Class Tailwind | Padanan CSS | Fungsi & Penggunaan pada Portofolio |
| :--- | :--- | :--- |
| `bg-[#f6f7f3]` | `background-color: #f6f7f3;` | Warna dasar halaman krem lembut yang nyaman di mata |
| `bg-white` | `background-color: #ffffff;` | Latar belakang putih bersih untuk header dan kartu badge |
| `bg-[#dfe5df]` | `background-color: #dfe5df;` | Warna abu kehijauan lembut untuk placeholder foto |
| `text-[#24312b]` | `color: #24312b;` | Warna teks utama gelap kehijauan (tajam & kontras tinggi) |
| `text-[#376b55]` | `color: #376b55;` | Warna hijau botol elegan untuk aksen status dan judul nama |
| `text-[#68736d]` | `color: #68736d;` | Warna teks abu-abu sekunder untuk deskripsi minat dan link |

---

### G. Border & Bentuk (Borders & Shapes)

| Class Tailwind | Padanan CSS | Fungsi & Penggunaan pada Portofolio |
| :--- | :--- | :--- |
| `border` | `border-width: 1px; border-style: solid;` | Memberi garis tepi tipis di sekeliling kotak badge |
| `border-b` | `border-bottom-width: 1px;` | Garis pembatas tipis di bagian bawah header |
| `border-t` | `border-top-width: 1px;` | Garis pembatas horizontal di atas section About dan Skills |
| `border-[#dfe5df]` | `border-color: #dfe5df;` | Memberikan warna abu-abu kehijauan lembut pada garis border |
| `rounded` | `border-radius: 0.25rem; (4px)` | Sudut kotak badge sedikit melengkung halus |
| `rounded-full` | `border-radius: 9999px; (50%)` | **Kunci foto bulat:** Mengubah kotak foto menjadi lingkaran penuh |
| `object-cover` | `object-fit: cover;` | Memastikan gambar mengisi lingkaran penuh tanpa distorsi/gepeng |

---

### H. Interaktivitas & Efek (Hover & Smooth Scroll)

| Class Tailwind | Padanan CSS | Fungsi & Penggunaan pada Portofolio |
| :--- | :--- | :--- |
| `hover:text-[#376b55]` | `:hover { color: #376b55; }` | Mengubah warna link menjadi hijau saat disentuh kursor |
| `transition-colors` | `transition-property: color;` | Animasi perpindahan warna yang lembut (tidak kaku) |
| `scroll-smooth` | `html { scroll-behavior: smooth; }` | Halaman bergeser mulus saat link anchor (`#about`, dll.) diklik |
| `scroll-mt-6` | `scroll-margin-top: 1.5rem;` | Memberi jarak aman di atas agar judul tidak tertutup saat scroll |

---

## 5. Template Latihan Praktikum

Untuk sesi praktik koding langsung, repositori ini telah dilengkapi dengan template portofolio yang siap digunakan:

**Jalur Template:** [`Modul/Modul-3-Tailwind-Dasar/TailWind-Template/`](TailWind-Template/)
* **`TailWind-Template/index.html`**: Kerangka HTML bersih dengan atribut `class=""` kosong yang siap kamu ketik bersama instruktur.
* **`TailWind-Template/images/ning2.jpg`**: Aset foto profil yang digunakan di Hero section.

---

## 6. Referensi
* [Dokumentasi Resmi Tailwind CSS](https://tailwindcss.com/docs)
* [Tailwind CSS Cheat Sheet](https://nerdcave.com/tailwind-cheat-sheet)
