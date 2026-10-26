# 🎯 PLAN: README.md Animatif Bertema VALORANT (Colorful Splash Style)

> Dokumen perencanaan lengkap untuk membuat README GitHub yang beranimasi, penuh warna, dengan gaya *splash art* ala Valorant: sudut tajam, garis diagonal, kontras tinggi, neon merah-cyan-ungu-kuning, tipografi tebal.
>
> **Catatan hak cipta:** Valorant adalah merek dagang Riot Games. Rencana ini hanya meniru **gaya visual** (palet, bentuk, tipografi, istilah). Jangan memakai logo resmi, artwork agent, atau aset game. Semua visual dibuat sendiri lewat SVG/CSS sehingga aman untuk repo publik.

---

## 0. ISI DULU: Data yang Dibutuhkan dari Kamu

Saya belum punya daftar project dan tech stack kamu, jadi seluruh bagian bertanda `{{...}}` di bawah adalah **placeholder**. Isi tabel ini, lalu tinggal ganti di template.

| Data | Contoh | Isi Kamu |
|---|---|---|
| Username GitHub | `rafiqdev` | `{{USERNAME}}` |
| Nama tampilan / codename | `RAFIQ // DUELIST` | `{{CODENAME}}` |
| Jenis README | Profil (`USERNAME/USERNAME`) atau README satu repo | `{{TIPE}}` |
| Role utama | Fullstack / Backend / Mobile / Data / DevOps | `{{ROLE}}` |
| Tagline (3-5 baris untuk typing effect) | "Building clean APIs", "Shipping fast" | `{{TAGLINE}}` |
| Bahasa & tech yang dikuasai + level | Laravel (Expert), React (Advanced) | `{{TECH_LIST}}` |
| Daftar project (nama, deskripsi, stack, link, status) | lihat Bagian 7 | `{{PROJECTS}}` |
| Kontak (LinkedIn, email, IG, portfolio) | | `{{CONTACTS}}` |
| Lokasi / zona waktu | Surabaya, WIB (UTC+7) | `{{LOCATION}}` |

> Tips: kalau mau, kirim saja daftar project + tech kamu, nanti saya isi semua placeholder dan hasilkan `README.md` final.

---

## 1. Konsep & Visi

**Nama konsep:** `PROJECT: LOADOUT`

Ide besarnya: README diperlakukan seperti **layar pemilihan agent + loadout** di game tactical shooter.

| Elemen Valorant | Dipetakan ke README |
|---|---|
| Agent select screen | Header + intro profil |
| Agent role (Duelist/Controller/Initiator/Sentinel) | Kategori tech (Frontend/Backend/DevOps/Database) |
| Abilities (C, Q, E, X) | 4 skill utama |
| Rank (Iron → Radiant) | Level kemampuan per tech |
| Weapon skin / loadout | Kartu project |
| Match history | Aktivitas GitHub, commit, streak |
| Battle pass | Roadmap belajar / sertifikasi |
| Spike plant/defuse | Call to action (hire me / contact) |
| Kill feed | Daftar update/rilis terbaru |

**Mood:** agresif, cepat, rapi, kontras tinggi, tetap terbaca di dark dan light mode GitHub.

---

## 2. Design System

### 2.1 Palet Warna (Colorful Splash)

| Nama | Hex | Penggunaan |
|---|---|---|
| Valorant Red | `#FF4655` | Aksen utama, judul, garis diagonal |
| Deep Navy | `#0F1923` | Latar utama |
| Off-White | `#ECE8E1` | Teks utama |
| Dark Slate | `#1F2326` | Panel/kartu |
| Neon Cyan | `#00E5FF` | Ikon, highlight, link |
| Splash Purple | `#A855F7` | Gradien, kategori Controller |
| Splash Yellow | `#F5C518` | Peringatan, rank Radiant, bintang |
| Splash Green | `#3DDC84` | Status "Online"/stable |
| Splash Pink | `#FF6BD6` | Gradien dekoratif |
| Splash Orange | `#FF8A3D` | Gradien dekoratif |

**Gradien splash utama:**
`#FF4655 → #FF6BD6 → #A855F7 → #00E5FF → #F5C518`

### 2.2 Warna per Role (seperti warna agent)

| Role | Warna | Kategori tech |
|---|---|---|
| DUELIST | `#FF4655` | Frontend / UI |
| CONTROLLER | `#A855F7` | Backend / API |
| INITIATOR | `#00E5FF` | Database / Data |
| SENTINEL | `#3DDC84` | DevOps / Security / Testing |

### 2.3 Tipografi
- GitHub memblokir font eksternal di dalam SVG yang dimuat lewat `<img>`. Gunakan stack aman:
  `Impact, 'Arial Black', 'Segoe UI', Arial, sans-serif` untuk judul, dan `'Courier New', monospace` untuk teks teknis.
- Judul: huruf kapital, tebal, `letter-spacing` lebar.
- Typing effect memakai layanan yang sudah menyediakan font (Fira Code).

