# Customer Segmentation using K-Means Clustering

## Deskripsi Proyek
Segmentasi pelanggan (*Customer Segmentation*) adalah strategi pemasaran yang membagi basis pelanggan menjadi kelompok-kelompok individu yang memiliki kesamaan berdasarkan karakteristik tertentu, seperti pendapatan tahunan (*Annual Income*) dan skor pengeluaran (*Spending Score*). 

Dalam proyek ini, algoritma **K-Means Clustering** digunakan sebagai pendekatan *Unsupervised Learning* untuk mengelompokkan pelanggan ke dalam **5 cluster optimal** yang diidentifikasi melalui **Metode Elbow**.

## Dataset
Dataset yang digunakan dalam proyek ini adalah **Mall Customer Segmentation Data** yang diperoleh dari Kaggle.
* **Link Dataset:** [Kaggle - Mall Customer Segmentation Data](https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python)
* **File Data:** `Mall_Customers.csv`
* **Fitur yang Tersedia:**
  * `CustomerID`: ID Unik Pelanggan
  * `Gender`: Jenis Kelamin Pelanggan
  * `Age`: Usia Pelanggan
  * `Annual Income (k$)`: Pendapatan Tahunan Pelanggan (dalam ribuan dollar)
  * `Spending Score (1-100)`: Skor Pengeluaran yang Diberikan oleh Mall berdasarkan Perilaku Pelanggan

##  Alur Implementasi
Proyek dikerjakan secara sistematis melalui tahapan berikut di dalam file notebook:
1. **Data Loading & Exploration:** Membaca data menggunakan Pandas, memeriksa struktur data (`.info()`), dan mengecek nilai yang hilang (*missing values*).
2. **Data Preprocessing:** Mengekstraksi fitur numerik utama (`Annual Income` dan `Spending Score`) serta menerapkan **StandardScaler** untuk menyamakan skala data (skala jarak Euclidean).
3. **Penentuan K Optimal (Elbow Method):** Melakukan iterasi nilai $K$ dari 1 hingga 10 untuk menghitung *Within-Cluster Sum of Square* (WCSS) guna menemukan titik patahan (siku) optimal pada grafik.
4. **Model Training:** Melatih model K-Means menggunakan nilai $K=5$ dengan inisialisasi `k-means++`.
5. **Evaluasi Model Clustering:** Mengukur performa cluster menggunakan metrik khusus *Unsupervised Learning*:
   * **Silhouette Score** (Mengukur kerapatan dan pemisahan antar cluster).
   * **Davies-Bouldin Index** (Mengukur rasio penyebaran dalam cluster dengan jarak antar cluster).
6. **Visualisasi Data & Centroid:** Menampilkan grafik sebaran 2D berwarna untuk setiap cluster lengkap dengan penanda titik pusat (*Centroid*) masing-masing kelompok dalam skala asli.

## Hasil Evaluasi Model
Berdasarkan eksperimen dengan $K=5$, model berhasil mengelompokkan pelanggan dengan metrik performa yang sangat solid:
* **Silhouette Score:** `0.5547` (Menunjukkan struktur cluster yang wajar, terpisah dengan baik, dan signifikan).
* **Davies-Bouldin Index:** `0.5722` (Nilai di bawah 1.0 menandakan model memiliki tingkat tumpang tindih yang sangat rendah dan performa klasterisasi yang optimal).

### Hasil Segmentasi Kelompok Pelanggan:
* **Cluster 0:** Pelanggan dengan pendapatan menengah dan pengeluaran menengah (Rata-rata/Standar).
* **Cluster 1:** Pelanggan dengan pendapatan tinggi namun tingkat pengeluaran rendah (Hemat/Irit).
* **Cluster 2:** Pelanggan dengan pendapatan rendah dan tingkat pengeluaran rendah (Sangat Berhati-hati).
* **Cluster 3:** Pelanggan dengan pendapatan rendah namun tingkat pengeluaran tinggi (Impulsif).
* **Cluster 4:** Pelanggan dengan pendapatan tinggi dan tingkat pengeluaran tinggi (Target Pasar Utama / Sultan).

## Cara Menjalankan Proyek di Lokal

### 1. Kloning Repositori
```bash
git clone [https://github.com/raflhynuramadhan18/K-Means_Machine_Learning.git](https://github.com/raflhynuramadhan18/K-Means_Machine_Learning.git)
cd K-Means_Machine_Learning
