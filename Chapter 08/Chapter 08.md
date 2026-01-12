# CHAPTER 8: Dimensionality Reduction

Banyak real-world problems memiliki ribuan atau jutuan features, yang membuat training lambat dan meningkatkan overfitting. Chapter ini menunjukkan teknik untuk mengurangi jumlah features sambil mempertahankan informasi penting.

## Curse of Dimensionality

**Curse of Dimensionality** adalah fenomena di mana:
- Data high-dimensional menjadi sparse
- Pattern recognition menjadi lebih sulit
- Overfitting menjadi lebih mungkin terjadi
- Jarak antara points menjadi kurang meaningful

## Dua Approach Utama

### Projection
- Melipatkan data dari high-dimensional space ke lower-dimensional space
- Seperti project foto 3D ke foto 2D
- Mengasumsikan data terletak di lower-dimensional subspace

### Manifold Learning
- Mengasumsikan data terletak di manifold lower-dimensional yang embedded dalam high-dimensional space
- Lebih flexible daripada projection jika data memiliki complex nonlinear structure

## Principal Component Analysis (PCA)

**PCA** menemukan axes (principal components) sepanjang data memiliki variance paling besar.

### Implementasi PCA:
1. Standardize features (mean = 0, std = 1)
2. Compute covariance matrix
3. Compute eigenvectors (principal components) dan eigenvalues
4. Select k eigenvectors dengan eigenvalues terbesar
5. Project training data ke eigenvectors

### Keuntungan:
- Unsupervised learning, tidak memerlukan labels
- Mengurangi noise dalam data
- Mempercepat training
- Mengurangi memory requirements

### Kerugian:
- Kehilangan beberapa informasi
- Transformed features sulit diinterpretasi
- Lebih slow untuk large number of features

### Explained Variance Ratio
- Menunjukkan berapa banyak variance dijelaskan oleh setiap principal component
- Membantu memilih jumlah components yang tepat
- Cumulative explained variance 95% sering menjadi good threshold

## Variants of PCA

### Kernel PCA
- Memperluas PCA dengan kernel trick
- Mampu menemukan nonlinear patterns
- Menggunakan kernel functions (polynomial, RBF, sigmoid)

### Randomized PCA
- Faster approximation untuk large datasets
- Menggunakan randomized SVD algorithm

### Incremental PCA
- Berguna jika dataset terlalu besar untuk fit dalam memory
- Training pada mini-batches

## Manifold Learning

### Locally Linear Embedding (LLE)
- Mereplikasi local linear structure data dalam lower-dimensional space
- Berasumsi each instance dapat direkonstruksi dari its nearest neighbors
- Good untuk data dengan complex nonlinear structure

### Other Techniques
- t-SNE: excellent untuk visualization high-dimensional data
- Autoencoders: neural network approach untuk learning representations

## Trade-offs

- Mengurangi dimensionality dapat mempercepat training dan mengurangi memory
- Tetapi kehilangan beberapa informasi
- Dalam banyak kasus, noise filtering dari dimensionality reduction meningkatkan performance
- Trade-off antara computational efficiency dan model accuracy harus dipertimbangkan

## Kesimpulan

Dimensionality reduction adalah powerful technique untuk handling high-dimensional data. PCA adalah standard choice untuk linear dimensionality reduction, sementara manifold learning techniques cocok untuk nonlinear structures.

