# LAPORAN EXPLORATORY DATA ANALYSIS (EDA)
## Analisis Deviasi Jadwal dan Keterlambatan Perjalanan KA 5568A Commuter Line (Studi Kasus Laporan Investigasi KNKT Stasiun Bekasi Timur, 27 April 2026)

### Identitas Penyusun
* **Nama Lengkap:** Muhammad Za’iimun Nasyiith
* **NIM:** 26MA41D002
* **Program Studi:** Magister Ilmu Komputer
* **Institusi:** Program Pascasarjana, Universitas Amikom Purwokerto
* **Tahun:** 2026

---

### Deskripsi Proyek
Repositori ini memuat seluruh rangkaian tugas proyek **Exploratory Data Analysis (EDA)** berdasarkan dokumen resmi **Laporan Akhir Investigasi Kecelakaan Perkeretaapian KNKT Nomor `KNKT.26.04.03.02`** mengenai tabrakan antara **KA 4B Argo Bromo Anggrek** dan **KA 5568A Commuter Line** di Jalur I Stasiun Bekasi Timur, Daerah Operasi 1 Jakarta pada tanggal **27 April 2026**.

Analisis difokuskan pada data program dan realisasi perjalanan **KA 5568A Commuter Line** (relasi Kampung Bandan – Cikarang) untuk mengidentifikasi pola deviasi waktu kedatangan/keberangkatan, faktor penyimpangan jadwal, serta rekomendasi pemodelan *Machine Learning*.

---

### Struktur Berkas Repositori
1. **`README.md`**: Dokumentasi utama dan ringkasan hasil proyek.
2. **`dataset_ka5568a.csv`**: Dataset mentah 15 stasiun lintasan KA 5568A yang diekstrak dari Tabel 3 Laporan KNKT.
3. **`EDA_KA5568A_KNKT.ipynb`**: Skrip *Jupyter Notebook* (Google Colab) berisi pengolahan data, analisis statistik, transformasi fitur, deteksi *outliers*, dan visualisasi grafik (Bab 3 – Bab 8).
4. **`Laporan_EDA_KA5568A_KNKT-v2.docx`**: Dokumen laporan lengkap terstruktur dari Bab 1 hingga Bab 9.

---

### Kamus Data (`dataset_ka5568a.csv`)
| Nama Kolom | Tipe Data | Keterangan |
| :--- | :--- | :--- |
| `Urutan` | Integer | Nomor urut stasiun dari St. Kampung Bandan (1) hingga St. Bekasi Timur (15) |
| `Stasiun` | String | Nama stasiun pemberhentian / lintasan |
| `Program_Datang` | Datetime | Jadwal rencana kedatangan kereta sesuai GAPEKA / Bentuk O.100 |
| `Program_Berangkat` | Datetime | Jadwal rencana keberangkatan kereta sesuai GAPEKA / Bentuk O.100 |
| `Realisasi_Datang` | Datetime | Waktu aktual kereta tiba berdasarkan *data logger* persinyalan |
| `Realisasi_Berangkat` | Datetime | Waktu aktual kereta berangkat berdasarkan *data logger* persinyalan |
| `Keterangan` | String | Catatan operasional resmi dari laporan investigasi KNKT |

---

### Ringkasan Temuan Utama
* **Pola Perjalanan Normal:** Sebanyak **86,7%** (13 dari 15 stasiun) memiliki durasi berhenti (*dwelling time*) normal di bawah 95 detik dengan nilai tengah (*median*) sebesar **44 detik**.
* **Anomali Keterlambatan Ekstrem (*Outlier*):** Terjadi lonjakan durasi singgah sebesar **693 detik (11 menit 33 detik)** dan keterlambatan keberangkatan sebesar **512 detik (8 menit 32 detik)** di **Stasiun Bekasi** akibat antrean penyusulan oleh KA 116B Sawunggalih.
* **Korelasi Kuat:** Terdapat korelasi positif sangat kuat (**r = +0,96**) antara durasi waktu singgah di stasiun dengan deviasi keterlambatan keberangkatan.
* **Rekomendasi Model:** Algoritma berbasis pohon keputusan (**Random Forest Regressor**, **XGBoost Regressor**) atau **Support Vector Regression (SVR)** sangat direkomendasikan karena tangguh menghadapi distribusi miring (*skewed*) dan *outliers* operasional.
