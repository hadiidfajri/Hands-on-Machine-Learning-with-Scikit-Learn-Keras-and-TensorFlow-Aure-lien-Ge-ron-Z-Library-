# CHAPTER 15: Processing Sequences Using RNNs and CNNs

Sequences seperti time series, text, dan speech memerlukan special handling. Recurrent Neural Networks (RNNs) memproses sequences element-by-element sambil maintaining hidden state.

## Recurrent Neurons

**Recurrent Neurons** memiliki internal state yang diupdate setiap timestep:
- Output tergantung pada current input dan previous hidden state
- Creating "memory" dari previous inputs
- Dapat process variable-length sequences

## Training RNNs: Backpropagation Through Time

**Backpropagation Through Time (BPTT)** compute gradients dengan unrolling network melalui time:
- Forward pass: compute predictions untuk each timestep
- Backward pass: propagate errors backward through time
- Challenges:
  - Vanishing/exploding gradients untuk long sequences
  - Computational complexity sebanding dengan sequence length

## Long Short-Term Memory (LSTM)

**LSTM** adalah advanced RNN architecture yang addresses vanishing gradient problem:

### Key Components:
- **Cell state**: long-term memory
- **Forget gate**: decide apa dari previous cell state untuk keep
- **Input gate**: decide apa dari current input untuk add
- **Output gate**: decide apa dari cell state untuk output

### Advantages:
- Dapat learn long-term dependencies
- Gradient flow lebih smooth
- Standard choice untuk sequence modeling

## Gated Recurrent Units (GRUs)

**GRUs** adalah simpler variant dari LSTM:
- Fewer parameters (reset dan update gates hanya)
- Similar performance dalam banyak tasks
- Faster training

## Time Series Forecasting

### Univariate Forecasting
- Predict next value(s) dalam sequence
- Use sliding window untuk create training instances
- Metrics: MAE, RMSE, MAPE

### Multivariate Forecasting
- Multiple time series digunakan untuk predict
- More realistic untuk real-world problems

### Multi-step Forecasting
- Predict multiple steps ahead
- Sequence-to-sequence architecture
- Teacher forcing vs free-running mode

## Deep RNNs

**Stacking multiple RNN layers**:
- Learn more complex temporal patterns
- Each layer adds capability untuk learn higher-level features
- Trade-off: increased parameters dan training time

## CNNs untuk Sequences

**Convolutional approaches** untuk sequences:
- **WaveNet**: 1D convolutions untuk audio generation
- **Temporal Convolutional Networks**: efficient untuk forecasting
- Parallel computation possible (unlike RNNs)

## Stateful RNNs

**Stateful RNNs** maintain state across batches:
- Useful ketika sequences sangat panjang
- Must process dalam consistent batch sizes
- Manual state management required

## Kesimpulan

RNNs powerful untuk sequence processing, LSTM gold standard untuk most applications. CNNs emerging sebagai alternative dengan better parallelization properties. Attention mechanisms (covered di Chapter 16) providing additional improvements.