### 2.4 Bahasa Bentuk
- Sudut tajam (tanpa rounded besar), potongan diagonal (`skewX(-20)`).
- Garis "slash" diagonal sebagai pemisah.
- Panel dengan sudut terpotong (polygon).
- Animasi cepat dan tegas (0.4–1.2 detik), lalu loop lembut.

---

## 3. Batasan Teknis GitHub (Wajib Diketahui)

| Hal | Status | Konsekuensi |
|---|---|---|
| JavaScript di README/SVG | ❌ Diblokir | Semua animasi harus SVG (SMIL/CSS) atau GIF/WebP |
| SVG via `<img src>` | ✅ | CSS animation dan SMIL jalan |
| SVG inline di Markdown | ❌ Tidak dirender | Simpan sebagai file `.svg` lalu panggil dengan `<img>` |
| Font eksternal di SVG | ❌ | Pakai font sistem |
| Gambar eksternal di dalam SVG | ❌ | Embed sebagai base64 atau gambar vektor |
| `<style>` / `class` di Markdown HTML | ❌ Di-strip | Styling hanya lewat atribut yang diizinkan (`align`, `width`, `height`) |
| Layanan pihak ketiga (stats, typing) | ⚠️ Bisa down/rate-limit | Siapkan fallback hasil generate lewat GitHub Actions |
| Dark/light mode | ✅ | Pakai `<picture>` + `prefers-color-scheme` bila perlu dua versi |
| Ukuran | ⚠️ | Tiap SVG sebaiknya < 100 KB, GIF < 5 MB |

**Strategi animasi (prioritas):**
1. **SVG animasi buatan sendiri** (utama, ringan, tajam, tema bisa dikontrol penuh).
2. **Layanan dinamis** (capsule-render, typing-svg, stats) untuk konten yang berubah.
3. **GitHub Actions** (snake, generate stats SVG) supaya tidak bergantung server orang lain.
4. **GIF/WebP** hanya untuk demo project (screen recording).

---

## 4. Struktur Folder Repo

```
.
├── README.md
├── plan.md
├── assets/
│   ├── header.svg            # banner animasi splash
│   ├── divider.svg           # garis pemisah slash animasi
│   ├── agent-card.svg        # kartu profil ala agent select
│   ├── rank-frontend.svg     # bar skill per kategori
│   ├── rank-backend.svg
│   ├── rank-data.svg
│   ├── rank-devops.svg
│   ├── project-1.svg         # kartu project (loadout)
│   ├── project-2.svg
│   ├── footer.svg
│   └── demo/
│       └── project-1.gif     # opsional demo
├── .github/
│   └── workflows/
│       ├── snake.yml         # animasi ular contribution
│       └── stats.yml         # generate stats SVG mandiri (opsional)
└── scripts/
    └── build-svg.mjs         # opsional: generate SVG dari data JSON
```

---

## 5. Blueprint Layout README (Urutan Section)

```
 1. HEADER BANNER         (header.svg animasi)
 2. TYPING TAGLINE        (typing-svg)
 3. BADGE BAR             (views, followers, status)
 4. AGENT CARD            (profil singkat)
 5. DIVIDER SLASH
 6. ABILITIES             (C / Q / E / X = 4 keahlian utama)
 7. LOADOUT: TECH STACK   (ikon + rank per role)
 8. DIVIDER SLASH
 9. FEATURED MISSIONS     (project unggulan = weapon skin cards)
10. MATCH HISTORY         (stats, streak, top languages, activity graph)
11. SNAKE / KILL FEED     (animasi + update terbaru)
12. BATTLE PASS           (roadmap belajar & sertifikasi)
13. CONTACT / PLANT SPIKE (CTA)
14. FOOTER WAVE           (capsule footer)
```

---

## 6. Komponen Detail + Kode

### 6.1 Header Banner (SVG Animasi Splash)

Simpan sebagai `assets/header.svg`. Fitur: latar navy, 5 garis diagonal warna splash yang menyapu masuk, judul yang "slam" masuk, garis merah berkedip, titik partikel mengambang.

