
# CHAPTER 4: Training Models

Chapter ini menggali lebih dalam bagaimana model-model machine learning dilatih, menjelaskan mekanisme "di balik layar" dari algoritma-algoritma pembelajaran.

## Linear Regression

**Linear Regression** adalah poin awal, menjelaskan cara memprediksi nilai numerik sebagai kombinasi linear dari features.

Persamaan model:
```
y = θ₀ + θ₁x₁ + θ₂x₂ + ... + θₙxₙ
```

di mana θ adalah model parameters yang perlu dioptimasi.

## Dua Cara Melatih Linear Regression

### 1. Normal Equation
- Solusi closed-form yang langsung menghitung parameter optimal
- Menyelesaikan: θ = (X^T X)^(-1) X^T y
- Kompleksitas O(n²) atau O(n³), tidak efisien untuk dataset besar dengan banyak features
- Menggunakan matrix inversion atau SVD decomposition

### 2. Gradient Descent
- Algoritma iteratif yang secara bertahap menyesuaikan parameter untuk meminimalkan cost function
- Dimulai dengan random initialization, kemudian iteratively update weights

**Tiga varian Gradient Descent:**

#### Batch Gradient Descent
- Menggunakan seluruh dataset per iteration
- Stabil tetapi lambat
- Computationally expensive untuk large datasets

#### Stochastic Gradient Descent (SGD)
- Menggunakan satu instance per iteration
- Cepat tetapi noisy (high variance)
- Dapat handle huge datasets yang tidak fit dalam memory
- Baik untuk online learning

#### Mini-batch Gradient Descent
- Kompromi antara keduanya menggunakan small batch (32, 128, 256 instances)
- Cepat dengan lebih stable dibanding pure SGD
- Best in practice untuk training modern neural networks

## Learning Rate

**Learning Rate** adalah hyperparameter kritis yang menentukan ukuran step dalam gradient descent:
- Rate terlalu kecil: konvergensi sangat lambat
- Rate terlalu besar: mungkin divergence atau overshoot optimal solution
- Dipilih melalui grid search atau eksperimen

## Polynomial Regression

**Polynomial Regression** memungkinkan fitting data nonlinear:
- Menambahkan powers dari features sebagai features baru
- Contoh: x, x², x³ sebagai features
- Memungkinkan model learn curved relationships
- Increased risk of overfitting dengan high-degree polynomials

## Learning Curves

**Learning Curves** adalah tool diagnostic:
- Plot training error vs validation error sebagai fungsi training set size
- Mendeteksi underfitting (bias tinggi): training dan validation error sama tingginya dan tinggi
- Mendeteksi overfitting (variance tinggi): large gap antara training dan validation error

## Regularized Linear Models

Mengurangi overfitting dengan menambahkan penalty pada cost function:

### Ridge Regression (L2)
- Menambahkan α * Σ(θᵢ²) ke cost function
- Semua weights dipusatkan ke nol tetapi jarang menjadi exactly zero
- Hyperparameter α mengontrol strength regularization

### Lasso Regression (L1)
- Menambahkan α * Σ|θᵢ| ke cost function
- Cenderung membuat weights menjadi exactly zero (automatic feature selection)
- Menghasilkan sparse models
- Dapat unstable jika features berkorelasi tinggi

### Elastic Net
- Kombinasi L1 dan L2 regularization
- Menambahkan r * Σ|θᵢ| + (1-r) * Σ(θᵢ²) ke cost function
- Menggabungkan benefits dari Ridge dan Lasso

## Logistic Regression

**Logistic Regression** adalah metode untuk binary classification:
- Menggunakan logistic function σ(z) = 1 / (1 + e^(-z)) untuk transformasi output linear menjadi probabilitas
- Output adalah probability bahwa instance termasuk positive class
- Decision boundary pada probability = 0.5
- Cost function: log loss (cross-entropy)

## Softmax Regression

Generalisasi untuk **multiclass classification**:
- Satu output neuron per kelas
- Menggunakan softmax activation untuk menormalisasi outputs ke probability distribution
- Multinomial logistic regression

## Kesimpulan

Chapter ini memberikan pemahaman mendalam tentang matematika di balik training, termasuk cost functions, gradients, dan convergence conditions. Understanding ini essential untuk memilih algoritma yang tepat dan tune hyperparameters secara efektif.
