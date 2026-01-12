# CHAPTER 12: Custom Models and Training with TensorFlow

Chapter ini menggali lebih dalam TensorFlow API untuk maximum flexibility dalam building custom models dan training procedures.

## TensorFlow Operations

**TensorFlow dapat digunakan seperti NumPy** untuk mathematical computations:

### Key Concepts:
- **Tensors**: Immutable, typed arrays (similar to NumPy arrays)
- **Variables**: Mutable tensors yang dapat dimodify dan tracked untuk gradients
- **GradientTape**: Context manager yang records operations untuk automatic differentiation

### Using TensorFlow like NumPy:
```python
import tensorflow as tf
a = tf.constant([[1, 2], [3, 4]])
b = tf.constant([[1, 0], [0, 1]])
c = tf.matmul(a, b)  # matrix multiplication
```

## Custom Components

### Custom Loss Functions
- Define sendiri loss function sesuai kebutuhan specific problem
- Implement sebagai Python function atau subclass tf.keras.losses.Loss
- Useful ketika standard losses tidak sesuai

### Custom Metrics
- Track custom quantities selama training
- Subclass tf.keras.metrics.Metric
- Useful untuk domain-specific evaluation

### Custom Layers
- Subclass keras.layers.Layer
- Implement build() untuk create weights
- Implement call() untuk forward pass
- Useful untuk layers tidak tersedia di Keras

### Custom Models
- Subclass keras.Model
- Implement call() method untuk custom forward pass
- Memberikan maximum flexibility untuk novel architectures

## Automatic Differentiation (Autodiff)

**TensorFlow dapat automatically compute gradients** menggunakan reverse-mode autodiff:

```python
with tf.GradientTape() as tape:
    y = model(X)
    loss = loss_fn(y, y_true)
gradients = tape.gradient(loss, model.trainable_variables)
```

Tape records semua operations, kemudian gradients dihitung backward.

## Custom Training Loops

Implement sendiri training steps untuk tasks yang tidak fit standar supervised learning:

```python
for epoch in range(num_epochs):
    for X_batch, y_batch in train_dataset:
        with tf.GradientTape() as tape:
            y_pred = model(X_batch)
            loss = loss_fn(y_batch, y_pred)
        gradients = tape.gradient(loss, model.trainable_variables)
        optimizer.apply_gradients(zip(gradients, model.trainable_variables))
```

## TensorFlow Functions dan Graphs

**@tf.function decorator** convert Python functions menjadi efficient TensorFlow graphs:
- Graphs dapat run pada GPUs dan TPUs
- Significantly faster untuk repeated execution
- Enable XLA compiler optimizations

```python
@tf.function
def train_step(X, y):
    with tf.GradientTape() as tape:
        y_pred = model(X)
        loss = loss_fn(y, y_pred)
    gradients = tape.gradient(loss, model.trainable_variables)
    optimizer.apply_gradients(zip(gradients, model.trainable_variables))
    return loss
```

## Saving Custom Models

Custom models dapat disave dan loaded dengan SavedModel format:
```python
model.save('my_custom_model')
loaded_model = tf.keras.models.load_model('my_custom_model')
```

Namun custom components memerlukan custom_objects parameter untuk loading.

## Kesimpulan

TensorFlow's flexibility memungkinkan building custom training loops dan models untuk advanced use cases. Automatic differentiation menghandle gradients computation, memudahkan experimentation dengan novel architectures dan training procedures.

