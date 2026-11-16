# Arena 3D – TV Olahraga Internasional

Situs statis 3D (Three.js) berisi karusel channel olahraga. Seret untuk memutar, klik kartu atau tombol **Tonton** untuk memutar siaran. Tidak perlu build; cukup satu file `index.html`.

## Mengisi channel

Edit array `CHANNELS` di `index.html`:

```js
{ name:"Nama Channel", sport:"Keterangan", color:"#1f6fb2", type:"youtube", id:"VIDEO_ID" }
{ name:"Nama Channel", sport:"Keterangan", color:"#1f6fb2", type:"youtube", channel:"UCxxxxxxxx" } // live channel
{ name:"Nama Channel", sport:"Keterangan", color:"#1f6fb2", type:"hls",     url:"https://.../index.m3u8" }
{ name:"Nama Channel", sport:"Keterangan", color:"#1f6fb2", type:"embed",   url:"https://.../embed" }
{ name:"Nama Channel", sport:"Keterangan", color:"#1f6fb2", type:"link",    url:"https://situs-resmi.example" }
```

Jenis `link` membuka situs resmi di tab baru, cocok untuk siaran yang tidak boleh di-embed.

Gunakan hanya siaran yang sah: live stream resmi di YouTube, atau stream HLS yang penyedianya mengizinkan penyiaran ulang. Stream HLS dari server lain harus mengaktifkan CORS agar bisa diputar di browser.

## Deploy ke GitHub Pages

1. Buat repo baru di GitHub, lalu unggah `index.html` dan `README.md` ke branch `main`.
2. Buka **Settings → Pages**.
3. Pada **Build and deployment**, pilih **Deploy from a branch**, branch `main`, folder `/ (root)`, lalu **Save**.
4. Tunggu satu sampai dua menit. Situs muncul di `https://USERNAME.github.io/NAMA-REPO/`.

## Deploy ke Cloudflare Pages

1. Pastikan repo sudah ada di GitHub (langkah di atas).
2. Di dashboard Cloudflare, buka **Workers & Pages → Create → Pages → Connect to Git**.
3. Pilih repo tadi, lalu isi:
   - Framework preset: **None**
   - Build command: *(kosongkan)*
   - Build output directory: `/`
4. Klik **Save and Deploy**. Situs tersedia di `https://NAMA-PROYEK.pages.dev`, dan Anda bisa menambahkan domain sendiri di tab **Custom domains**.

Alternatif tanpa Git: pada **Create → Pages → Upload assets**, seret folder ini langsung.

## Catatan

- Three.js dan hls.js dimuat dari cdnjs; font dari Google Fonts.
- Putaran dengan keyboard: tombol panah kiri/kanan, `Enter` untuk menonton, `Esc` untuk menutup.
