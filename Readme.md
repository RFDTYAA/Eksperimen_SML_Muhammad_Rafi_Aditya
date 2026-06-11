# Eksperimen SML - Muhammad Rafi Aditya

Repositori ini berisi eksperimen _Supervised Machine Learning_ (SML) untuk mengklasifikasikan risiko kredit (_good/bad credit risk_) menggunakan **German Credit Dataset** (dari OpenML). Proyek ini mencakup proses Exploratory Data Analysis (EDA), preprocessing data, serta _pipeline_ otomatisasi yang terintegrasi dengan GitHub Actions.

## 📂 Struktur Repositori

- **`.github/workflows/preprocess.yml`**
  _Workflow_ GitHub Actions yang memungkinkan preprocessing data berjalan secara otomatis (CI/CD). Skrip ini akan dieksekusi setiap kali ada _push_ pada file `automate_*.py` atau dapat dijalankan secara manual (_workflow_dispatch_).

- **`preprocessing/Eksperimen_Muhammad_Rafi_Aditya.ipynb`**
  Jupyter Notebook yang berisi dokumentasi langkah-langkah eksperimen secara detail, meliputi:
  1. Memuat dataset dari OpenML.
  2. Melakukan Exploratory Data Analysis (EDA) seperti pengecekan _missing values_, distribusi target, dan matriks korelasi.
  3. Membangun _Pipeline_ Preprocessing menggunakan `scikit-learn`.

- **`preprocessing/automate_muhammad_rafi_aditya.py`**
  Skrip Python untuk mengotomatiskan proses preprocessing yang sebelumnya dieksperimenkan di Jupyter Notebook. Saat dijalankan, skrip ini mengekspor model preprocessor dan dataset yang sudah dibersihkan.

- **Artifak Dataset Hasil Preprocessing:**
  - `german_credit_train_preprocessed.csv`: Data latih (train) yang sudah diproses.
  - `german_credit_test_preprocessed.csv`: Data uji (test) yang sudah diproses.
  - `preprocessor.pkl`: Objek _ColumnTransformer_ yang disimpan untuk digunakan kembali (deployment/prediksi).

## ⚙️ Tahapan Preprocessing Data

Langkah-langkah preprocessing yang dilakukan pada dataset ini adalah:

- **Fitur Numerik (`int64`, `float64`):** Menggunakan `SimpleImputer` dengan strategi `median` untuk menangani _missing values_, dilanjutkan dengan standarisasi menggunakan `StandardScaler`.
- **Fitur Kategorikal (`object`, `category`):** Menggunakan `SimpleImputer` dengan strategi `most_frequent` (modus) untuk _missing values_, dilanjutkan dengan _encoding_ menggunakan `OneHotEncoder`.
- **Pemisahan Data (Train-Test Split):** Data dibagi menjadi data latih (80%) dan data uji (20%) dengan metode _stratify_ berdasarkan kelas target agar proporsinya seimbang.

## 🖼️ Bukti Penyerahan / Paparan Platform

Berikut adalah tangkapan skrin yang menunjukkan fail yang dimuat naik dan artifak (output) yang dijana oleh skrip `automate_*.py` di platform pembelajaran:

![Screenshot Platform Submission](uploaded:Screenshot 2026-06-11 at 12.01.59.png-71c23b34-ec60-4317-956a-cb265ddeeab1)

Tangkapan skrin mengesahkan kewujudan:

- Skrip `automate_muhammad_rafi_aditya.py` yang dimuat naik.
- Artifak output CSV dan PKL yang dijana.
- Notebook eksperimen `Eksperimen_Muhammad_Rafi_Aditya.ipynb`.

## 🚀 Cara Penggunaan

### Menjalankan secara Lokal

1. Pastikan Anda telah menginstal _library_ Python yang dibutuhkan:
   ```bash
   pip install pandas numpy scikit-learn joblib matplotlib seaborn
   ```
2. Masuk ke direktori _preprocessing_ dan jalankan skrip otomatisasi:

```bash
   cd preprocessing
   python automate_muhammad_rafi_aditya.py
```

3. File output berupa _.csv_ dan _.pkl_ akan ter-generate secara otomatis di direktori tersebut.

### Menggunakan GitHub Actions

Repositori ini sudah dikonfigurasi dengan GitHub Actions. Setiap kali Anda melakukan push pada pembaruan di file _automate_muhammad_rafi_aditya.py_, alur kerja akan berjalan di GitHub secara otomatis. Anda dapat mengunduh hasilnya (artifak _preprocessed-dataset-latest_) langsung melalui tab Actions di repositori GitHub Anda.

## 👤 Profil Pengembang

Proyek ini dikembangkan oleh **Muhammad Rafi Aditya** sebagai bagian dari kurikulum _Membangun Sistem Machine Learning (Level Mahir)_ di **Dicoding Indonesia** dalam program Pijak in collaboration with IBM SkillsBuild.
