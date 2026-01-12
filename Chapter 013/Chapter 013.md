# CHAPTER 13: Loading and Preprocessing Data with TensorFlow

Efisien loading dan preprocessing data adalah critical untuk training deep learning models pada large datasets.

## The Data API (tf.data)

**tf.data** menyediakan efficient tools untuk data loading dan preprocessing:

### Creating Datasets
- Dari NumPy arrays: tf.data.Dataset.from_tensor_slices()
- Dari files: tf.data.TextLineDataset(), tf.io.decode_csv()
- Dari generators: tf.data.Dataset.from_generator()
- Dari TFRecord files: tf.data.TFRecordDataset()

### Chaining Transformations
- `.map()`: apply function ke each element
- `.filter()`: filter elements berdasarkan condition
- `.batch()`: group elements ke batches
- `.shuffle()`: shuffle data (important untuk training)
- `.prefetch()`: load next batch selama current batch processing

```python
dataset = tf.data.Dataset.range(10)
dataset = dataset.shuffle(buffer_size=3)
dataset = dataset.batch(2)
for batch in dataset:
    print(batch)
```

## TFRecord Format

**TFRecord** adalah efficient binary format untuk storing large datasets:

### Advantages:
- Compressed storage
- Efficient read dari disk
- dapat streamed tanpa load full dataset

### Structure:
- Uses protocol buffers untuk serialization
- Example format untuk tabular data, SequenceExample untuk sequences

### Workflow:
1. Serialize data ke TFRecord
2. Read TFRecord dengan tf.data.TFRecordDataset()
3. Parse examples dengan tf.io.parse_example()

## Feature Preprocessing

### Categorical Encoding
- **One-hot encoding**: Small number of categories
- **Embeddings**: Large number of categories (learnable representations)

### Numerical Preprocessing
- Standardization: zero mean, unit variance
- Normalization: scale ke [0, 1]

### Keras Preprocessing Layers
```python
keras.layers.Normalization(axis=-1)
keras.layers.Rescaling(1./255)
keras.layers.StringLookup()
keras.layers.IntegerLookup()
keras.layers.CategoryEncoding()
```

Layers dapat fit pada training data dan apply same transformation ke test data.

## TF Transform

**TF Transform** adalah production-level tools:
- Compute preprocessing statistics dari training data
- Apply same transformations consistently di training dan serving
- Handle large-scale data

## TensorFlow Datasets (TFDS)

**TFDS** adalah collection of ready-to-use datasets:
- Can be downloaded dengan single command
- Automatic splitting ke train/validation/test
- Consistent preprocessing across datasets

## Putting It All Together

Typical pipeline:
1. Load raw data
2. Split ke train/validation/test
3. Create tf.data.Dataset
4. Apply transformations (shuffle, batch, prefetch)
5. Use dalam model.fit()

```python
dataset = tf.data.Dataset.from_tensor_slices((X, y))
dataset = dataset.shuffle(buffer_size=1000)
dataset = dataset.batch(32)
dataset = dataset.prefetch(tf.data.AUTOTUNE)

model.fit(dataset, epochs=10)
```

## Kesimpulan

Efficient data loading adalah crucial untuk deep learning. tf.data API menyediakan powerful tools untuk building efficient data pipelines yang dapat handle very large datasets.