```svg
<svg xmlns="http://www.w3.org/2000/svg" width="1000" height="260" viewBox="0 0 1000 260">
  <defs>
    <linearGradient id="splash" x1="0" y1="0" x2="1" y2="0">
      <stop offset="0" stop-color="#FF4655"/>
      <stop offset="0.25" stop-color="#FF6BD6"/>
      <stop offset="0.5" stop-color="#A855F7"/>
      <stop offset="0.75" stop-color="#00E5FF"/>
      <stop offset="1" stop-color="#F5C518"/>
    </linearGradient>
    <clipPath id="frame"><rect width="1000" height="260"/></clipPath>
    <style>
      .title { font: 900 64px Impact, 'Arial Black', sans-serif; letter-spacing: 6px; fill: #ECE8E1;
               animation: slam 0.7s cubic-bezier(.2,1.4,.4,1) both; transform-origin: 70px 150px; }
      .sub   { font: 700 18px 'Courier New', monospace; letter-spacing: 8px; fill: #00E5FF;
               animation: fade 1s 0.7s both; }
      .slash { animation: sweep 1.1s cubic-bezier(.2,.8,.2,1) both; }
      .s2 { animation-delay: .1s } .s3 { animation-delay: .2s }
      .s4 { animation-delay: .3s } .s5 { animation-delay: .4s }
      .bar   { animation: pulse 1.6s ease-in-out infinite; }
      .dot   { animation: floaty 4s ease-in-out infinite; }
      @keyframes slam  { from { transform: scale(2.2); opacity: 0 } to { transform: scale(1); opacity: 1 } }
      @keyframes fade  { from { opacity: 0 } to { opacity: 1 } }
      @keyframes sweep { from { transform: translateX(-1200px) } to { transform: translateX(0) } }
      @keyframes pulse { 0%,100% { opacity: 1 } 50% { opacity: .25 } }
      @keyframes floaty{ 0%,100% { transform: translateY(0) } 50% { transform: translateY(-14px) } }
    </style>
  </defs>
  <g clip-path="url(#frame)">
    <rect width="1000" height="260" fill="#0F1923"/>
    <!-- garis splash diagonal -->
    <polygon class="slash"    points="560,0 700,0 520,260 380,260" fill="#FF4655" opacity=".95"/>
    <polygon class="slash s2" points="680,0 760,0 580,260 500,260" fill="#A855F7" opacity=".9"/>
    <polygon class="slash s3" points="760,0 850,0 670,260 580,260" fill="#00E5FF" opacity=".9"/>
    <polygon class="slash s4" points="850,0 920,0 740,260 670,260" fill="#F5C518" opacity=".9"/>
    <polygon class="slash s5" points="920,0 1000,0 1000,40 820,260 740,260" fill="#FF6BD6" opacity=".9"/>
    <!-- overlay gelap supaya teks terbaca -->
    <polygon points="0,0 600,0 420,260 0,260" fill="#0F1923" opacity=".88"/>
    <!-- bar aksen -->
    <rect class="bar" x="40" y="70" width="8" height="120" fill="url(#splash)"/>
    <text class="title" x="70" y="150">{{CODENAME}}</text>
    <text class="sub" x="72" y="190">{{ROLE}} // ONLINE</text>
    <!-- partikel -->
    <circle class="dot" cx="470" cy="60"  r="4" fill="#F5C518"/>
    <circle class="dot" cx="520" cy="200" r="3" fill="#00E5FF" style="animation-delay:.8s"/>
    <circle class="dot" cx="440" cy="130" r="2.5" fill="#FF6BD6" style="animation-delay:1.6s"/>
    <!-- garis bawah gradien -->
    <rect x="0" y="252" width="1000" height="8" fill="url(#splash)"/>
  </g>
</svg>
```

Pemakaian di README:

```html
<p align="center">
  <img src="./assets/header.svg" alt="{{CODENAME}} header" width="100%"/>
</p>
```

**Alternatif cepat tanpa file** (capsule-render, gelombang gradien):

```html
<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&height=220&section=header&text={{CODENAME}}&fontSize=60&fontColor=ECE8E1&fontAlignY=38&animation=fadeIn&color=gradient&customColorList=12,14,18,20,24&desc={{ROLE}}&descSize=18&descAlignY=60"/>
```

### 6.2 Typing Tagline

```html
<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=24&duration=2800&pause=900&color=FF4655&center=true&vCenter=true&width=700&height=50&lines=%7B%7BTAGLINE_1%7D%7D;%7B%7BTAGLINE_2%7D%7D;%7B%7BTAGLINE_3%7D%7D;Ready+to+ship.+Ready+to+clutch." alt="typing tagline"/>
</p>
```

Catatan: spasi diganti `+`, karakter `{}` perlu di-encode (`%7B %7D`) atau cukup tulis teks asli setelah diisi.

### 6.3 Badge Bar

```html
<p align="center">
  <img src="https://komarev.com/ghpvc/?username={{USERNAME}}&style=for-the-badge&color=FF4655&label=PROFILE+VIEWS"/>
  <img src="https://img.shields.io/github/followers/{{USERNAME}}?style=for-the-badge&logo=github&color=A855F7&labelColor=0F1923"/>
  <img src="https://img.shields.io/github/stars/{{USERNAME}}?style=for-the-badge&logo=github&color=F5C518&labelColor=0F1923"/>
  <img src="https://img.shields.io/badge/STATUS-OPEN_TO_WORK-3DDC84?style=for-the-badge&labelColor=0F1923"/>
</p>
```

### 6.4 Divider Slash (SVG animasi)

`assets/divider.svg`:

```svg
<svg xmlns="http://www.w3.org/2000/svg" width="1000" height="24" viewBox="0 0 1000 24">
  <defs>
    <linearGradient id="g" x1="0" x2="1">
      <stop offset="0" stop-color="#FF4655"/><stop offset=".35" stop-color="#A855F7"/>
      <stop offset=".7" stop-color="#00E5FF"/><stop offset="1" stop-color="#F5C518"/>
    </linearGradient>
  </defs>
  <polygon points="0,12 440,12 452,0 468,0 456,12 544,12 532,24 548,24 560,12 1000,12 1000,14 560,14 548,26 532,26 544,14 456,14 468,2 452,2 440,14 0,14" fill="url(#g)">
    <animate attributeName="opacity" values="1;.35;1" dur="2.4s" repeatCount="indefinite"/>
  </polygon>
  <rect x="0" y="10" width="60" height="4" fill="#ECE8E1">
    <animate attributeName="x" values="-60;1000" dur="3s" repeatCount="indefinite"/>
  </rect>
</svg>
```

