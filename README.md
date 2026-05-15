# 📚 Sistem Rekomendasi Buku (Book Recommendation System)

Di era literatur digital, kelimpahan informasi (*information overload*) sering membuat pengguna kesulitan menemukan buku yang sesuai dengan minat mereka. Proyek ini memecahkan masalah tersebut dengan membangun **Sistem Rekomendasi Buku Cerdas** yang mampu memberikan kurasi bacaan secara personal guna meningkatkan *engagement* pengguna.

Proyek ini menerapkan dua pendekatan algoritma *Machine Learning* yang berbeda: **Content-Based Filtering** dan **Collaborative Filtering**.

---

## 📊 Sumber Data
Dataset yang digunakan berasal dari Kaggle: **[Book Recommendation Dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset)**. 
Data terdiri dari tiga tabel utama:
*   `Books.csv`: Metadata buku (ISBN, Judul, Penulis, Penerbit, dll).
*   `Ratings.csv`: Histori *rating* (0-10) yang diberikan pengguna.
*   `Users.csv`: Data demografis pengguna (ID, Lokasi, Umur).

---

## 🛠️ Pendekatan dan Solusi Model

### 1. Content-Based Filtering
Pendekatan ini merekomendasikan buku berdasarkan **kemiripan fitur metadata** (dalam hal ini, Penulis buku).
*   **Metode:** Menggunakan **TF-IDF Vectorizer** untuk mengekstraksi bobot representasi teks dari nama penulis.
*   **Algoritma:** Menghitung tingkat kemiripan antar-buku menggunakan **Cosine Similarity**.
*   **Cara Kerja:** Jika pengguna menyukai buku dari penulis X, sistem akan merekomendasikan Top-N judul buku lain yang juga ditulis oleh penulis X atau penulis dengan kemiripan atribut tertinggi.

### 2. Collaborative Filtering
Pendekatan ini memprediksi ketertarikan pengguna terhadap suatu buku yang belum dibaca berdasarkan **pola historis komunitas**.
*   **Metode:** Membangun arsitektur **Deep Learning (RecommenderNet)** menggunakan Keras/TensorFlow.
*   **Algoritma:** Memanfaatkan *Embedding Layer* untuk menyandikan representasi laten dari `User-ID` dan `ISBN`, lalu menghitung kecocokan menggunakan *Dot Product* yang diakhiri dengan fungsi aktivasi *Sigmoid*.
*   **Cara Kerja:** Sistem mengenali pola kolektif (*implicit & explicit feedback*). Jika kelompok pengguna A dan pengguna B memiliki selera serupa, buku yang disukai pengguna B dapat direkomendasikan kepada pengguna A (*serendipity*).

---

## 📈 Evaluasi Performa

*   **Content-Based Filtering:** Dievaluasi menggunakan metrik **Precision**. Model mampu memberikan rekomendasi yang deterministik. Presisi sangat bergantung pada subset data dan kelengkapan fitur dari item.
*   **Collaborative Filtering:** Dievaluasi menggunakan **Root Mean Squared Error (RMSE)**. Berdasarkan riwayat pelatihan (*training*), model menunjukkan hasil yang stabil dan terhindar dari *overfitting* yang ekstrem:
    *   **Train RMSE:** ~0.1536
    *   **Validation RMSE:** ~0.2936

---

## 💻 Teknologi yang Digunakan
*   **Bahasa:** Python
*   **Manipulasi Data:** Pandas, NumPy
*   **Machine Learning:** Scikit-Learn (TF-IDF, Cosine Similarity)
*   **Deep Learning:** TensorFlow / Keras

---
*Proyek ini dikembangkan oleh Muhammad Iqbal Saputra.*
