# Hands-On 3 Pandas Lanjutan
## Case 02: Customer Churn Analysis

### Deskripsi
Analisis ini memeriksa kualitas data pelanggan, membersihkan data,
menganalisis pola churn, dan membuat model klasifikasi Logistic Regression.

### Dataset
Dataset asli disimpan di folder `data/`.

### Urutan pembersihan
1. Audit dataset dan pemeriksaan duplikat.
2. Penanganan missing value.
3. Deteksi outlier menggunakan metode IQR dan capping pada dataset ekspor.
4. Perbaikan tipe data dan normalisasi kategori.
5. Pembuatan laporan kualitas sebelum dan sesudah pembersihan.

### Pencegahan data leakage
Model menggunakan data mentah yang sudah melalui penyesuaian kategori
deterministik. Data dibagi menjadi training dan testing menggunakan
`train_test_split` dengan `stratify=y`. Imputasi, scaling, dan encoding
dilakukan dalam pipeline yang di-fit hanya pada data training.

### Hasil model
- Model: Logistic Regression
- Jumlah training: 4000
- Jumlah testing: 1000
- Accuracy: 0.6320

Classification report:
```text
              precision    recall  f1-score   support

       Aktif       0.66      0.73      0.69       564
       Churn       0.59      0.51      0.55       436

    accuracy                           0.63      1000
   macro avg       0.62      0.62      0.62      1000
weighted avg       0.63      0.63      0.63      1000

```

### Temuan dan rekomendasi
1. Kontrak bulanan memiliki tingkat churn lebih tinggi pada analisis awal.
   Evaluasi pengalaman pelanggan bulanan dan program retensi.
2. Perbedaan churn antarjenis layanan internet relatif kecil.
   Periksa faktor lain sebelum membuat keputusan berbasis jenis layanan.
3. Perbedaan antar-metode pembayaran juga relatif kecil.
   Teliti pengalaman pembayaran tanpa menyimpulkan hubungan sebab-akibat.

### File hasil
- `output/data_bersih.csv`: dataset hasil pembersihan.
- `output/kamus_data.csv`: deskripsi kolom dan tipe data.
- `laporan_kualitas.csv`: perbandingan kualitas sebelum dan sesudah.

### Catatan
Capping IQR merupakan keputusan pengolahan data, bukan bukti bahwa seluruh
nilai ekstrem adalah kesalahan. Temuan analisis bersifat deskriptif dan
tidak membuktikan sebab-akibat.
