
# CHAPTER 7: Ensemble Learning and Random Forests

Chapter ini menunjukkan bagaimana menggabungkan multiple weak learners menjadi strong learner yang memiliki performa superior.

## Voting Classifiers

**Voting Classifiers** mengagregasi prediksi dari multiple classifiers berbeda:

### Hard Voting
- Mengambil class yang paling banyak dipilih oleh semua classifiers
- Effectif jika individual classifiers membuat errors yang berbeda

### Soft Voting
- Mengrata-rata probabilities dari semua classifiers
- Memilih class dengan highest average probability
- Biasanya lebih baik daripada hard voting

## Bagging (Bootstrap Aggregating)

**Bagging** melatih klasifier yang sama pada random subsets dari training data:
- Sampling with replacement (bootstrap)
- Setiap subset digunakan untuk melatih independent learner
- Prediksi akhir adalah aggregation dari semua learners

### Keuntungan:
- Mengurangi variance, terutama efektif untuk high-variance models seperti Decision Trees
- Sangat parallelizable

### Out-of-Bag Evaluation
- Instances yang tidak dipilih dalam bootstrap dapat digunakan untuk evaluation
- Memberikan unbiased estimate tanpa perlu separate validation set

## Random Forests

**Random Forests** adalah ensemble Decision Trees yang menggunakan bagging dan menambahkan extra randomness:
- Setiap split mempertimbangkan random subset dari features
- Ini lebih mengurangi correlation antara trees
- Sangat powerful dan sering menjadi baseline untuk banyak problems
- Out-of-the-box performance excellent tanpa extensive tuning

### Feature Importance
- Dapat diekstrak dari Random Forest
- Menunjukkan fitur mana yang paling mendorong prediksi
- Useful untuk feature selection dan understanding

## Extra Trees

**Extra Trees (Extremely Randomized Trees)** meningkatkan randomness:
- Menggunakan random thresholds untuk setiap feature
- Training lebih cepat karena tidak perlu search untuk optimal split
- Slight peningkatan bias tetapi significant reduction dalam variance

## Boosting

**Boosting** melatih weak learners secara sequential:
- Setiap learner memperbaiki kesalahan dari predecessornya
- Instances yang diprediksi salah mendapat weight lebih besar

### AdaBoost
- Meningkatkan weight instances yang diprediksi salah
- Memaksa learner berikutnya fokus pada hard instances
- Kombinasi dari many weak learners membuat strong learner
- Sequential training (tidak parallelizable)

### Gradient Boosting
- Setiap learner baru memprediksi residuals (prediction errors) dari ensemble sebelumnya
- Sering menghasilkan performa excellent
- Rentan terhadap overfitting jika tidak diregularisasi dengan baik
- XGBoost adalah optimized implementation yang powerful

## Stacking

**Stacking** menggabungkan multiple models berbeda:
- Meta-learner (blender) belajar bagaimana best mengagregasi predictions
- Base learners membuat predictions pada training data
- Meta-learner dilatih pada predictions dari base learners
- Dapat menghasilkan excellent results jika base learners membuat komplementer errors

## Kesimpulan

Ensemble methods adalah powerful techniques yang sering menghasilkan better performance dibanding single models. Random Forests adalah praktis dan powerful default choice, sementara Gradient Boosting dapat memberikan state-of-the-art results dengan proper tuning.