```html
<img src="./assets/divider.svg" width="100%"/>
```

### 6.5 Agent Card (Profil Singkat)

Dua opsi:

**Opsi A: tabel Markdown bergaya kartu**

```md
<table align="center">
<tr>
<td width="50%">

### 🎴 AGENT PROFILE
- **Codename:** `{{CODENAME}}`
- **Role:** `{{ROLE}}`
- **Base:** `{{LOCATION}}`
- **Main Weapon:** `{{BAHASA_UTAMA}}`
- **Playstyle:** `{{GAYA_KERJA}}`
- **Currently:** `{{SEDANG_DIKERJAKAN}}`
- **Learning:** `{{SEDANG_DIPELAJARI}}`

</td>
<td width="50%">

### 🧠 ABOUT
{{DESKRIPSI_2_3_KALIMAT}}

</td>
</tr>
</table>
```

**Opsi B: `assets/agent-card.svg`** dengan polygon sudut terpotong, foto avatar (di-embed base64), dan nama yang masuk dengan animasi. Bentuk dasar:

```svg
<svg xmlns="http://www.w3.org/2000/svg" width="460" height="300" viewBox="0 0 460 300">
  <style>
    .n{font:900 34px Impact,'Arial Black',sans-serif;fill:#ECE8E1;letter-spacing:3px}
    .r{font:700 14px 'Courier New',monospace;fill:#00E5FF;letter-spacing:5px}
    .t{font:600 14px 'Courier New',monospace;fill:#ECE8E1}
    .edge{stroke-dasharray:1200;stroke-dashoffset:1200;animation:draw 2s ease forwards}
    @keyframes draw{to{stroke-dashoffset:0}}
  </style>
  <polygon points="0,0 430,0 460,30 460,300 30,300 0,270" fill="#1F2326"/>
  <polygon class="edge" points="0,0 430,0 460,30 460,300 30,300 0,270" fill="none" stroke="#FF4655" stroke-width="3"/>
  <text class="r" x="24" y="48">DUELIST</text>
  <text class="n" x="24" y="92">{{CODENAME}}</text>
  <text class="t" x="24" y="140">ROLE ....... {{ROLE}}</text>
  <text class="t" x="24" y="168">BASE ....... {{LOCATION}}</text>
  <text class="t" x="24" y="196">WEAPON ..... {{BAHASA_UTAMA}}</text>
  <text class="t" x="24" y="224">STATUS ..... ONLINE</text>
  <circle cx="420" cy="30" r="6" fill="#3DDC84"><animate attributeName="opacity" values="1;.2;1" dur="1.4s" repeatCount="indefinite"/></circle>
</svg>
```

### 6.6 Abilities (C / Q / E / X)

Empat keahlian utama dalam bentuk ikon kotak. Contoh tabel:

| Key | Ability | Isi |
|---|---|---|
| **C** | Signature | `{{SKILL_1}}` (contoh: REST API design) |
| **Q** | Basic | `{{SKILL_2}}` (contoh: Realtime dengan WebSocket) |
| **E** | Signature | `{{SKILL_3}}` (contoh: Optimasi query & caching) |
| **X** | **Ultimate** | `{{SKILL_ULTIMATE}}` (contoh: Arsitektur sistem end-to-end) |

Bisa dibuat visual dengan `shields.io`:

```html
<img src="https://img.shields.io/badge/C-{{SKILL_1}}-FF4655?style=for-the-badge&labelColor=0F1923"/>
<img src="https://img.shields.io/badge/Q-{{SKILL_2}}-A855F7?style=for-the-badge&labelColor=0F1923"/>
<img src="https://img.shields.io/badge/E-{{SKILL_3}}-00E5FF?style=for-the-badge&labelColor=0F1923"/>
<img src="https://img.shields.io/badge/X-{{SKILL_ULTIMATE}}-F5C518?style=for-the-badge&labelColor=0F1923"/>
```

### 6.7 Loadout: Tech Stack + Rank

**Langkah:**
1. Kelompokkan tech jadi 4 role (lihat 2.2).
2. Beri rank per tech: `IRON → BRONZE → SILVER → GOLD → PLATINUM → DIAMOND → ASCENDANT → IMMORTAL → RADIANT`.
3. Tampilkan ikon lewat `skillicons.dev` atau `shields.io`, plus bar rank SVG.

**Ikon cepat:**

