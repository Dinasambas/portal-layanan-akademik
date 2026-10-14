# Portal Layanan Akademik

Tugas Pertemuan 5 – Responsive & Accessible Web Client.
Satu halaman web client (HTML + CSS, tanpa JavaScript) untuk mengajukan dokumen akademik.

- **URL aplikasi:** _isi dengan link GitHub Pages Anda_
- **Repositori:** _isi dengan link GitHub Anda_

## Struktur proyek

```
index.html
css/styles.css
img/logo.svg            (dekoratif)
img/alur-layanan.svg    (informatif)
evidence/               (bukti pengujian DevTools)
README.md
```

## Keputusan desain

| Aspek | Keputusan | Alasan |
|---|---|---|
| Semantik | `header`, `nav`, `main`, 3 `section`, `article` per kartu, `footer` | Landmark membantu screen reader berpindah area |
| Heading | h1 (beranda) → h2 (tiap section) → h3 (judul kartu) | Hierarki mengikuti struktur informasi, bukan ukuran |
| Layout | Mobile-first; kartu pakai CSS Grid (1 → 2 → 4 kolom), nav & header pakai Flexbox | Mulai dari satu kolom, tambah kolom saat ruang cukup |
| Breakpoint | `40em` dan `64em` | Dipilih saat kartu mulai terlalu lebar/sempit, bukan berdasarkan nama perangkat |
| Form | Label terasosiasi (`for`/`id`), `type="email"`, `required`, `pattern` NIM, `minlength`/`maxlength`, `fieldset`+`legend` untuk radio, `<button type="submit">` | Elemen native lebih dulu sebelum ARIA |
| Keyboard | Skip link, `:focus-visible` outline 3 px, target sentuh min. 44 px | Semua kontrol dapat dicapai dan fokusnya terlihat |
| Kontras | Teks gelap `#12263a` di `#f3f6f4`; putih di `#0b5d50` (> 7:1) | Memenuhi WCAG AA |
| Font | System font stack | Tanpa resource eksternal, jadi Network bersih dari request gagal |

## Gambar dan alt text

| Gambar | Jenis | alt | Alasan |
|---|---|---|---|
| `logo.svg` | Dekoratif | `""` (kosong) | Nama portal sudah ada sebagai teks di sebelahnya, sehingga screen reader tidak membaca informasi ganda |
| `alur-layanan.svg` | Informatif | Deskripsi alur 3 langkah | Menyampaikan alur pengajuan |

## Hasil pengujian DevTools

Pengujian otomatis (Chromium, mode responsif) pada file ini:

| Viewport | Horizontal scroll | Request gagal (Network) |
|---|---|---|
| 360 px | Tidak ada | 0 |
| 768 px | Tidak ada | 0 |
| 1280 px | Tidak ada | 0 |

Screenshot ada di folder `evidence/`.

**Lengkapi sendiri dengan DevTools di browser Anda** (disarankan, agar bukti sesuai tugas):

1. **Elements/Inspector:** periksa struktur DOM dan CSS aktif pada `.cards` di tiap lebar. Catat perubahan `grid-template-columns`.
2. **Responsive Mode:** uji 360, 768, dan 1280 px. Screenshot masing-masing.
3. **Network:** reload (Ctrl+Shift+R), pastikan `index.html`, `styles.css`, dan 2 SVG berstatus 200. Screenshot.
4. **Accessibility:** buka Accessibility tree. Pastikan landmark, heading, dan label form terbaca. Jalankan Lighthouse (kategori Accessibility) bila tersedia.
5. **Keyboard:** tekan Tab dari awal, pastikan urutan logis dan fokus terlihat.
6. **Validasi form:** kirim form kosong, lalu isi email tanpa `@`. Catat pesan validasi browser.

### Temuan debugging
_Tulis temuan Anda di sini (contoh: overflow yang sempat muncul, perbaikan kontras, dst.). Jika tidak ada masalah, tulis itu dan sebutkan apa yang sudah diperiksa._

## Menjalankan dan deploy

Buka `index.html` di browser. Untuk GitHub Pages: push ke repositori, lalu **Settings → Pages → Deploy from a branch → `main` / root**.

Catatan: form memakai `method="get"` dan `action="#permohonan"` karena tugas tanpa JavaScript/backend. Data hanya tampil di URL setelah submit, tidak dikirim ke server.
