
# Laporan Proyek UAS AI - Prediksi Aktivitas Bermain Berdasarkan Cuaca dan Suhu Menggunakan Algoritma Decision Tree

## 1. Domain Proyek

Aktivitas bermain anak-anak dipengaruhi oleh berbagai faktor lingkungan, salah satunya adalah kondisi cuaca dan suhu. Dengan adanya prediksi terhadap kondisi cuaca, kita dapat memperkirakan apakah suatu aktivitas bermain layak dilakukan atau tidak.

Teknologi machine learning memungkinkan analisis dan prediksi aktivitas berdasarkan data historis. Salah satu algoritma yang cocok untuk kasus klasifikasi seperti ini adalah **Decision Tree**, yang dapat mengidentifikasi pola dari fitur cuaca untuk memutuskan apakah bermain di luar ruangan bisa dilakukan atau tidak.

## 2. Business Understanding

### Problem Statement
- Bagaimana memprediksi apakah aktivitas bermain dapat dilakukan berdasarkan data cuaca dan suhu?
- Bagaimana penerapan algoritma Decision Tree dalam kasus klasifikasi sederhana seperti ini?

### Goals
- Membuat model prediksi aktivitas bermain berdasarkan cuaca dan suhu.
- Menerapkan dan memvisualisasikan hasil model Decision Tree.
- Mengevaluasi akurasi model menggunakan metrik evaluasi sederhana.

### Solution Statement
Solusi dari masalah ini adalah:
1. Mengumpulkan data aktivitas bermain berdasarkan suhu dan cuaca.
2. Melakukan eksplorasi dan visualisasi data.
3. Melatih model Decision Tree menggunakan data tersebut.
4. Mengevaluasi model dengan metrik akurasi dan visualisasi hasil prediksi.

## 3. Data Understanding

### Visualisasi Distribusi Fitur
Untuk memahami pola dalam data, dibuat grafik batang distribusi dari masing-masing fitur:

- **Distribusi Cuaca**: Jumlah data tertinggi adalah cuaca Cerah dan Hujan.
- **Distribusi Suhu**: Suhu Dingin mendominasi dataset.
- **Distribusi Aktivitas Bermain**: Mayoritas data menunjukkan anak bermain di kondisi yang ada.

Visualisasi ini membantu mengetahui proporsi data dan mendukung proses modeling.


Dataset yang digunakan merupakan dataset sederhana yang terdiri dari fitur:
- `Outlook`: kondisi cuaca (Sunny, Overcast, Rain)
- `Temperature`: suhu udara (Hot, Mild, Cool)
- `Play`: target/label (Yes jika bermain, No jika tidak)

Contoh isi data:

| Outlook | Temperature | Play |
|---------|-------------|------|
| Sunny   | Hot         | No   |
| Overcast| Mild        | Yes  |
| Rain    | Cool        | Yes  |

### Distribusi Kelas
- Yes (Bermain): 9 data
- No (Tidak bermain): 5 data

Dataset memiliki ukuran kecil (14 baris), namun cukup untuk demonstrasi algoritma klasifikasi dasar.

## 4. Data Preparation

1. **Encoding**: Data kategorikal diubah menjadi format numerik agar bisa diproses model.
   - `Outlook`: Sunny=0, Overcast=1, Rain=2
   - `Temperature`: Hot=0, Mild=1, Cool=2
   - `Play`: No=0, Yes=1

2. **Split Data**: Dataset dibagi menjadi data latih (80%) dan data uji (20%) menggunakan `train_test_split`.

## 5. Modeling

Model yang digunakan adalah **Decision Tree Classifier** dari scikit-learn.

```python
from sklearn.tree import DecisionTreeClassifier
from sklearn.model_selection import train_test_split

model = DecisionTreeClassifier()
model.fit(X_train, y_train)
```

Model kemudian digunakan untuk memprediksi data uji:

```python
prediksi = model.predict(X_test)
```

## 6. Evaluation

Model dievaluasi menggunakan akurasi.

```python
from sklearn.metrics import accuracy_score
accuracy = accuracy_score(y_test, prediksi)
print("Akurasi:", accuracy)
```

Contoh hasil:
- **Akurasi: 1.0 (100%)** pada data uji sederhana.

Model juga divisualisasikan menggunakan:

```python
from sklearn.tree import plot_tree
plot_tree(model, feature_names=['Outlook', 'Temperature'], class_names=['No', 'Yes'], filled=True)
```

Hasil visualisasi menunjukkan bagaimana keputusan dibuat berdasarkan fitur cuaca dan suhu.

## 7. Kesimpulan

- Algoritma Decision Tree mampu mempelajari pola sederhana dari data cuaca dan suhu untuk memprediksi aktivitas bermain.
- Dengan dataset kecil dan bersih, akurasi model bisa mencapai 100%.
- Model dapat digunakan untuk edukasi dan demonstrasi dasar machine learning, serta dapat dikembangkan untuk data cuaca nyata di masa depan.

## 8. Referensi

1. Risanti, F. et al. (2024). *Analisis Model Prediksi Cuaca Menggunakan Decision Tree*. Prosiding SNF UNJ. https://journal.unj.ac.id/unj/index.php/prosidingsnf/article/view/41625  
2. Fikry, U. et al. (2023). *Implementasi Data Mining pada Dataset Prakiraan Cuaca Menggunakan C4.5*. Jurnal Alkhawarizmi. https://ojs.jurnalmahasiswa.com/ojs/index.php/alkhawarizmi/article/view/255  
3. Rajesh, K. (2013). *Decision Tree for the Weather Forecasting*. International Journal of Computer Applications. https://research.ijcaonline.org/volume76/number2/pxc3890620.pdf  
