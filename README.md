# Pijak by IBM — Submission Dicoding

**Deskripsi Singkat:**
- **Proyek:** Implementasi analisis clustering dan klasifikasi untuk dataset transaksi (bagian dari tugas submission Dicoding pada program "Pijak by IBM").
- **Tujuan:** Mempelajari dan menerapkan teknik unsupervised learning (clustering) dan supervised learning (classification) untuk memahami pola transaksi, segmentasi pelanggan / transaksi, serta membangun model prediktif sederhana.

**Isi Analisis yang Dipelajari (Ringkasan):**
- **Pra-pemrosesan:** Membersihkan data, menangani nilai hilang, normalisasi/skala fitur (StandardScaler/MinMax), dan encoding variabel kategorikal bila perlu.
- **Clustering:**
  - Teknik yang dipelajari: PCA untuk reduksi dimensi dan visualisasi, serta metode clustering seperti K-Means (atau algoritma serupa) untuk menemukan kelompok alami pada data.
  - Pemilihan jumlah cluster: mengaplikasikan metode Elbow / Silhouette untuk menentukan jumlah cluster yang cocok.
  - Insight umum: clustering membantu menemukan segmentasi transaksi (mis. transaksi kecil vs besar, pola frekuensi, atau grup yang berpotensi anomali). PCA memperjelas struktur data dengan mereduksi noise dan fitur yang berkorelasi.
- **Klasifikasi:**
  - Alur yang dipelajari: split data train/test, feature engineering, training model, hyperparameter sederhana, dan evaluasi menggunakan metrik seperti akurasi, precision, recall, F1, serta confusion matrix.
  - Model yang umum dipakai: pohon keputusan / Random Forest / model neural sederhana; model disimpan (contoh file model: `latihan_membuat_model.joblib`, `model_clustering.h5`).
  - Insight umum: setelah pra-pemrosesan yang baik, model klasifikasi dapat mengidentifikasi kelas transaksi dengan performa wajar; metrik selain akurasi (precision/recall) penting bila kelas tidak seimbang.

**Proyek yang Dibuat & Tujuan:**
- **Apa yang dibuat:** Sebuah analisis end-to-end yang meliputi eksplorasi data, segmentasi (clustering), dan pembuatan model klasifikasi sederhana untuk dataset transaksi perbankan.
- **Tujuan fungsional:** Memahami pola transaksi, mengelompokkan data untuk insight bisnis (mis. segmentasi pelanggan atau deteksi anomali), dan menyediakan model dasar yang dapat dipakai sebagai alat bantu keputusan atau sebagai baseline untuk pengembangan lebih lanjut.

**File Penting dalam Workspace:**
- Notebook Clustering: file notebook analisis clustering (lihat notebook clustering untuk langkah detail).
- Notebook Klasifikasi: file notebook analisis klasifikasi (lihat notebook klasifikasi untuk langkah detail).
- Model dan artefak yang dihasilkan: `latihan_membuat_model.joblib`, `model_clustering.h5`, `PCA_model_clustering.h5`.
- Dataset contoh: folder `dataset/` berisi `bank_transactions_data_edited.csv`.

**Langkah Step-by-step Pengerjaan:**
1. Persiapan lingkungan
   - Siapkan Python 3.8+ dan install library utama: `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`, `joblib`, `tensorflow`/`keras` (jika ada model NN).
   - Contoh instalasi: `pip install pandas numpy scikit-learn matplotlib seaborn joblib tensorflow`.
2. Eksplorasi Data (EDA)
   - Muat dataset, cek dimensi, tipe data, nilai hilang, dan distribusi tiap fitur.
   - Visualisasi distribusi fitur penting dan korelasi antar fitur.
3. Pra-pemrosesan
   - Hapus atau imputasi nilai hilang.
   - Scaling (StandardScaler/MinMaxScaler) untuk fitur numerik.
   - Encoding untuk fitur kategorikal (One-Hot atau LabelEncoder bila perlu).
4. Analisis Clustering
   - Terapkan PCA untuk reduksi dimensi dan visualisasi (2D/3D scatter plot).
   - Gunakan Elbow / Silhouette untuk memilih jumlah cluster.
   - Jalankan K-Means (atau algoritma lain), analisis centroid, dan beri label cluster pada data.
   - Interpretasi: periksa rata-rata fitur tiap cluster untuk memahami karakteristik tiap grup.
5. Analisis Klasifikasi
   - Tentukan variabel target (jika ada) dan fitur predictor.
   - Bagi data menjadi train/test (mis. 80/20) dan lakukan cross-validation bila perlu.
   - Latih model (mis. RandomForest / MLP), lakukan tuning sederhana hyperparameter.
   - Evaluasi model menggunakan confusion matrix, precision, recall, F1-score.
   - Simpan model terlatih ke file (`joblib` atau `.h5`).
6. Pelaporan & Kesimpulan
   - Ringkas temuan penting: pola cluster, fitur yang berpengaruh, performa model klasifikasi, dan rekomendasi perbaikan.
7. Langkah Lanjutan (opsional)
   - Percobaan algoritma lain (DBSCAN, GaussianMixture, XGBoost).
   - Pipeline produksi: packaging model dengan API atau integrasi ke dashboard.

**Cara Reproduksi Singkat:**
- Buka kedua notebook (clustering & klasifikasi) di environment Jupyter/Colab.
- Jalankan sel secara berurutan dari atas setelah memastikan semua dependency terinstal.
- Untuk menjalankan model yang sudah disimpan, muat artefak model dengan `joblib.load()` atau `keras.models.load_model()` sesuai tipe file.

**Dependensi Utama:**
- Python, Pandas, NumPy, scikit-learn, matplotlib, seaborn, joblib, tensorflow/keras (opsional).

**Catatan & Rekomendasi:**
- Pastikan class imbalance ditangani (resampling, class weights) jika target klasifikasi tidak seimbang.
- Validasi hasil clustering dengan metrik internal (silhouette) dan interpretasi bisnis.
- Dokumentasikan asumsi preprocessing agar eksperimen reproducible.