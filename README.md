# Analisis Kualitas Data dan Sumber Daya Manusia

**Portofolio Data Analyst | Python · Pandas · SQL (SQLite) · Power BI**

Proyek ini mengolah dataset kepegawaian sintetis **HRDataset_v14** untuk mengevaluasi kualitas data dan menganalisis komposisi tenaga kerja, status kepegawaian, kinerja, keterlibatan pegawai, kepuasan kerja, serta absensi. Pengerjaan dilakukan melalui proses *data understanding*, *data cleaning & validation*, *exploratory data analysis* (EDA), analisis SQL, dan visualisasi dalam dashboard Power BI interaktif.

> **Catatan:** Dataset ini merupakan data sintetis dari organisasi fiktif untuk tujuan pembelajaran. Hasil analisis tidak menggambarkan kondisi kepegawaian Pegadaian, BPK Kupang, maupun instansi nyata lainnya.

## Tampilan Dashboard Power BI

Dashboard terdiri dari tiga halaman. Gambar di bawah akan tampil setelah tiga screenshot diunggah ke folder `assets/` dengan nama file yang sama persis.

### 1. Employee Data Quality

Menampilkan jumlah pegawai, kelengkapan `ManagerID`, ketidaksesuaian tanggal penilaian kinerja, sebaran temuan per departemen, serta daftar record yang perlu ditinjau.

![Dashboard Employee Data Quality](assets/01_employee_data_quality.png)

### 2. Workforce Overview

Menampilkan komposisi pegawai aktif dan terminasi, distribusi pegawai menurut departemen, serta tren tahun perekrutan.

![Dashboard Workforce Overview](assets/02_workforce_overview.png)

### 3. Employee Performance & Attendance

Menampilkan distribusi kategori kinerja, rata-rata *engagement* dan kepuasan kerja, absensi, serta keterlambatan berdasarkan kategori kinerja.

![Dashboard Employee Performance dan Attendance](assets/03_performance_attendance.png)

## Tujuan Proyek

1. Mengidentifikasi masalah kualitas data, seperti nilai kosong, duplikasi, dan ketidaksesuaian antaratribut.
2. Menstandarkan format data dan mendokumentasikan perubahan tanpa menghilangkan informasi yang belum terverifikasi.
3. Menganalisis komposisi, status, kinerja, keterlibatan, kepuasan, dan absensi pegawai.
4. Menggunakan SQL untuk menghasilkan ringkasan data yang dapat dibandingkan dengan hasil Python.
5. Menyajikan temuan dalam dashboard Power BI yang mudah dibaca dan dapat difilter.

## Dataset

