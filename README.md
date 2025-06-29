
# 📊 Analisis Data _Bermain Dataset_ dengan Python

Proyek ini bertujuan untuk melakukan eksplorasi data dan visualisasi terhadap dataset `bermain_dataset.csv`. Analisis dilakukan di Google Colab menggunakan bahasa Python dan beberapa pustaka populer seperti Pandas, Seaborn, dan Matplotlib.

---

## 📁 Struktur Proyek

```
bermain-dataset/
├── bermain_dataset.csv
├── notebook.ipynb
└── README.md
```

---

## ✅ Langkah-Langkah Menjalankan Proyek

1. **Buka Google Colab**
   - Kunjungi: [https://colab.research.google.com](https://colab.research.google.com)

2. **Mount Google Drive**
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```

3. **Atur Path ke Dataset**
   ```python
   dataset_path = "/content/drive/MyDrive/tb/bermain_dataset.csv"
   ```

4. **Import Pustaka yang Dibutuhkan**
   ```python
   import pandas as pd
   import seaborn as sns
   import matplotlib.pyplot as plt
   ```

5. **Load Dataset**
   ```python
   df = pd.read_csv(dataset_path)
   ```

6. **Lihat Informasi Awal**
   ```python
   print("Shape:", df.shape)
   df.info()
   df.describe()
   ```

---

## 📈 Visualisasi Data

### Distribusi Kolom Kategori
```python
for col in df.columns:
    if df[col].dtype == 'object':
        plt.figure()
        sns.countplot(x=col, data=df)
        plt.title(f'Distribusi {col}')
        plt.xticks(rotation=45)
        plt.tight_layout()
        plt.show()
```

### Korelasi Antar Kolom Numerik
```python
plt.figure(figsize=(10,8))
sns.heatmap(df.select_dtypes(include='number').corr(), annot=True, cmap='coolwarm', fmt=".2f")
plt.title('Heatmap Korelasi')
plt.show()
```

> ⚠️ Pastikan dataset sudah bersih dari kolom non-numerik atau NaN sebelum melakukan korelasi.

---

## 🛠 Tools yang Digunakan

- [Google Colab](https://colab.research.google.com)
- Python 3
- Pandas
- Seaborn
- Matplotlib

---

## 📌 Catatan

- Dataset harus berada di folder yang sesuai: `MyDrive/tb/bermain_dataset.csv`
- Jika `sns.heatmap()` error, pastikan hanya kolom numerik yang dihitung korelasinya:
  ```python
  df.select_dtypes(include='number').corr()
  ```

---

## 🧑‍💻 Kontributor

- 📍 Proyek oleh: Andrean kosasih
-                 m.jamil alfadilah
