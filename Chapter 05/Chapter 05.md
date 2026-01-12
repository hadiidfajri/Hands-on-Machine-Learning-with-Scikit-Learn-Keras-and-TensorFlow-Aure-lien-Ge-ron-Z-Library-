# CHAPTER 5: Support Vector Machines

Chapter ini mengeksplorasi Support Vector Machines (SVMs), algoritma powerful yang bekerja baik untuk classification dan regression.

## Ide Fundamental SVM

Ide fundamental SVM adalah mencari "street" terlebar antara kelas-kelas - **margin** yang memisahkan data dengan jarak maksimal dari decision boundary. Klasifier dengan margin terbesar memiliki generalisasi yang lebih baik.

## Linear SVM Classification

**Linear SVM Classification** bekerja dengan sempurna jika data linearly separable:
- Mencari hyperplane yang memaksimalkan margin antara classes
- Support vectors adalah instances yang terletak di edge dari margin
- Decision boundary hanya tergantung pada support vectors, bukan semua instances

## Soft Margin Classification

Dalam praktik, data jarang linearly separable, sehingga **soft margin classification** digunakan:
- Memungkinkan beberapa instances melintasi decision boundary
- Hyperparameter C mengontrol trade-off antara margin dan classification errors
- C besar: penalti besar untuk misclassification (hard margin)
- C kecil: toleransi lebih besar untuk errors (soft margin)

## Nonlinear SVM Classification

**Nonlinear SVM Classification** menangani data nonlinearly separable dengan menggunakan **kernel trick**:
- Secara implisit memetakan data ke dimensi yang lebih tinggi tanpa perlu menghitung transformasi secara eksplisit
- Membuat komputasi tetap efisien

### Kernel Populer:

#### Polynomial Kernel
- Menciptakan polynomial features
- Hyperparameters: degree d dan coef0
- Berguna untuk moderately nonlinear data

#### Gaussian RBF Kernel
- Radial Basis Function yang powerful dan versatile
- Dapat menangani arbitrary complex nonlinear boundaries
- Hyperparameter: gamma γ mengontrol influence dari single training example
  - γ besar: sharp boundaries, risk overfitting
  - γ kecil: smoother boundaries, underfitting risk

#### Sigmoid Kernel
- Mirip dengan neural networks
- Jarang digunakan dalam praktik

## SVM Regression

**SVM Regression** menerapkan ide margin untuk regression tasks:
- Meminimalkan prediction errors sambil mempertahankan margin
- Hyperparameter ε menentukan margin threshold
- Instances di dalam margin dianggap acceptable, instances outside memiliki penalty

## Computational Complexity

- Complexity O(n²) hingga O(n³) tergantung implementasi
- Membuatnya kurang cocok untuk dataset sangat besar
- Bekerja well pada dataset medium dan memberikan hasil excellent
- Linear SVMs bekerja lebih baik pada very large datasets

## Mathematical Foundation

SVMs dibangun atas dasar optimization theory:
- **Dual problem**: transformasi dari primal optimization problem
- **Lagrange multipliers**: teknik untuk solving constrained optimization
- **Kernel trick**: memungkinkan implicit high-dimensional mappings

## Online SVMs

**Online SVMs** dapat menangani aliran data besar secara incremental, menjadikan mereka cocok untuk streaming data applications.

## Kesimpulan

SVMs adalah powerful algorithm yang excellent untuk medium-sized datasets dan nonlinear problems. Kernel trick memungkinkan fleksibilitas dalam handling complex nonlinear boundaries, sementara soft margin classification membuat mereka robust terhadap noisy data.

