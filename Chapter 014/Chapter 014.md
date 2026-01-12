# CHAPTER 14: Deep Computer Vision Using Convolutional Neural Networks

Computer vision adalah salah satu sukses terbesar deep learning. Chapter ini menjelaskan Convolutional Neural Networks (CNNs), architecture khusus untuk image processing.

## Convolutional Layers

**Convolutional Layers** berbeda dari dense layers:
- Setiap neuron connected ke small region dari input (receptive field), bukan seluruh input
- Filters slide across image, detecting local features
- Same filter applied di berbagai lokasi (weight sharing)
- Menghasilkan feature maps

### Benefits:
- **Local connectivity**: neurons aware dari small regions saja
- **Weight sharing**: reduce parameter count dramatically
- **Translation invariance**: detect features regardless of position

## Pooling Layers

**Pooling layers** mengurangi spatial dimensions:
- **Max pooling**: take maximum dari small region
- **Average pooling**: take average
- Reduces computation dan memory
- Captures translation invariance

## CNN Architectures

### Historical Progression:
- **LeNet-5**: Early CNN untuk digit recognition
- **AlexNet**: Breakthrough menggunakan ReLU, dropout, GPU training
- **VGGNet**: Deep networks dengan many small 3x3 filters
- **GoogLeNet/Inception**: Parallel paths dengan berbagai filter sizes
- **ResNet**: Residual connections untuk train very deep networks
- **Xception**: Depthwise separable convolutions untuk efficiency
- **SENet**: Squeeze-and-excitation blocks untuk channel attention

### Modern Architectures:
- **MobileNets**: Efficient untuk mobile/embedded devices
- **EfficientNet**: Scaling architecture dimensions systematically
- **Vision Transformers**: Attention-based alternative ke convolutions

## Transfer Learning

**Transfer Learning** dengan pre-trained models:
- Most models trained pada ImageNet (14M+ images, 1000 classes)
- Fine-tuning pada new task requires fraction of data dan time
- Strategies:
  1. Freeze base model, train top layers only
  2. Train all layers dengan small learning rate
  3. Gradually unfreeze layers dari top

## Computer Vision Tasks

### Image Classification
- Predict single class untuk entire image
- Standard task untuk most architectures

### Object Localization
- Predict class dan bounding box untuk object
- Add regression outputs untuk box coordinates

### Object Detection
- Identify multiple objects dan their bounding boxes
- Algorithms: YOLO, R-CNN, SSD, etc.
- Real-time detection possible dengan modern architectures

### Semantic Segmentation
- Classify setiap pixel dalam image
- Output spatial map dengan class predictions
- Fully Convolutional Networks (FCNs) untuk architecture

### Instance Segmentation
- Detect individual objects dan segment mereka
- Mask R-CNN adalah popular approach
- Combines object detection dan segmentation

## Data Augmentation untuk Vision

Techniques untuk increase effective training data size:
- Horizontal/vertical flips
- Rotations
- Shifts, crops, zooms
- Brightness, contrast adjustments
- Combinations through Albumentations atau tf.image

## Kesimpulan

CNNs revolutionized computer vision dengan incorporating local structure assumptions yang appropriate untuk images. Transfer learning membuat state-of-the-art results accessible bahkan untuk small datasets.
