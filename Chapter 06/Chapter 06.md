
# CHAPTER 6: Decision Trees

Decision Trees adalah algoritma intuitif yang memecah data secara rekursif menjadi subsets yang semakin homogen.

## Training Decision Trees

Penulis menjelaskan cara training Decision Tree menggunakan **CART (Classification and Regression Trees) algorithm**, yang memilih split yang meminimalkan impurity.

## Measures of Impurity

**Dua measure impurity dibahas:**

### Gini Impurity
- Probabilitas misclassifying random instance jika dilabel secara random menurut class distribution di node
- Gini = 1 - Σ(pᵢ²) di mana pᵢ adalah proportion dari class i
- Gini = 0 untuk pure node (single class)

### Entropy
- Measure of disorder, berkisar dari 0 hingga 1
- Entropy = -Σ(pᵢ log₂(pᵢ))
- Information gain = parent entropy - weighted child entropy

Dalam praktik, perbedaan antara Gini dan Entropy biasanya kecil.

## Regularization Hyperparameters

**Regularization hyperparameters mencegah overfitting:**

### max_depth
- Membatasi kedalaman tree
- Default = None (expand sampai semua leaves pure)
- Smaller depth = simpler model, less overfitting risk

### min_samples_split
- Minimum instances diperlukan untuk split node
- Default = 2
- Larger values = simpler model

### min_samples_leaf
- Minimum instances diperlukan di leaf node
- Default = 1
- Mencegah creation dari very small leaves

### max_features
- Maximum features yang dipertimbangkan untuk split di setiap node
- Menambahkan randomness, membantu reduce overfitting

## Decision Trees untuk Regression

Decision Trees dapat digunakan untuk **regression** dengan memilih split yang meminimalkan variance daripada impurity.

Untuk setiap region, prediksi adalah mean target value dari training instances di region tersebut.

## Instability - Kelemahan Utama

**Instability** adalah kelemahan utama Decision Trees:
- Kecil changes dalam data dapat menghasilkan tree yang sangat berbeda
- Sensitivitas tinggi terhadap rotasi data
- Tidak stabil untuk data dengan features berkorelasi

## Solusi: Ensemble Methods

Kelemahan ini dipecahkan dengan ensemble methods:
- **Random Forests**: Menggabungkan many decision trees dengan bagging
- **Gradient Boosting**: Sequentially building trees untuk correct previous errors
- Ensemble methods memberikan performa yang jauh lebih baik dibanding single tree

## Keuntungan Decision Trees

- Mudah dipahami dan diinterpretasikan
- Tidak memerlukan data preprocessing (scaling, normalization)
- Dapat handle mixed numerical dan categorical features
- Feature importance dapat diekstrak
- Computational complexity relatively low

## Kesimpulan

Decision Trees adalah powerful algorithm yang mudah dipahami, tetapi tanpa regularization mereka cenderung overfit. Ensemble methods seperti Random Forests dan Gradient Boosting mengatasi masalah ini dan memberikan performa superior untuk sebagian besar applications.