| Informasi | Keterangan |
| --- | --- |
| Nama | Human Resources Data Set — HRDataset_v14 |
| Sumber | [Kaggle — Human Resources Data Set](https://www.kaggle.com/datasets/rhuebner/human-resources-data-set) |
| Pembuat | Dr. Rich Huebner dan Dr. Carla Patalano |
| Jenis data | Sintetis, untuk pembelajaran |
| Jumlah data | 311 record pegawai |
| Jumlah atribut | 36 kolom asli |
| Rentang tanggal perekrutan | 2006–2018 |
| Dokumentasi kolom | [HRDataset_v14 Codebook](https://rpubs.com/rhuebner/hrd_cb_v14) |

Dataset asli maupun versi CSV yang dimodifikasi **tidak didistribusikan** dalam repository ini. Untuk menjalankan ulang proyek, unduh dataset langsung dari Kaggle dan ikuti petunjuk di bawah.

## Tools dan Alur Pengerjaan

| Tahap | Tools | Pekerjaan |
| --- | --- | --- |
| Data Understanding | Google Colab, Pandas | Pemeriksaan struktur data, tipe data, missing values, dan duplikasi |
| Data Cleaning & Validation | Python, Pandas | Standardisasi format, validasi tanggal dan status, dokumentasi temuan |
| Exploratory Data Analysis | Pandas, Matplotlib | Analisis tenaga kerja, kinerja, engagement, kepuasan, dan absensi |
| SQL Data Analysis | SQLite | Query agregasi dan pemeriksaan konsistensi |
| Dashboard | Power BI Desktop, DAX | KPI Cards, grafik, tabel review, dan slicer departemen |

Seluruh analisis menggunakan kolom asli yang tersedia pada dataset. Tidak ada penambahan dataset pelatihan atau inventaris dokumen buatan.

## Ringkasan Hasil Analisis

| Indikator | Hasil |
| --- | ---: |
| Pegawai unik | 311 |
| Atribut dipertahankan | 36 |
| Pegawai berstatus aktif | 207 |
| Pegawai telah terminasi | 104 |
| Jumlah departemen | 6 |
| ID pegawai duplikat | 0 |
| `ManagerID` kosong | 8 |
| Tanggal performance review sebelum tanggal masuk | 2 |
| Total temuan yang perlu review | 10 |
| Rata-rata engagement | 4,11 |
| Rata-rata kepuasan kerja | 3,89 |
| Rata-rata absensi | 10,24 |

**Catatan kualitas data:** Sepuluh temuan adalah total hasil dari dua aturan pemeriksaan dan tidak selalu berarti sepuluh pegawai berbeda. Sebanyak 207 nilai `DateofTermination` kosong merupakan kondisi yang diharapkan untuk pegawai yang belum mengalami terminasi. Proses cleaning juga mencatat 100 penyesuaian interpretasi abad pada tanggal lahir; hasilnya didokumentasikan dan tidak dianggap sebagai verifikasi terhadap dokumen identitas asli.

### Temuan Utama

- **Komposisi pegawai:** Departemen Production memiliki 209 record (67,2% dari total pegawai), jumlah terbanyak dalam dataset.
- **Status kepegawaian:** Terdapat 207 pegawai aktif dan 104 pegawai yang tercatat telah terminasi. Sebanyak 83 kasus terminasi berada pada departemen Production.
- **Kinerja:** Sebanyak 243 pegawai (78,1%) termasuk kategori *Fully Meets*, 37 *Exceeds*, 18 *Needs Improvement*, dan 13 *PIP*.
- **Keterlambatan:** Rata-rata `DaysLateLast30` pada kategori *PIP* sebesar 4,31 dan *Needs Improvement* 3,78, lebih tinggi dibandingkan kategori *Fully Meets* (0,02) dan *Exceeds* (0,00). Temuan ini bersifat deskriptif dan **tidak menunjukkan sebab-akibat**.

## Struktur Repository

```text
analisis-kualitas-data-dan-sdm/
├── README.md
├── notebooks/
│   ├── 01_data_understanding_and_cleaning.ipynb
│   ├── 02_exploratory_data_analysis.ipynb
│   └── 03_sql_data_analysis.ipynb
├── assets/
│   ├── 01_employee_data_quality.png
│   ├── 02_workforce_overview.png
│   └── 03_performance_attendance.png
├── powerbi/
│   └── HC_Analytics_PowerBI_Theme.json
├── requirements.txt
└── .gitignore
```

*Struktur di atas adalah susunan yang dituju. Sesuaikan dengan nama file yang benar-benar sudah Anda unggah.*

## Cara Menjalankan Ulang Analisis

1. Unduh `HRDataset_v14.csv` melalui tautan Kaggle pada bagian Dataset.
2. Buka notebook di folder `notebooks/` menggunakan Google Colab.
3. Jalankan notebook pertama, lalu unggah CSV asli saat diminta.
4. Simpan hasil cleaning untuk digunakan pada notebook EDA dan SQL.
5. Jalankan notebook secara berurutan dan cocokkan hasilnya dengan ringkasan di atas.
6. Untuk membuat ulang dashboard, impor hasil cleaning ke Power BI Desktop dan bangun visual berdasarkan indikator yang didokumentasikan.

## Keterbatasan Analisis

- Dataset bersifat sintetis, bukan data pegawai organisasi nyata.
- Informasi perekrutan mencakup periode hingga 2018; dashboard tidak menggambarkan kondisi terkini.
- Hasil pemeriksaan data yang membutuhkan review tidak diisi dengan nilai perkiraan.
- Analisis bersifat deskriptif sehingga hubungan antarvariabel tidak dapat langsung dianggap sebagai hubungan sebab-akibat.

## Atribusi dan Penggunaan Data

Sumber data: **Dr. Rich Huebner dan Dr. Carla Patalano**, [Human Resources Data Set di Kaggle](https://www.kaggle.com/datasets/rhuebner/human-resources-data-set). Pembuat dataset menyatakan ketentuan berbagi berdasarkan **CC BY-NC-ND 4.0**. Repository ini berfokus pada kode, metode, dan visualisasi agregat, tanpa mengunggah ulang file dataset asli maupun hasil modifikasinya. Harap tinjau ketentuan sumber sebelum menggunakan atau membagikan ulang data.
