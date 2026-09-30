# Health Map AI – Sulawesi Tenggara

## Latar Belakang
Ketersediaan tenaga medis di Sulawesi Tenggara berbeda antarwilayah. Jumlah tenaga medis secara absolut belum cukup untuk menggambarkan kebutuhan suatu wilayah karena setiap kabupaten/kota memiliki jumlah penduduk yang berbeda.

Selain itu, jumlah penduduk dan tenaga medis dapat berubah dari tahun ke tahun. Oleh karena itu, diperlukan pendekatan yang dapat mempelajari pola historis tersebut untuk memperkirakan jumlah tenaga medis pada tahun berikutnya.

Berdasarkan kondisi tersebut, Health Map AI dikembangkan untuk memprediksi jumlah tenaga medis di 17 kabupaten/kota di Sulawesi Tenggara menggunakan data historis tahun 2015–2025.

## Permasalahan
Bagaimana memprediksi jumlah kekurangan tenaga medis pada setiap kabupaten/kota di Sulawesi Tenggara berdasarkan jumlah penduduk dan tahun dari data historis?

## Tujuan
Health Map AI bertujuan untuk menghasilkan prediksi jumlah tenaga medis pada setiap kabupaten/kota di Sulawesi Tenggara serta memberikan gambaran kebutuhan tenaga medis berdasarkan jumlah penduduk dan standar 0,8 tenaga medis per 1.000 penduduk yang digunakan dalam project.

## Dataset
Dataset yang digunakan merupakan data Sulawesi Tenggara tahun 2015–2025 yang terdiri dari:

- Kabupaten/Kota
- Tahun
- Jumlah Penduduk
- Jumlah Tenaga Medis

Dataset mencakup 17 kabupaten/kota di Sulawesi Tenggara.

## Data Training dan Testing
Data dibagi berdasarkan tahun, bukan secara acak.

- **Training:** 2015–2024
- **Testing:** 2025

Data tahun 2015–2024 digunakan untuk mempelajari pola historis, sedangkan data tahun 2025 digunakan untuk menguji kemampuan model dalam memprediksi jumlah tenaga medis.

## Preprocessing
Pada tahap preprocessing, nilai jumlah penduduk yang masih menggunakan satuan ribuan dikonversi menjadi nilai jumlah penduduk sebenarnya.

Selain itu, data diperiksa untuk memastikan tidak terdapat data kosong dan duplikat berdasarkan kombinasi Kabupaten/Kota dan Tahun.

Kolom Kabupaten/Kota yang berbentuk teks kemudian diubah menjadi bentuk numerik menggunakan **One-Hot Encoding** agar dapat digunakan oleh model machine learning.

## Feature dan Target
Feature yang digunakan dalam model:
- Jumlah Penduduk
- Tahun
- Kabupaten/Kota
Kabupaten/Kota diubah menjadi beberapa fitur numerik melalui One-Hot Encoding.

Target yang diprediksi adalah:
- Jumlah Tenaga Medis

## Mengapa Menggunakan Regression?
Health Map AI menggunakan pendekatan **Regression** karena target yang ingin diprediksi berupa nilai numerik kontinu, yaitu jumlah tenaga medis.

Berbeda dengan klasifikasi yang menghasilkan kategori seperti rendah, sedang, atau tinggi, regression digunakan untuk menghasilkan prediksi dalam bentuk angka. Dalam project ini, model mempelajari hubungan antara jumlah penduduk, tahun, dan wilayah dengan jumlah tenaga medis untuk menghasilkan prediksi jumlah tenaga medis.

## Algoritma
Untuk membandingkan pendekatan prediksi, digunakan dua algoritma regression:

### 1. Linear Regression
Linear Regression digunakan untuk mempelajari hubungan antara feature yang digunakan dengan jumlah tenaga medis berdasarkan pola hubungan dalam data historis.

### 2. Random Forest Regression
Random Forest Regression digunakan untuk mempelajari pola yang lebih kompleks dengan menggabungkan beberapa Decision Tree dalam menghasilkan prediksi.

Kedua algoritma dilatih menggunakan data tahun 2015–2024 dan diuji menggunakan data tahun 2025.

## Evaluasi Model
Performa kedua model dievaluasi menggunakan tiga metrik:
- **MAE (Mean Absolute Error)** untuk mengukur rata-rata besar kesalahan prediksi.
- **RMSE (Root Mean Squared Error)** untuk mengukur besar kesalahan prediksi dengan memberikan penalti lebih besar terhadap kesalahan yang besar.
- **R² (R-squared)** untuk melihat seberapa baik model menjelaskan variasi pada data target.

Hasil evaluasi:

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 37.74 | 83.91 | 0.7086 |
| Random Forest Regression | 25.38 | 42.50 | 0.9252 |

## Analisis Kebutuhan Tenaga Medis
Selain menghasilkan prediksi, project menghitung kebutuhan tenaga medis berdasarkan standar 0,8 tenaga medis per 1.000 penduduk.

Perhitungan yang dilakukan meliputi:
1. Rasio tenaga medis per 1.000 penduduk.
2. Kebutuhan tenaga medis berdasarkan standar.
3. Selisih antara jumlah tenaga medis aktual dengan kebutuhan berdasarkan standar.
4. Status pemenuhan standar.
5. Prediksi jumlah tenaga medis menggunakan Linear Regression dan Random Forest Regression.

## Output
Hasil akhir Health Map AI memberikan informasi berupa:
**Jumlah Penduduk → Tenaga Medis Saat Ini → Prediksi AI → Kebutuhan Berdasarkan Standar → Kekurangan Tenaga Medis**
Output prediksi ditampilkan untuk 17 kabupaten/kota pada tahun 2025.

## Struktur Project
```text
Health-Map-AI-Sulawesi-Tenggara/
│
├── README.md
└── HealthMap_AI.ipynb
