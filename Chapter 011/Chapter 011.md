# CHAPTER 11: Training Deep Neural Networks

Melatih deep neural networks lebih challenging daripada shallow networks karena beberapa masalah fundamental.

## Vanishing/Exploding Gradients Problem

Selama backpropagation, gradients dapat menjadi sangat kecil (vanishing) atau sangat besar (exploding) ketika propagating melalui many layers.

### Vanishing Gradients
- Gradients menjadi extremely small untuk early layers
- Early layers belajar very slowly
- Network tidak efektif belajar long-range dependencies

### Exploding Gradients
- Gradients menjadi extremely large
- Weights blow up, training unstable
- NaN values dapat terjadi

## Solutions untuk Vanishing Gradients

### Glorot (Xavier) Initialization
- Initialize weights dengan mean 0 dan carefully chosen variance
- Variance scaled dengan number of inputs dan outputs
- Memastikan signals tidak vanish atau explode dalam network depth

### He Initialization
- Similar ke Glorot tetapi optimized untuk ReLU activations
- Menggunakan variance = 2 / fan_in

### Batch Normalization
- Normalize aktivasi setiap layer
- Zero mean, unit variance setiap batch
- Dramatically accelerates training
- Acts sebagai regularizer, reducing overfitting
- Sedikit slow down inference time

### Gradient Clipping
- Clip magnitude of gradients selama training
- Prevents exploding gradients
- Set threshold untuk max gradient norm

## Activation Functions

### Step Function
- Digunakan di Perceptrons
- Tidak differentiable (tidak cocok untuk gradient descent)

### Logistic Sigmoid
- σ(z) = 1 / (1 + e^(-z))
- Saturate untuk extreme values
- Menghasilkan slow learning (vanishing gradient problem)

### Tanh
- tanh(z) = (e^z - e^(-z)) / (e^z + e^(-z))
- Similar issues dengan sigmoid
- Zero-centered output (slightly better)

### ReLU (Rectified Linear Unit)
- ReLU(z) = max(0, z)
- Tidak saturate untuk positive values
- Computationally efficient
- Default choice untuk hidden layers
- Issue: "dead ReLU" (neuron always output 0)

### Leaky ReLU
- LeakyReLU(z) = max(αz, z) untuk small α (e.g., 0.01)
- Solusi untuk dead ReLU problem
- Always allows small gradient untuk negative values

### ELU (Exponential Linear Unit)
- ELU(z) = z jika z > 0, α(e^z - 1) jika z ≤ 0
- Smoother derivative
- No dead unit problem

## Transfer Learning

**Transfer Learning** memanfaatkan knowledge dari task yang sudah dilatih sebelumnya:

### Pre-trained Models
- Banyak pre-trained models tersedia (ImageNet, etc.)
- Save training time dan data requirements
- Particularly useful untuk computer vision

### Fine-tuning Strategy
- Option 1: Freeze berat dari base model, hanya train top layers
- Option 2: Train semua layers dengan small learning rate
- Option 3: Gradually unfreeze layers dari top

## Advanced Optimizers

### Momentum
- Accumulate gradients dari steps sebelumnya
- Accelerate convergence, terutama pada plateaus
- Hyperparameter: momentum (usually 0.9)

### Nesterov Accelerated Gradient (NAG)
- Slightly better variant dari momentum
- Look ahead sebelum compute gradient

### AdaGrad
- Adaptive learning rates per parameter
- Frequently updated parameters mendapat smaller learning rates
- Good untuk sparse data

### RMSProp
- Adaptive learning rates considering recent gradients
- Divides learning rate dengan RMS dari recent gradients

### Adam (Adaptive Moment Estimation)
- Combines momentum dan RMSProp
- Adaptive learning rate per parameter dengan momentum
- Default good choice untuk most problems
- Hyperparameters: learning rate (default 0.001), beta_1 (0.9), beta_2 (0.999)

## Learning Rate Scheduling

Gradually mengurangi learning rate during training:
- Exponential decay: lr = lr0 * 0.1^(epoch / 10)
- Power scheduling: lr = lr0 * (1 + epoch)^(-0.5)
- Performance scheduling: reduce jika validation loss stops improving

## Regularization untuk Avoid Overfitting

### L1/L2 Regularization
- Add penalty untuk large weights: α * Σ|w| atau α * Σw²
- Encourage simpler models

### Dropout
- Randomly drop neuron activations selama training dengan probability p
- Very effective dan easy to implement
- Tidak affect inference time

### Max-Norm Regularization
- Constrain weight norms: ||w|| ≤ r
- Alternative approach untuk preventing overfitting

### Early Stopping
- Stop training ketika validation performance degrades
- Simple tetapi powerful technique

## Praktis Guidelines

1. Start dengan simple architecture, gradually increase complexity
2. Use batch normalization untuk deep networks
3. Choose activation function: ReLU untuk hidden, softmax untuk multiclass output
4. Use Adam optimizer dengan default parameters
5. Implement early stopping dengan validation set
6. Monitor learning curves untuk detect overfitting

## Kesimpulan

Training deep networks memerlukan careful attention ke initialization, activation functions, optimizers, dan regularization. Modern techniques seperti batch normalization dan ReLU activations membuat training much more practical.

