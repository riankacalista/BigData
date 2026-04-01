# Minilab Big Data – Data Ingestion Pipeline

Proyek ini merupakan implementasi sederhana dari pipeline ingestion data dalam ekosistem Big Data menggunakan PostgreSQL, MinIO, dan Python (Jupyter Notebook).

---

## Deskripsi Singkat

Pipeline ini melakukan proses:
- Mengambil data dari **PostgreSQL (RDBMS)**
- Membaca data dari **file lokal (CSV & XLSX)**
- Mengolah data menggunakan **Pandas**
- Menyimpan hasil ke **MinIO (data lake)**

---

## Tools & Teknologi

| Tools        | Fungsi |
|-------------|--------|
| Docker      | Menjalankan container |
| PostgreSQL  | Database relasional |
| MinIO       | Object storage (data lake) |
| Python      | Data processing |
| Pandas      | Manipulasi data |
| SQLAlchemy  | Koneksi database |
| MinIO SDK   | Upload ke MinIO |

---

## Struktur Data di MinIO
raw/
├── rdbms/
├── csv/
└── xlsx/

---

## Cara Menjalankan Project

### 1. Install dependency
```bash
pip install pandas sqlalchemy psycopg2-binary openpyxl minio jupyter

### 2. Jalankan Docker
```bash
docker compose up -d

```bash
docker ps

### 3. Jalankan Jupyter Notebook
```bash
jupyter notebook

### 4. Jalankan Script Ingestion
- Jalankan file .ipynb
- Script akan mengambil data dari PostgreSQL, membaca file CSV & XLSX, dan upload ke MinIO

### 4. Akses MinIO
- Buka di browser http://localhost:9001
- Login dengan Username: minioadmin dan Password: minioadmin123

---

## Dataset
Dataset yang digunakan dalam proyek ini merupakan dataset dummy yang disediakan sebagai bagian dari perintah minilab, terdiri dari:
1. Customers
   customer_id
   nama
   kota
   umur
   tanggal registrasi
2. Products
   nama produk
   kategori
   harga
   stok
3. Orders
   relasi customer dan produk
   jumlah pembelian
   tanggal transaksi

Dataset ini dirancang untuk mendukung:
- Clustering (segmentasi pelanggan)
- Klasifikasi
- Association Rules (analisis pembelian)

---

## File Dataset Tambahan

| File        | Keterangan |
|-------------|--------|
| products.csv      | Data produk |
| orders_source.xlsx  | Data transaksi |

Folder venv/ dan .ipynb_checkpoints/ tidak diupload karena merupakan file sistem
---

## Error dalam Koneksi
Jika terjadi error koneksi, restart container dengan:
```bash
docker compose down -v
docker compose up -d