```html
<!-- DUELIST: Frontend -->
<p><img src="https://skillicons.dev/icons?i=html,css,js,ts,react,nextjs,vue,tailwind,figma&theme=dark"/></p>
<!-- CONTROLLER: Backend -->
<p><img src="https://skillicons.dev/icons?i=nodejs,express,php,laravel,python,django,go,java,spring&theme=dark"/></p>
<!-- INITIATOR: Data -->
<p><img src="https://skillicons.dev/icons?i=mysql,postgres,mongodb,redis,firebase,supabase,prisma&theme=dark"/></p>
<!-- SENTINEL: DevOps -->
<p><img src="https://skillicons.dev/icons?i=docker,kubernetes,nginx,linux,git,github,githubactions,aws,gcp&theme=dark"/></p>
```

> Hapus ikon yang tidak kamu kuasai. Jujur lebih baik daripada daftar panjang: rekruter mudah membedakan.

**Bar rank (template, `assets/rank-backend.svg`)** dengan animasi isi bar:

```svg
<svg xmlns="http://www.w3.org/2000/svg" width="700" height="170" viewBox="0 0 700 170">
  <style>
    .lbl{font:700 14px 'Courier New',monospace;fill:#ECE8E1}
    .rk{font:700 12px 'Courier New',monospace;fill:#A855F7;letter-spacing:2px}
    .head{font:900 20px Impact,'Arial Black',sans-serif;fill:#A855F7;letter-spacing:4px}
    .fill{transform-origin:left center;transform:scaleX(0);animation:grow 1.4s cubic-bezier(.2,.9,.2,1) forwards}
    .f2{animation-delay:.2s}.f3{animation-delay:.4s}
    @keyframes grow{to{transform:scaleX(1)}}
  </style>
  <rect width="700" height="170" fill="#0F1923"/>
  <rect width="6" height="170" fill="#A855F7"/>
  <text class="head" x="24" y="28">CONTROLLER // BACKEND</text>

  <text class="lbl" x="24" y="64">{{TECH_1}}</text>
  <text class="rk"  x="560" y="64">DIAMOND</text>
  <rect x="24" y="72" width="640" height="10" fill="#1F2326"/>
  <rect class="fill" x="24" y="72" width="512" height="10" fill="#A855F7"/>

  <text class="lbl" x="24" y="108">{{TECH_2}}</text>
  <text class="rk"  x="560" y="108">GOLD</text>
  <rect x="24" y="116" width="640" height="10" fill="#1F2326"/>
  <rect class="fill f2" x="24" y="116" width="384" height="10" fill="#A855F7"/>

  <text class="lbl" x="24" y="152">{{TECH_3}}</text>
  <text class="rk"  x="560" y="152">SILVER</text>
  <rect x="24" y="158" width="640" height="8" fill="#1F2326"/>
  <rect class="fill f3" x="24" y="158" width="256" height="8" fill="#A855F7"/>
</svg>
```

**Konversi rank → lebar bar (dari total 640):**

| Rank | % | Lebar |
|---|---|---|
| Iron | 10 | 64 |
| Bronze | 22 | 141 |
| Silver | 40 | 256 |
| Gold | 60 | 384 |
| Platinum | 72 | 461 |
| Diamond | 80 | 512 |
| Ascendant | 88 | 563 |
| Immortal | 95 | 608 |
| Radiant | 100 | 640 |

Tampilkan 4 kartu rank ini dalam 2×2 grid:

```html
<table align="center">
<tr>
<td><img src="./assets/rank-frontend.svg" width="100%"/></td>
<td><img src="./assets/rank-backend.svg" width="100%"/></td>
</tr>
<tr>
<td><img src="./assets/rank-data.svg" width="100%"/></td>
<td><img src="./assets/rank-devops.svg" width="100%"/></td>
</tr>
</table>
```

### 6.8 Featured Missions: Kartu Project (Weapon Skin)

Setiap project ditampilkan seperti **skin senjata**: nama, tier (Select/Deluxe/Premium/Ultra/Exclusive), stack, status, tautan.

**Mapping tier:**

| Tier | Arti pada project |
|---|---|
| SELECT | Project latihan / kecil |
| DELUXE | Project serius, fitur lengkap |
| PREMIUM | Production / dipakai orang lain |
| ULTRA | Skala besar / banyak user / open source populer |
| EXCLUSIVE | Karya terbaik / flagship |

**Template tabel project (cepat, tanpa SVG):**

```md
| 🎯 Mission | 📝 Briefing | 🧰 Loadout | 🏷 Tier | 🔗 |
|---|---|---|---|---|
| **{{PROJECT_1}}** | {{DESKRIPSI}} | `{{STACK}}` | EXCLUSIVE | [Repo](url) · [Live](url) |
| **{{PROJECT_2}}** | {{DESKRIPSI}} | `{{STACK}}` | PREMIUM   | [Repo](url) |
| **{{PROJECT_3}}** | {{DESKRIPSI}} | `{{STACK}}` | DELUXE    | [Repo](url) |
```

**Template kartu SVG (`assets/project-1.svg`):**

