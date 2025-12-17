# 📘 Klasifikasi Pasien Penyakit Alzheimer Dari Orang Sehat Menggunakan Dataset Darwin

### 👤 Informasi

* **Nama:** Angger Rahmadi
* **Repo:** [UAS_Angger](https://github.com/LuffyNikaa/UAS_Data_Science.git)
* **Video:** #

---

### 1. 🎯 Ringkasan Proyek

Proyek ini bertujuan untuk menyelesaikan permasalahan klasifikasi kondisi ('P' atau 'H') berdasarkan analisis fitur-fitur dari tulisan tangan. Dataset yang digunakan adalah data tulisan tangan berdimensi tinggi (174 sampel, 452 fitur) yang mencakup berbagai metrik dari 25 trial.

**Aktivitas Utama:**
* Melakukan *data cleaning* dan preprocessing pada dataset Darwin.
* Membangun 3 model perbandingan: **KNN (Baseline)**, **Random Forest (Advanced)**, dan **Deep Learning (MLP)**.
* Melakukan evaluasi performa berdasarkan akurasi dan waktu komputasi.

---

### 2. 📄 Problem & Goals

**Problem Statements:**
* Dataset tulisan tangan yang sangat berdimensi tinggi (452 fitur) seringkali menyebabkan redundancy, noise, dan tantangan dalam mengidentifikasi fitur yang paling informatif, yang dapat menghambat performa dan efisiensi model machine learning.
* Diperlukan metode yang efektif untuk mengklasifikasikan kondisi ('P' atau 'H') dari data tulisan tangan yang kompleks ini, sambil menjaga efisiensi komputasi dan memberikan wawasan tentang fitur-fitur yang paling relevan.

**Goals:**
* Menganalisis dan memahami struktur data tulisan tangan berdimensi tinggi, termasuk distribusi kelas, korelasi antar fitur, dan potensi untuk reduksi dimensi.
* Membangun dan mengevaluasi berbagai model machine learning (KNN, Random Forest, Deep Learning/MLP) untuk klasifikasi kondisi 'P' dan 'H', dengan mempertimbangkan akurasi dan efisiensi waktu pelatihan.
* Mengidentifikasi trial dan jenis fitur yang paling prediktif, serta melakukan seleksi fitur strategis untuk mengoptimalkan performa model secara signifikan.
* Mengembangkan model klasifikasi yang robust dengan akurasi tinggi, terutama melalui optimasi fitur, yang dapat memberikan wawasan berguna untuk aplikasi di dunia nyata.

---

### 📁 Struktur Folder

```text
UAS_Exasens_Classification/
│
├── data/
│   └── data.csv         # Dataset utama
│
├── images/                 # Hasil Visualisasi & Plot Evaluasi
│   ├── Visualisasi 1.png
│   ├── Visualisasi 2.jpg
│   └── Visualisasi 3.png
│
├── models/                 # Model yang sudah dilatih (Saved Models)
│   ├── model_knn.pkl    # Baseline Model
│   ├── model_rf.pkl     # Random Forest Model
│   └── model_mlp.h5     # Deep Learning Model
│
├── notebooks/              # Jupyter Notebook eksperimen utama
│   └── 233307005_AnggerR_UAS.ipynb
│
├── Laporan UAS.pdf
├── requirements.txt        # Daftar library python
└── README.md
```

---

### 3. 📊 Dataset

* **Nama Dataset:** Darwin
* **File:** `data/data.csv`
* **Sumber:** [UCI Machine Learning Repository - Darwin](https://archive.ics.uci.edu/dataset/732/darwin)
* **Jumlah Data:** 174 Sampel
* **Tipe Masalah:** Classification

**Fitur Utama yang Digunakan:**

| Nama Fitur | Deskripsi | Tipe Data |
| :--- | :--- | :--- |
| **air_time1** | Waktu pena tidak menyentuh kertas pada trial pertama (milidetik) | Float |
| **total_time25** | Total waktu penyelesaian tugas pada trial ke-25 (milidetik) | Float |
| **pressure_mean1** | Tekanan pena rata-rata pada trial pertama (unit tekanan) | Float |
| **mean_speed_in_air1** | Kecepatan rata-rata pena di udara pada trial pertama (unit/s) | Float |
| **disp_index1** | JIndeks dispersi/keragaman gerakan pada trial pertama | Float |

---

### 4. 🔧 Data Preparation

Langkah-langkah preprocessing yang dilakukan dalam `233307005_AnggerR_UAS.ipynb`:

1.  **Cleaning:** Menghapus kolom `ID` yang tidak relevan.
2.  **Encoding:** Mengubah label *class* menjadi format numerik (Label Encoding).
3.  **Splitting:** Membagi data menjadi **80% Training** dan **20% Testing** (`random_state=42`).
4.  **Scaling:** Melakukan normalisasi data menggunakan **MinMaxScaler** agar rentang nilai fitur seragam (0-1), yang sangat penting untuk performa model KNN dan Neural Network.

---

### 5. 🤖 Modeling

Saya membangun tiga model dengan pendekatan berbeda:

**Model 1: K-Nearest Neighbors (Baseline)**
* Algoritma berbasis jarak.
* Parameter: `n_neighbors=5`.

**Model 2: Random Forest (Advanced)**
* Algoritma *Ensemble Learning* (Bagging).
* Parameter: `n_estimators=100`.

**Model 3: Deep Learning (MLP)**
* Arsitektur Neural Network (TensorFlow/Keras).
* Layer: 3 Hidden Layers (256, 128, 64 neuron) + Output Layer (Softmax).
* Optimizer: Adam.

---

### 6. 🧪 Evaluation

Berdasarkan hasil pengujian pada data test:

| Model | Accuracy | Training Time (s) | Analisis |
| :--- | :--- | :--- | :--- |
| **KNN (Baseline)** | **0.63** | **0.01s** | Paling cepat, tetapi akurasi terendah |
| **Random Forest** | **0.71%** | 0.30s | Akurasi tertinggi dengan waktu training masih cepat |
| **Deep Learning** | 0.69% | 3.33s | Waktu training paling lama, akurasi di antara KNN dan RF |

---

### 7. 🏁 Kesimpulan

* **Model Terbaik:** **Random Forest** dipilih sebagai model terbaik untuk kasus ini.
* **Alasan:** Random Forest menunjukkan kinerja terbaik dengan akurasi tertinggi sebesar 71.43%.
* **Insight:** Model K-Nearest Neighbors (KNN) adalah yang paling efisien dari segi waktu pelatihan, dengan rata-rata mendekati 0.00 detik per trial. Ini menjadikannya pilihan ideal untuk skenario di mana kecepatan pelatihan adalah prioritas utama dan sumber daya komputasi sangat terbatas. Model Random Forest juga sangat cepat, dengan rata-rata sekitar 0.11 detik per trial. Sebaliknya, model MLP membutuhkan waktu pelatihan yang jauh lebih lama, rata-rata sekitar 3.76 detik per trial, yang mengindikasikan kompleksitas komputasi yang lebih tinggi untuk model Deep Learning

---

### 8. 🔮 Future Work

* **Data Augmentation:** Menambah jumlah data sampel untuk meningkatkan performa Deep Learning.
* **Hyperparameter Tuning:** Melakukan GridSearch pada Random Forest untuk mencari parameter yang lebih optimal.
* **Advanced Deep Learning:** Mencoba arsitektur CNN 1D jika data dianggap sebagai sinyal.

---

### 9. 🔁 Reproducibility

Untuk menjalankan proyek ini di lokal komputer Anda:

1. **Clone Repository:**
   ```bash
   git clone [https://github.com/LuffyNikaa/UAS_Data_Science.git](https://github.com/LuffyNikaa/UAS_Data_Science.git)
   ```

2. **Jalankan Notebook:**
   Buka `notebooks/23307005_AnggerR_UAS.ipynb` menggunakan Jupyter Notebook atau VS Code.
