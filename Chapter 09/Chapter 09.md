# CHAPTER 9: Unsupervised Learning Techniques

Chapter final dari Part I mencakup algoritma-algoritma untuk belajar dari unlabeled data.

## Clustering

**Clustering** mengelompokkan similar instances bersama tanpa label.

### K-Means
- Algorithm iteratif yang mempartisi data menjadi k clusters
- Meminimalkan within-cluster variance (inertia)
- Challenges:
  - Memilih k yang tepat
  - Sensitivitas terhadap initialization
  - Dapat stuck di local minima
- Solutions:
  - Elbow method untuk memilih k
  - Multiple inertializations dengan random_state
  - Silhouette analysis untuk evaluate cluster quality

### DBSCAN (Density-Based Spatial Clustering of Applications with Noise)
- Density-based clustering
- Menemukan clusters arbitrary shape
- Robust terhadap outliers (treated as noise)
- Hyperparameters: eps (neighborhood distance) dan min_samples
- Tidak perlu specify k di awal

### Hierarchical Clustering
- Membangun tree (dendrogram) dari clusters
- Agglomerative (bottom-up): start dari individual points, merge ke clusters
- Divisive (top-down): start dari single cluster, split into smaller clusters
- Linkage criteria: single, complete, average, Ward

### Applications of Clustering
- Customer segmentation untuk targeted marketing
- Image compression dengan clustering pixels
- Feature engineering untuk supervised learning
- Document clustering untuk information organization

## Gaussian Mixture Models (GMM)

**GMM** adalah probabilistic model yang berasumsi data dihasilkan dari mixture of Gaussian distributions.

### Keuntungan dibanding K-Means:
- Lebih flexible: each cluster memiliki own covariance matrix
- Dapat mengestimasi probability distribution
- Dapat predict probabilities untuk new instances
- Soft clustering: instances memiliki probability berbeda untuk setiap cluster

### EM Algorithm (Expectation-Maximization)
- Training algorithm untuk GMM
- E-step: compute responsibility (probability) untuk each instance terhadap each cluster
- M-step: update cluster parameters berdasarkan responsibilities
- Iteratively improve model likelihood

### Model Selection
- BIC dan AIC untuk selecting number of components
- Cross-validation dapat juga digunakan
- Bayesian Gaussian Mixtures sebagai alternative yang lebih robust

## Anomaly Detection

**Anomaly Detection** mengidentifikasi instances yang berbeda dari mayoritas (outliers atau anomalies).

### Methods:
- **PCA**: Instances dengan high reconstruction error adalah anomalies
- **Isolation Forest**: Anomalies mudah di-isolate dalam random splits
- **One-class SVM**: Learns boundary around normal instances
- **Local Outlier Factor (LOF)**: Compares density dari instances dengan neighbors

### Novelty Detection
- Detecting new instances yang berbeda dari training data
- Requires clean training data tanpa outliers

## Semi-Supervised Learning

Menggabungkan labeled dan unlabeled data:
- Useful ketika labeling mahal atau time-consuming
- **Self-training**: Train model pada labeled data, use untuk label unlabeled data
- **Label propagation**: Propagate labels dari labeled ke nearby unlabeled instances
- **Co-training**: Multiple models train setiap other's predictions

## Kesimpulan

Chapter ini memberikan toolkit lengkap untuk unsupervised learning. Clustering sangat useful untuk exploratory analysis dan customer segmentation, sementara anomaly detection powerful untuk fraud detection dan quality control.

