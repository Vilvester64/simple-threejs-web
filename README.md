# Tugas Komputer Grafika — #470 Leafeon (Three.js)

Visualisasi 3D interaktif karakter Pokémon **Leafeon (#470)** menggunakan **Three.js (WebGL)** yang disusun dari berbagai objek geometris **Quadric** dan **Kurva Parametrik**.

---

## Struktur Folder

```text
1411/
├── README.md
└── komputer graafika/
    ├── index.html    # Kode utama (HTML, CSS, Three.js Scene & Model Builder)
    └── GAMBAR.jpeg   # Gambar referensi 2D Leafeon (#470)
```

---

## Prasyarat

- **Koneksi Internet**: Dibutuhkan saat membuka halaman karena library `three`, `OrbitControls`, dan `lil-gui` dimuat melalui CDN (`https://unpkg.com/three@0.160.0/`).
- **Browser Modern**: Google Chrome, Microsoft Edge, Firefox, atau Brave yang mendukung WebGL & `<script type="importmap">`.

---

## Cara Menjalankan Project

Pilih salah satu dari 4 cara berikut:

### Cara 1: Menggunakan Ekstensi Live Server di VS Code (Direkomendasikan)
1. Buka folder project ini di **VS Code**.
2. Pastikan ekstensi **Live Server** (oleh Ritwick Dey) sudah terinstal.
3. Klik kanan pada file `komputer graafika/index.html` lalu pilih **"Open with Live Server"**.
4. Browser akan otomatis terbuka di alamat `http://127.0.0.1:5500/komputer%20graafika/index.html`.

### Cara 2: Menggunakan Node.js (`npx serve` / `http-server`)
Jika sudah menginstal **Node.js**, jalankan perintah berikut di terminal (PowerShell / CMD) dari folder root project:

```powershell
npx --yes serve "komputer graafika"
```
Lalu buka URL yang muncul di terminal (biasanya `http://localhost:3000`) pada browser.

### Cara 3: Menggunakan Python HTTP Server
Jika memiliki **Python 3** terinstal, jalankan perintah berikut di terminal:

```powershell
python -m http.server 8080 --directory "komputer graafika"
```
Lalu buka `http://localhost:8080` di browser.

### Cara 4: Membuka Langsung File `index.html`
1. Buka **File Explorer** dan masuk ke folder `komputer graafika`.
2. Klik dua kali (*double-click*) pada `index.html` untuk membukanya langsung di browser.
*(Catatan: Jika ingin menggunakan fitur muat tekstur/gambar lokal, disarankan menggunakan Cara 1–3 melalui local server agar tidak terkena pembatasan CORS browser).*

---

## Fitur Utama & Kontrol Interaktif

### 1. Objek Quadric & Kurva Penyusun Model
- **Sphere**: Pupil mata, highlight kilau mata, detail jari kaki (`paw`).
- **Ellipsoid**: Kepala, pipi, moncong, hidung, mata, telinga daun, `headLeaf`, badan, dada, daun dada/bahu/kaki, telapak kaki (`paw`), `tailLeaf`, serta batu & semak diorama.
- **Cylinder**: Tungkai kaki depan & kaos kaki, serta podium diorama hutan.
- **Hyperboloid of One Sheet (Parametric Surface)**: Leher, paha/betis kaki belakang, dan pangkal ekor.
- **CatmullRomCurve3 + TubeGeometry**: Tulang dan urat daun pada telinga, lekuk jambul dahi, serta urat daun ekor bercabang.

### 2. Kontrol Kamera (Mouse & Toolbar)
- **Klik Kiri + Geser**: Memutar kamera (*Orbit*).
- **Scroll Mouse**: Memperbesar / memperkecil (*Zoom*).
- **Klik Kanan + Geser**: Menggeser titik fokus kamera (*Pan*).
- **Preset Kamera**: Tombol `Reset`, `Depan`, `Samping`, `Atas`, dan `Wajah` untuk berpindah sudut pandang secara halus.

### 3. Fitur Interaktif & Akademis
- **Inspeksi 2-Arah (Raycasting 3D ↔ Tabel)**:
  - Arahkan kursor (*hover*) atau klik bagian tubuh Leafeon di 3D viewer untuk menyorot bagian tersebut dan otomatis menyorot barisnya di tabel spesifikasi.
  - Klik baris pada tabel spesifikasi di sebelah kanan untuk menyorot bagian terkait di model 3D.
- **Filter Primitif**: Gunakan tombol filter (`Semua`, `Sphere`, `Ellipsoid`, `Cylinder`, `Hyperboloid`, `Curve`) di atas tabel untuk memfilter daftar dan mengisolasi bentuk geometris tertentu pada model 3D.
- **Slider Explode**: Geser slider `Explode` di toolbar bawah untuk memisahkan tiap kelompok komponen tubuh agar struktur objek Quadric terlihat jelas.
- **Mode Animasi**:
  - `Idle`: Animasi bernapas, mata berkedip, serta goyangan halus pada daun dan ekor.
  - `Jalan`: Animasi langkah kaki (*walk cycle*).
  - `Leaf Storm`: Animasi serangan dengan pusaran partikel daun berkecepatan tinggi.
- **Mode Pencahayaan**: `Siang` (*Forest Day*), `Sore` (*Golden Sunset*), dan `Malam` (*Firefly Night*).
- **Screenshot PNG**: Unduh hasil tangkapan layar canvas 3D secara langsung dalam format `.png`.
- **Muat Gambar 3D**: Unggah gambar referensi dari komputer untuk ditampilkan sebagai latar (*background*) sekaligus *3D Sprite Billboard* di dalam scene.