```svg
<svg xmlns="http://www.w3.org/2000/svg" width="480" height="210" viewBox="0 0 480 210">
  <defs>
    <linearGradient id="skin" x1="0" y1="0" x2="1" y2="1">
      <stop offset="0" stop-color="#FF4655"/><stop offset=".5" stop-color="#A855F7"/><stop offset="1" stop-color="#00E5FF"/>
    </linearGradient>
  </defs>
  <style>
    .nm{font:900 26px Impact,'Arial Black',sans-serif;fill:#ECE8E1;letter-spacing:2px}
    .tr{font:700 12px 'Courier New',monospace;fill:#F5C518;letter-spacing:4px}
    .ds{font:400 13px 'Courier New',monospace;fill:#ECE8E1}
    .st{font:700 12px 'Courier New',monospace;fill:#00E5FF}
    .shine{animation:shine 3.2s linear infinite}
    @keyframes shine{from{transform:translateX(-200px)}to{transform:translateX(700px)}}
  </style>
  <clipPath id="c"><polygon points="0,0 450,0 480,30 480,210 30,210 0,180"/></clipPath>
  <g clip-path="url(#c)">
    <rect width="480" height="210" fill="#1F2326"/>
    <rect width="480" height="6" fill="url(#skin)"/>
    <polygon class="shine" points="0,0 40,0 0,210 -40,210" fill="#ECE8E1" opacity=".08"/>
    <text class="tr" x="22" y="40">EXCLUSIVE EDITION</text>
    <text class="nm" x="22" y="78">{{PROJECT_1}}</text>
    <text class="ds" x="22" y="112">{{DESKRIPSI_BARIS_1}}</text>
    <text class="ds" x="22" y="132">{{DESKRIPSI_BARIS_2}}</text>
    <text class="st" x="22" y="178">{{STACK}}</text>
    <circle cx="452" cy="190" r="5" fill="#3DDC84"><animate attributeName="opacity" values="1;.25;1" dur="1.6s" repeatCount="indefinite"/></circle>
  </g>
  <polygon points="0,0 450,0 480,30 480,210 30,210 0,180" fill="none" stroke="url(#skin)" stroke-width="2"/>
</svg>
```

Bungkus agar bisa diklik:

```html
<a href="{{LINK_PROJECT_1}}"><img src="./assets/project-1.svg" width="48%"/></a>
<a href="{{LINK_PROJECT_2}}"><img src="./assets/project-2.svg" width="48%"/></a>
```

**Alternatif otomatis:** pin repo lewat `github-readme-stats`:

```html
<a href="https://github.com/{{USERNAME}}/{{REPO}}">
  <img src="https://github-readme-stats.vercel.app/api/pin/?username={{USERNAME}}&repo={{REPO}}&bg_color=0F1923&title_color=FF4655&text_color=ECE8E1&icon_color=00E5FF&border_color=FF4655"/>
</a>
```

### 6.9 Match History (Statistik)

```html
<p align="center">
  <img height="170" src="https://github-readme-stats.vercel.app/api?username={{USERNAME}}&show_icons=true&hide_border=false&bg_color=0F1923&title_color=FF4655&icon_color=00E5FF&text_color=ECE8E1&border_color=FF4655&rank_icon=github"/>
  <img height="170" src="https://github-readme-stats.vercel.app/api/top-langs/?username={{USERNAME}}&layout=compact&langs_count=8&bg_color=0F1923&title_color=A855F7&text_color=ECE8E1&border_color=A855F7"/>
</p>

<p align="center">
  <img src="https://streak-stats.demolab.com?user={{USERNAME}}&background=0F1923&ring=FF4655&fire=F5C518&currStreakNum=ECE8E1&currStreakLabel=FF4655&sideNums=ECE8E1&sideLabels=00E5FF&dates=8B949E&stroke=FF4655&border=FF4655"/>
</p>

<p align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username={{USERNAME}}&bg_color=0F1923&color=ECE8E1&line=FF4655&point=00E5FF&area=true&area_color=A855F7&hide_border=true&title_color=FF4655"/>
</p>
```

> Ganti judul statistik dengan istilah game: *Total Kills = Commits*, *Headshots = Stars*, *Assists = PR*, *Rounds Won = Issues closed*.

### 6.10 Snake Contribution (Animasi ular, otomatis)

`.github/workflows/snake.yml`:

