# CHAPTER 1: The Machine Learning Landscape

Chapter pertama ini memberikan fondasi konseptual tentang machine learning secara keseluruhan. Bab ini dimulai dengan mendefinisikan machine learning sebagai sains dan seni pemrograman komputer agar dapat belajar dari data, bukan sekadar mengeksekusi instruksi yang telah diprogram sebelumnya.

## Definisi dan Pentingnya Machine Learning

Penulis menjelaskan mengapa machine learning sangat berguna dibandingkan dengan pemrograman tradisional. Dalam pendekatan tradisional, programmer harus mengidentifikasi semua pola dan menulis aturan secara manual, sehingga menghasilkan kode yang kompleks dan sulit dipertahankan. Sebaliknya, machine learning memungkinkan sistem untuk secara otomatis belajar pola dari data, membuat sistem lebih fleksibel dan mampu beradaptasi dengan perubahan.

## Klasifikasi Machine Learning Systems

Chapter ini mengklasifikasikan machine learning systems ke dalam beberapa kategori penting:

### 1. Supervised Learning vs Unsupervised Learning

**Supervised Learning** dilatih dengan data berlabel (contohnya classification dan regression), sementara **Unsupervised Learning** bekerja dengan data tanpa label untuk menemukan struktur tersembunyi (seperti clustering).

### 2. Batch Learning vs Online Learning

**Batch Learning** melatih sistem sekali dengan seluruh dataset dan kemudian tidak belajar lagi, sedangkan **Online Learning** dapat belajar secara inkremental dari aliran data baru.

### 3. Instance-based vs Model-based Learning

**Instance-based Learning** mengingat contoh pelatihan dan membandingkannya dengan data baru, sementara **Model-based Learning** membangun model matematis dan menggunakannya untuk prediksi.

## Tantangan Utama dalam Machine Learning

Chapter ini membahas tantangan utama yang dapat menghambat kinerja model:

- **Data yang tidak cukup**: Sebagian besar algoritma memerlukan ribuan atau jutaan contoh untuk bekerja dengan baik
- **Data yang tidak representatif**: Jika data pelatihan tidak mewakili kasus baru dengan baik, model akan generalisasi dengan buruk
- **Data berkualitas rendah**: Data yang rusak atau berisi kesalahan akan mengurangi kinerja model
- **Fitur yang tidak relevan**: Fitur yang tidak berkontribusi pada prediksi dapat mengganggu pembelajaran
- **Overfitting**: Model belajar noise dalam data pelatihan, bukan pola umum
- **Underfitting**: Model terlalu sederhana untuk menangkap kompleksitas data

## Testing, Validasi, dan Tuning Hyperparameter

Chapter ini menekankan pentingnya:
- **Testing dan Validasi**: Mengevaluasi model pada data terpisah untuk mendapatkan estimasi kinerja yang tidak bias
- **Hyperparameter Tuning**: Memilih hyperparameter terbaik menggunakan teknik seperti cross-validation
- **Data Mismatch**: Memastikan data training, validation, dan test berasal dari distribusi yang sama

## Kesimpulan

Chapter ini memberikan landasan konseptual yang kuat untuk memahami machine learning sebagai bidang, termasuk berbagai jenis sistem pembelajaran, tantangan yang dihadapi, dan pentingnya evaluasi yang tepat. Ini adalah fondasi penting sebelum mempelajari algoritma dan teknik spesifik di chapter-chapter berikutnya.

