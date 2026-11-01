# Lab6Web — Praktikum 6: JavaScript DOM dan Event Handling
 
**Mata kuliah:** Pemrograman Web · **Pertemuan:** 7
**Nama / NIM / Kelas:** _(isi sendiri)_
 
## Tujuan
1. Memahami DOM sebagai representasi dokumen HTML yang bisa diakses JavaScript.
2. Memilih elemen dengan id, class, dan selector CSS.
3. Mengubah teks, atribut, kelas CSS, dan gaya elemen.
4. Menangani event dengan `addEventListener()`.
5. Membuat validasi form dengan pesan sesuai kondisi input.
6. Membuat halaman interaktif dengan minimal tiga fungsi yang berjalan benar.
## Struktur file
```
lab6_dom_event/
├── index.html   # struktur halaman (Latihan 1–6 + Mini Project)
├── style.css    # tampilan, responsif desktop & mobile
├── script.js    # seluruh logika DOM & event
├── README.md
└── screenshots/ # letakkan screenshot di sini
```
 
## Cara menjalankan
1. Unduh/clone repository `Lab6Web`.
2. Buka `index.html` di browser modern (Chrome/Edge/Firefox). Tidak perlu server.
3. Buka Developer Tools → Console untuk memeriksa error.
## Langkah kerja
| Latihan | Isi | Konsep utama |
|---|---|---|
| 1 | Judul dan paragraf diubah saat halaman dimuat | `getElementById`, `textContent` |
| 2 | Klik tombol → paragraf menampilkan waktu klik | `addEventListener("click")`, `Date` |
| 3 | Tombol mengganti gaya paragraf | `classList.toggle` |
| 4 | Penghitung karakter saat mengetik | event `input`, `value.length` |
| 5 | Validasi nama, email, usia | `submit`, `preventDefault`, regex |
| 6 | To-do list: tambah, tandai selesai | `createElement`, `append`, `appendChild` |
| Mini Project | Pendaftaran workshop | validasi, ringkasan langsung, pesan, reset |
 
### Mini Project — fungsi interaktif
1. **Validasi** nama (min. 3 karakter), email (format), dan sesi (wajib dipilih), dijalankan saat `submit` dan `blur`.
2. **Penghitung karakter** kolom alasan dan **ringkasan langsung** di panel kanan (event `input`, `change`).
3. **Pesan error per kolom** dan **pesan sukses/gagal** di halaman.
4. **Tombol "Hapus input"** untuk mengosongkan form dan semua pesan.
### Eksperimen mandiri
1. **Hapus item To-do** — tombol "Hapus" pada tiap item memanggil `item.remove()`.
2. **Nama minimal 3 karakter** — ditambahkan pada Latihan 5 dan Mini Project.
3. **Event `change` pada dropdown sesi** — sesi terpilih ditampilkan di bawah dropdown dan di ringkasan.
4. **Sembunyikan/tampilkan paragraf** — `classList.toggle("tersembunyi")` dengan CSS `display: none`.
5. **Script tanpa `defer` di `<head>`** — lihat penjelasan di bawah.
#### Penjelasan Eksperimen 5
Tanpa `defer`, browser menghentikan parsing HTML untuk mengunduh dan menjalankan `script.js` saat tag `<script>` di `<head>` ditemukan. Pada saat itu `<body>` belum dibaca, sehingga `document.getElementById("judul")` mengembalikan `null`. Baris berikutnya seperti `judul.textContent = ...` memunculkan error `Cannot set properties of null` dan sisa script tidak berjalan. Solusinya: pakai `defer`, pindahkan `<script>` ke akhir `<body>`, atau bungkus kode dalam `DOMContentLoaded`.
 
## Pengujian form (isi screenshot)
| No | Skenario | Input | Hasil yang diharapkan |
|---|---|---|---|
| 1 | Semua kosong | — | "Nama wajib diisi." |
| 2 | Nama kosong | email & usia valid | "Nama wajib diisi." |
| 3 | Nama terlalu pendek | `Al` | "Nama minimal terdiri dari 3 karakter." |
| 4 | Email tidak valid | `budi@` | "Masukkan email yang valid." |
| 5 | Usia di bawah 17 | `16` | "Usia harus berupa bilangan bulat 17–100." |
| 6 | Usia desimal | `20.5` | pesan usia tidak valid |
| 7 | Semua valid | `Budi`, `budi@mail.com`, `20` | "Validasi berhasil. Form siap diproses." |
 
Screenshot: `screenshots/latihan1.png` … `latihan6.png`, `form-invalid.png`, `form-valid.png`, `mini-project.png`.
 
## Jawaban pertanyaan evaluasi
1. **DOM** adalah representasi dokumen HTML sebagai pohon objek (node) yang bisa dibaca dan diubah JavaScript. Manfaatnya: memilih elemen, mengubah konten, atribut, dan gaya, serta merespons tindakan pengguna tanpa memuat ulang halaman.
2. `getElementById()` mengambil satu elemen berdasarkan id. `querySelector()` mengambil elemen **pertama** yang cocok dengan selector CSS. `querySelectorAll()` mengambil **semua** elemen yang cocok sebagai `NodeList`.
3. `addEventListener()` menghubungkan sebuah event dengan fungsi yang dijalankan saat event terjadi, dan boleh dipasang lebih dari satu pada elemen yang sama. Contoh event: `click`, `input`, `submit` (juga `change`, `keydown`, `mouseover`).
4. `event.preventDefault()` mencegah perilaku bawaan submit, yaitu mengirim form dan memuat ulang halaman. Dengan begitu data bisa diperiksa dulu dan pesan kesalahan tidak hilang.
5. `textContent` memasukkan teks apa adanya, sehingga aman untuk teks pengguna. `innerHTML` mem-parsing string sebagai HTML sehingga berguna untuk markup, tetapi jika diisi teks pengguna yang tidak dipercaya, bisa terjadi XSS (misalnya `<img src=x onerror=...>`).
6. `classList.toggle("x")` menambahkan kelas jika belum ada dan menghapusnya jika sudah ada. Satu tombol cukup untuk beralih antara dua tampilan, karena gayanya diatur di CSS.
7. Skenario pengujian: (a) semua input kosong, (b) email tanpa `@` atau domain, (c) usia di bawah batas/di atas batas/bukan bilangan bulat, (d) nama hanya spasi, (e) semua input valid.

 

Claude selesai menulis balasan
