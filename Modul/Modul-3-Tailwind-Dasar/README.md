# Modul 3: Styling Cepat & Modern dengan Tailwind CSS

## 1. Tujuan Praktikum
1. Memahami konsep Utility-First CSS Framework menggunakan Tailwind CSS.
2. Mampu mengintegrasikan Tailwind CSS melalui CDN pada file HTML.
3. Menguasai class-class utilitas populer untuk typography, spacing (margin/padding), flexbox/grid, background, rounded, dan shadow.
4. Menerapkan pseudo-class modifier (seperti `hover:`, `focus:`) langsung pada atribut class HTML.

---

## 2. Teori Dasar

Tailwind CSS adalah framework CSS berparadigma **Utility-First**. Berbeda dengan pendekatan tradisional yang mengharuskan pembuatan file `.css` terpisah dan penamaan class kustom, Tailwind menyediakan ribuan kelas utilitas siap pakai (misal: `flex`, `pt-4`, `text-center`, `rotate-90`) yang dapat digabungkan langsung di dalam atribut `class="..."`.

### 2.1 Mengapa Tailwind CSS?
* **Pengembangan Lebih Cepat**: Tidak perlu berpindah bolak-balik antara file HTML dan CSS.
* **Konsistensi Desain**: Nilai spasi, warna, dan font sudah terstandarisasi.
* **Maintainable**: Mengubah desain satu elemen tidak akan merusak tampilan elemen di bagian lain website.

### 2.2 Anatomi Utility Classes Populer
| Kategori | Nama Class Tailwind | Fungsi CSS Ekuivalen |
| --- | --- | --- |
| **Typography** | `text-3xl`, `font-bold`, `text-blue-600`, `text-center` | Font size, weight, color, alignment |
| **Spacing** | `p-6` (padding), `mb-8` (margin-bottom), `mx-auto` (horizontal auto) | Spacing dalam dan luar |
| **Sizing** | `max-w-md`, `w-full`, `h-64` | Batasan lebar dan tinggi |
| **Borders & Corners** | `rounded-xl`, `border`, `border-gray-200` | Sudut melengkung & garis tepi |
| **Effects** | `shadow-lg`, `shadow-xl`, `transition-all` | Efek bayangan & animasi transisi |
| **Pseudo-Classes** | `hover:bg-blue-700`, `hover:shadow-2xl` | Mengubah gaya saat disentuh kursor |

---

## 3. Alat & Persiapan
* **Text Editor**: Visual Studio Code / Antigravity IDE.
* **Ekstensi Disarankan**: `Tailwind CSS IntelliSense`.
* File contoh: [index.html](file:///C:/Users/justl/.gemini/antigravity/scratch/template-web-portofolio/Modul/Modul-3-Tailwind-Dasar/index.html).

---

## 4. Langkah-Langkah Praktikum

1. Buka [index.html](file:///C:/Users/justl/.gemini/antigravity/scratch/template-web-portofolio/Modul/Modul-3-Tailwind-Dasar/index.html).
2. Perhatikan script CDN pada baris `<script src="https://cdn.tailwindcss.com"></script>`.
3. Analisis elemen card:
   ```html
   <div class="max-w-md mx-auto bg-white p-6 rounded-xl shadow-lg hover:shadow-xl transition-shadow">
   ...
   </div>
   ```
4. Buka halaman di browser dengan Live Server.
5. Lakukan eksperimen:
   - Ubah warna tombol dari `bg-blue-500` menjadi warna lain (contoh: `bg-emerald-500`, `bg-purple-600`).
   - Ubah `rounded-xl` menjadi `rounded-full`.
   - Tambahkan efek `hover:scale-105` pada tombol untuk animasi zoom saat disentuh kursor.

---

## 5. Tugas Modul
1. Buat satu halaman Hero Section atau Card Profil portofolio modern murni menggunakan class Tailwind CSS.
2. Elemen wajib:
   - Navbar sederhana menggunakan Flexbox (`flex justify-between items-center`).
   - Foto profil dengan sudut bulat penuh (`rounded-full`) dan border tebal.
   - Tombol CTA ("Hubungi Saya") dengan interaksi hover warna dan transisi mulus.

---

## Referensi
* [Dokumentasi Resmi Tailwind CSS](https://tailwindcss.com/docs)
* [Tailwind CSS Cheat Sheet](https://nerdcave.com/tailwind-cheat-sheet)