```yaml
name: Generate Snake

on:
  schedule:
    - cron: "0 */12 * * *"
  workflow_dispatch:
  push:
    branches: [main]

permissions:
  contents: write

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/snake.svg?palette=github-dark&color_snake=#FF4655&color_dots=#1F2326,#3b1d5c,#7a2f9e,#00E5FF,#F5C518
            dist/snake-dark.svg?palette=github-dark

      - uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

Pemakaian (branch `output`):

```html
<img src="https://raw.githubusercontent.com/{{USERNAME}}/{{USERNAME}}/output/snake.svg" width="100%"/>
```

### 6.11 Kill Feed (Update Terbaru)

Tabel gaya kill feed, bisa diperbarui manual atau lewat Actions (mis. `blog-post-workflow`):

```md
| 🕒 | Event |
|---|---|
| `2026-10` | 🔥 **{{NAMA}}** mengeliminasi bug kritis di `{{PROJECT}}` |
| `2026-09` | 🚀 Rilis `v1.0` **{{PROJECT}}** |
| `2026-08` | 🎓 Lulus sertifikasi **{{SERTIFIKAT}}** |
```

### 6.12 Battle Pass (Roadmap Belajar)

```md
| Tier | Target | Status |
|---|---|---|
| 1 | {{TARGET_1}} | ✅ Selesai |
| 2 | {{TARGET_2}} | ✅ Selesai |
| 3 | {{TARGET_3}} | 🔄 Sedang berjalan |
| 4 | {{TARGET_4}} | ⏳ Direncanakan |
| 5 | **{{TARGET_ULTIMATE}}** | 🎯 Goal akhir |
```

Atau bar progres SVG sederhana:

```html
<img src="https://progress-bar.xyz/65/?title=Battle+Pass+Season+1&width=400&color=FF4655&suffix=%25"/>
```

### 6.13 Contact: "Plant the Spike"

```html
<p align="center">
  <a href="{{LINKEDIN}}"><img src="https://img.shields.io/badge/LinkedIn-0F1923?style=for-the-badge&logo=linkedin&logoColor=00E5FF"/></a>
  <a href="mailto:{{EMAIL}}"><img src="https://img.shields.io/badge/Email-0F1923?style=for-the-badge&logo=gmail&logoColor=FF4655"/></a>
  <a href="{{PORTFOLIO}}"><img src="https://img.shields.io/badge/Portfolio-0F1923?style=for-the-badge&logo=vercel&logoColor=ECE8E1"/></a>
  <a href="{{INSTAGRAM}}"><img src="https://img.shields.io/badge/Instagram-0F1923?style=for-the-badge&logo=instagram&logoColor=FF6BD6"/></a>
  <a href="{{DISCORD}}"><img src="https://img.shields.io/badge/Discord-0F1923?style=for-the-badge&logo=discord&logoColor=A855F7"/></a>
</p>

<h3 align="center">💣 SPIKE PLANTED: let's build something together.</h3>
```

### 6.14 Footer

```html
<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=12,14,18,20,24&height=120&section=footer"/>
```

---

## 7. Format Data Project (Isi untuk Saya)

Salin template ini per project, lalu isi:

```yaml
- name: "{{NAMA_PROJECT}}"
  tagline: "{{SATU_KALIMAT}}"
  description: "{{2-3_KALIMAT: masalah, solusi, hasil}}"
  tier: EXCLUSIVE | ULTRA | PREMIUM | DELUXE | SELECT
  stack: [Laravel, MySQL, Tailwind, Docker]
  role: "Solo dev / Lead / Contributor"
  features:
    - "..."
    - "..."
  metrics: "contoh: 1.2k user, response < 200 ms"   # opsional
  links:
    repo: ""
    live: ""
    demo_gif: ""
  status: Live | Beta | WIP | Archived
```

Panduan menulis deskripsi project yang kuat:
1. **Masalah** yang diselesaikan (1 kalimat).
2. **Solusi** dan tech pilihan beserta alasannya.
3. **Hasil** terukur (angka, waktu, jumlah user).
4. **Tantangan teknis** paling menarik yang kamu pecahkan.

---

## 8. Peta Tech → Role → Warna → Ikon (Referensi Cepat)

| Kategori | Role | Warna | Contoh slug `skillicons.dev` |
|---|---|---|---|
| Frontend | DUELIST | `#FF4655` | `html, css, js, ts, react, nextjs, vue, nuxt, svelte, angular, tailwind, bootstrap, sass, vite, figma` |
| Backend | CONTROLLER | `#A855F7` | `nodejs, express, nestjs, php, laravel, python, django, flask, fastapi, java, spring, go, rust, dotnet, cs, ruby, rails` |
| Mobile | DUELIST | `#FF4655` | `flutter, dart, kotlin, swift, androidstudio, reactnative` |
| Database | INITIATOR | `#00E5FF` | `mysql, postgres, mongodb, redis, sqlite, firebase, supabase, prisma, graphql` |
| DevOps | SENTINEL | `#3DDC84` | `docker, kubernetes, nginx, linux, bash, git, github, githubactions, gitlab, aws, gcp, azure, vercel, netlify, cloudflare` |
| Data/AI | INITIATOR | `#00E5FF` | `python, pytorch, tensorflow, jupyter, pandas, numpy` |
| Testing/Tools | SENTINEL | `#3DDC84` | `jest, postman, vscode, idea, npm, yarn, pnpm` |

---

## 9. Aksesibilitas, Performa, Kompatibilitas

- Beri `alt` deskriptif di setiap gambar.
- Jangan menaruh informasi penting **hanya** di dalam gambar. Ulangi di teks/tabel agar bisa dibaca screen reader dan mesin pencari.
- Animasi tidak boleh berkedip cepat (> 3 kali/detik) demi keamanan epilepsi. Semua animasi di atas memakai ≥ 1.4 detik per siklus.
- Hormati `prefers-reduced-motion` di dalam SVG:
  ```css
  @media (prefers-reduced-motion: reduce) { * { animation: none !important; } }
  ```
