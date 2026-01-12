# CHAPTER 3: Classification

Chapter ini berfokus pada classification tasks, dengan dataset MNIST sebagai studi kasus - kumpulan 70,000 gambar digit tulisan tangan.

## Binary Classification dengan MNIST

Penulis mulai dengan training binary classifier untuk mendeteksi digit 5 vs bukan 5, menggunakan SGDClassifier (Stochastic Gradient Descent Classifier).

Prosesnya meliputi:
- Loading dataset MNIST
- Membuat target labels binary (5 vs non-5)
- Training model menggunakan SGD
- Testing predictions pada new instances

## Performance Measures untuk Classification

Performance measures untuk classification jauh lebih kompleks daripada regression:

### Accuracy
- Rasio prediksi yang benar dari total prediksi
- Bisa menyesatkan jika dataset tidak seimbang (imbalanced classes)

### Confusion Matrix
- Menampilkan true positives, false positives, true negatives, false negatives
- Memberikan gambaran komprehensif tentang jenis-jenis error yang dibuat model

### Precision dan Recall
- **Precision**: Dari prediksi positif yang dibuat model, berapa banyak yang benar (TP / (TP + FP))
- **Recall**: Dari semua instance positif yang sebenarnya, berapa banyak yang teridentifikasi dengan benar (TP / (TP + FN))

### Precision-Recall Trade-off
- Meningkatkan precision berarti mengurangi recall, dan sebaliknya
- Diperlukan threshold decision yang tepat tergantung pada business requirements
- F1 score adalah harmonic mean antara precision dan recall

## ROC Curves dan ROC AUC

**ROC (Receiver Operating Characteristic) Curves** dan **ROC AUC Score**:
- ROC curve menampilkan trade-off antara true positive rate dan false positive rate pada berbagai threshold
- Area Under the Curve (AUC) memberikan metrik single number untuk membandingkan classifiers
- AUC = 1 untuk perfect classifier, AUC = 0.5 untuk random classifier

## Multiclass Classification

Chapter melanjutkan dengan **multiclass classification**, di mana ada lebih dari dua kelas. Dua strategi utama dijelaskan:

### One-vs-Rest (OvR)
- Melatih satu classifier untuk setiap kelas
- Total classifiers = jumlah kelas
- Lebih efisien untuk binary classifiers

### One-vs-One (OvO)
- Melatih satu classifier untuk setiap pair kelas
- Total classifiers = N * (N-1) / 2
- Lebih efisien untuk non-linear classifiers seperti SVM

Scikit-Learn secara otomatis memilih strategi yang tepat berdasarkan jenis classifier.

## Multilabel dan Multioutput Classification

### Multilabel Classification
- Setiap instance dapat memiliki multiple labels yang tidak mutually exclusive
- Contoh: foto dapat memiliki multiple people yang dikenali
- Evaluation menggunakan per-label metrics atau averaged metrics

### Multioutput Classification
- Generalisasi dari multilabel classification
- Setiap label bisa multiclass (bukan hanya binary)
- Contoh: image denoising di mana output adalah pixel intensity values

## Error Analysis

Penulis menunjukkan cara melakukan error analysis:
- Menggunakan confusion matrix untuk mengidentifikasi di mana model membuat kesalahan
- Fokus pada tipe-tipe error yang paling costly untuk bisnis
- Menganalisis individual misclassifications untuk mendapatkan insights
- Menggunakan visualisasi untuk memahami pola dalam errors

## Kesimpulan

Chapter ini memberikan pemahaman komprehensif tentang classification tasks, dari metrics evaluasi yang tepat hingga handling berbagai jenis classification problems (binary, multiclass, multilabel, multioutput) dan error analysis yang efektif.

