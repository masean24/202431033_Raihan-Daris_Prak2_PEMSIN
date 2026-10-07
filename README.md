# Web Scraping - Countries of the World

Tugas praktikum web scraping untuk mengambil data negara (nama, ibu kota, populasi) dari situs latihan scraping dan menyimpannya ke file CSV. Notebook ini menggunakan `requests` + `BeautifulSoup` untuk scraping, lalu `pandas` untuk verifikasi hasil.

**Nama:** Raihan Daris Ramadhan
**NIM:** 202431033_Raihan Daris
**Sumber data:** https://www.scrapethissite.com/pages/simple/

## 📁 Struktur File

```
.
├── Scraping.ipynb   # Notebook scraping
├── countries.csv    # Hasil scraping (dibuat saat notebook dijalankan)
└── README-Scraping.md
```

## 🛠️ Library yang Digunakan

- `requests` — mengambil halaman HTML
- `bs4 (BeautifulSoup)` — parsing HTML
- `csv` — menyimpan hasil ke CSV
- `pandas` — membaca / verifikasi `countries.csv`

Install:

```bash
pip install requests beautifulsoup4 pandas jupyter
```

## 🔍 Tahapan di Scraping.ipynb

1. **Install `requests`**
   ```python
   pip install requests
   ```
2. **Import library** — `requests`, `csv`, `BeautifulSoup`.
3. **Request halaman** — `GET https://www.scrapethissite.com/pages/simple/`, cek `status_code` (200 = sukses) dan `response.text`.
4. **Parsing HTML** — `BeautifulSoup(response.text, "html.parser")`, ambil semua `div.col-md-4.country`. Jumlah yang ditemukan ± 250 negara.
5. **Ekstraksi data** — loop tiap blok, ambil:
   - `h3.country-name` → `name`
   - `span.country-capital` → `capital`
   - `span.country-population` → `population`
   
   Disimpan sebagai list of dict `result`.
6. **Cetak hasil** — loop `result`, format `Country: X - Capital: Y - Population: Z`.
7. **Simpan ke CSV** — tulis `countries.csv` dengan header `name,capital,population` via `csv.DictWriter`.
8. **Verifikasi dengan pandas** — `import pandas as pd`, `db = pd.read_csv('countries.csv')`, tampilkan `db`.

## 📊 Output `countries.csv`

Kolom: `name, capital, population`

Contoh:

| name | capital | population |
|---|---|---|
| Andorra | Andorra la Vella | 84000 |
| Afghanistan | Kabul | 29121286 |
| Indonesia | Jakarta | ... |

## ▶️ Cara Menjalankan

```bash
jupyter notebook Scraping.ipynb
```

Jalankan cell berurutan dari atas ke bawah. File `countries.csv` akan muncul di folder yang sama dengan notebook.

## 📌 Catatan

Situs `scrapethissite.com` adalah sandbox publik untuk belajar scraping, jadi aman untuk latihan.