- Tes di **mobile** (lebar ~360 px): gunakan `width="100%"` dan hindari tabel > 2 kolom berisi gambar.
- Tes di **dark & light mode** GitHub. Panel navy sudah kontras di keduanya.
- Cache GitHub (camo) bisa menahan gambar lama. Saat update SVG, tambahkan `?v=2` pada URL.

---

## 10. Rencana Eksekusi (Timeline)

| Fase | Tugas | Estimasi | Output |
|---|---|---|---|
| **1. Riset & data** | Isi Bagian 0 & 7 | 30–60 menit | Data lengkap |
| **2. Setup repo** | Buat folder `assets/`, `.github/workflows/` | 10 menit | Struktur siap |
| **3. Aset inti** | `header.svg`, `divider.svg`, `agent-card.svg` | 45 menit | Banner & profil |
| **4. Tech stack** | Ikon + 4 `rank-*.svg` | 45 menit | Loadout |
| **5. Project** | Kartu project per proyek | 20 menit/project | Missions |
| **6. Statistik** | Stats, streak, graph, snake workflow | 30 menit | Match history |
| **7. Konten teks** | About, abilities, roadmap, contact | 30 menit | Konten final |
| **8. Rakit README** | Susun sesuai blueprint Bagian 5 | 30 menit | `README.md` v1 |
| **9. QA** | Cek mobile, dark/light, link, alt text | 30 menit | Siap rilis |
| **10. Polish** | Tuning warna, kecepatan animasi, cache bust | 30 menit | v1.1 |

Total sekitar **5–7 jam** untuk hasil lengkap; versi minimal (header + stack + project + stats) bisa selesai dalam ±2 jam.

---

## 11. Checklist Final

- [ ] Semua `{{PLACEHOLDER}}` sudah diganti
- [ ] Username benar di semua URL statistik
- [ ] Semua SVG tampil (path relatif benar, huruf besar/kecil sesuai)
- [ ] Animasi jalan di Chrome, Firefox, Safari, dan GitHub mobile
- [ ] Tidak ada logo/artwork resmi Valorant
- [ ] Snake workflow sukses dan branch `output` terbentuk
- [ ] Semua tautan project & kontak valid
- [ ] Teks alternatif ada di semua gambar
- [ ] Ukuran total aset wajar (< 2 MB tanpa GIF)
- [ ] Preview di mode gelap dan terang
- [ ] Commit dengan pesan jelas, mis. `feat: valorant-style animated readme`

---

## 12. Kerangka README.md Final (Siap Salin)

```md
<p align="center">
  <img src="./assets/header.svg" width="100%" alt="{{CODENAME}} header"/>
</p>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=24&pause=900&color=FF4655&center=true&vCenter=true&width=700&lines=Tagline+1;Tagline+2;Tagline+3" alt="typing"/>
</p>

<p align="center">
  <!-- badge bar 6.3 -->
</p>

<img src="./assets/divider.svg" width="100%"/>

## 🎴 AGENT SELECT
<!-- agent card 6.5 -->

## ⚡ ABILITIES
<!-- 6.6 -->

<img src="./assets/divider.svg" width="100%"/>

## 🎒 LOADOUT
<!-- 6.7 ikon + rank cards -->

<img src="./assets/divider.svg" width="100%"/>

## 🎯 FEATURED MISSIONS
<!-- 6.8 project cards -->

## 📊 MATCH HISTORY
<!-- 6.9 stats -->

## 🐍 CONTRIBUTION FEED
<!-- 6.10 snake -->

## 🔔 KILL FEED
<!-- 6.11 -->

## 🎫 BATTLE PASS
<!-- 6.12 -->

## 💣 PLANT THE SPIKE
<!-- 6.13 contact -->

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=12,14,18,20,24&height=120&section=footer"/>
```

---

## 13. Ide Lanjutan (Opsional, Level Berikutnya)

1. **Generator SVG dari JSON:** satu file `data.json` berisi tech & project, `scripts/build-svg.mjs` membuat semua `rank-*.svg` dan `project-*.svg` otomatis, dijalankan via GitHub Actions saat `push`.
2. **Stats mandiri** (tanpa Vercel pihak ketiga) memakai Action seperti `lowlighter/metrics`, sehingga stabil dan bisa dikustom warnanya.
3. **WakaTime** untuk "jam bermain" (jam ngoding per bahasa) lewat `waka-readme`.
4. **Quote of the day** gaya voice line agent, diperbarui harian lewat Action.
5. **Music/Spotify now playing** untuk suasana "lobby".
6. **Versi dua tema** (`<picture>` dengan `prefers-color-scheme`) untuk dark dan light penuh.
7. **GIF demo project** (Peek/ScreenToGif) yang dimasukkan ke dalam kartu project.
8. **Intro screen "agent lock-in"**: header dengan teks "LOCKED IN" yang muncul setelah 2 detik (SMIL `begin="2s"`).

---

## 14. Langkah Selanjutnya

1. Kirim data Bagian 0 (username, role, tech, project, kontak).
2. Saya hasilkan `README.md` final + seluruh file `assets/*.svg` + workflow Actions yang sudah terisi.
3. Kamu commit ke repo, cek tampilan, lalu kita iterasi warna/animasi sesuai selera.
