# CHAPTER 10: Introduction to Artificial Neural Networks with Keras

Chapter ini memperkenalkan artificial neural networks (ANNs), model yang terinspirasi dari biological neurons dalam otak.

## Sejarah Singkat ANNs

Penulis memulai dengan sejarah, mulai dari:
- **Threshold Logic Units (TLUs)** dan **Perceptrons** (1957)
- Perceptrons hanya mampu belajar linear decision boundaries
- **Multilayer Perceptrons (MLPs)** mengatasi keterbatasan dengan stacking layers
- **Backpropagation** (1986) memungkinkan training MLPs yang dalam

## Perceptron Learning Rule

**Perceptron learning rule** secara iteratif menyesuaikan weights:
- Mencoba untuk meminimalkan prediction errors
- Konvergen untuk linearly separable data
- Limited power: tidak bisa solve XOR problem

## Multilayer Perceptrons (MLPs)

**MLPs** mengatasi keterbatasan Perceptrons:
- Input layer: passthrough neurons
- Hidden layers: compute features (non-linear transformations)
- Output layer: make final predictions
- Fully connected: setiap neuron di layer connected ke semua neurons di next layer

### Backpropagation Algorithm
- Menggunakan reverse-mode automatic differentiation
- Forward pass: compute predictions
- Backward pass: compute gradients untuk semua weights
- Update weights menggunakan gradient descent

## Keras API

**Keras** adalah high-level API yang membuat building neural networks straightforward.

### Tiga API Styles:

#### Sequential API
- Untuk linear stacks of layers
- Simple dan intuitif
- Model().add(layer) atau Sequential([layer1, layer2, ...])

#### Functional API
- Untuk complex architectures dengan multiple inputs/outputs
- Skip connections possible
- Lebih flexible daripada Sequential

#### Subclassing API
- Subclass keras.Model untuk maximum flexibility
- Implement sendiri forward pass di call() method
- Untuk researchers experimenting dengan novel ideas

## Praktik Building, Training, dan Evaluation

### Building Model
- Sequential API: create model, add layers (Dense, Flatten, etc.)
- Specify input shape, output size, activation functions

### Compiling Model
- Specify loss function (mse untuk regression, categorical_crossentropy untuk multiclass)
- Specify optimizer (sgd, adam, dll)
- Specify metrics untuk monitoring

### Training Model
- model.fit(X_train, y_train, epochs=30, validation_data=(X_val, y_val))
- Trains untuk specified epochs
- Validates pada validation set setiap epoch

### Evaluation dan Prediction
- model.evaluate(X_test, y_test): compute loss dan metrics
- model.predict(X_new): make predictions pada new data
- model.predict_classes(X_new): for classification

## Hyperparameter Tuning

**Architecture hyperparameters:**
- Number of hidden layers
- Number of neurons per layer
- Activation functions

**Training hyperparameters:**
- Learning rate
- Batch size
- Number of epochs
- Optimizer choice

Penulis merekomendasikan menggunakan RandomizedSearchCV dengan KerasRegressor wrapper untuk systematic tuning.

## Callbacks

**Callbacks** memungkinkan monitoring dan modification training:
- **ModelCheckpoint**: save best model
- **EarlyStopping**: stop jika validation performance tidak improve
- **ReduceLROnPlateau**: reduce learning rate jika stuck

## TensorBoard

**TensorBoard** adalah visualization tool powerful:
- Visualize learning curves
- Monitor metrics selama training
- Debug model architecture

## Kesimpulan

Keras membuat building dan training neural networks menjadi accessible bahkan untuk beginners. Sequential API adalah good starting point, Functional API untuk complex architectures, dan Subclassing API untuk maximum flexibility.

