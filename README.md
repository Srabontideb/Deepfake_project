A deep learning-based system for detecting and classifying deepfake videos using 3D Convolutional Neural Networks with Inception architecture.

### Key Features:
- Multi-class Classification: Distinguishes between 6 video types.
- Temporal Analysis: Processes 20-frame sequences to detect cross-frame inconsistencies.
- 3D Inception Architecture: Multi-scale feature extraction for comprehensive artifact detection.
- Conditional Training: Handles class imbalance through targeted fine-tuning.
- Memory-Efficient: Uses memory-mapped arrays for large datasets.

### Architecture
###### 3D Inception Network:
The model uses a custom 3D Convolutional Neural Network inspired by Google's Inception architecture, adapted for video analysis.
###### Key Components:
- 9 Inception Blocks: Multi-scale feature extraction (1×1, 3×3, 5×5 convolutions + pooling)
- 3D Convolutions: Process video clips as 4D tensors (channels, time, height, width)
- Batch Normalization: Stabilizes training in deep networks
- Dropout (40%): Prevents overfitting

![Model](https://github.com/Srabontideb/Deepfake_project/blob/e4d9aba62379c5810c6e071e4edce175d6ab7fe9/Model.png)

### Dataset
FaceForensics++ - A large-scale benchmark for deepfake detection
Total Videos: ~5,441
Compression: c23 (moderate quality)
Resolution: 256×256 (cropped faces)
Frame Rate: 5 FPS (sampled)
Split: 80% train / 20% test

### Methodology
#### 1. Data Preprocessing
##### Face Extraction:
Extract frames from videos at 5 FPS
Detect faces using Haar Cascade Classifier
Crop and resize faces to 256×256 pixels
Save bounding box coordinates for consistency

##### Consistent Cropping:
Use same bounding boxes for original and manipulated videos
Ensures fair comparison between real and fake samples
Eliminates spatial bias

##### Data Organization:
Create lookup table for efficient video segment access
Split videos into 20-frame chunks
Use memory-mapped arrays to handle 38GB+ dataset


#### 2. Model Training
##### Phase 1: Initial Training (10 epochs):
- Train on full dataset (all 6 classes)
- Batch size: 36 video clips
- Optimizer: Adam (learning rate: 0.0001)
- Loss: Cross-Entropy

Result: 87% overall accuracy, but poor performance on minority classes

##### Phase 2: Conditional Training (5 epochs)
Problem Detected:
- NeuralTextures: Only 500 samples (minority class)
- FaceShifter: Only 800 samples (minority class)
Model biased toward majority classes

Solution - Transfer Learning:
- Load pre-trained model from Phase 1
- Fine-tune only on minority classes for 5 epochs

How it works:
Early layers (generic features) remain mostly unchanged
Deep layers (task-specific features) adapt significantly
Classification layer adjusts decision boundaries

Result: FaceShifter accuracy improves from 65% → 82%, NeuralTextures from 58% → 78%

##### Phase 3: Re-balancing (2 epochs)
Purpose: Prevent over-specialization on minority classes
- Train on full dataset again for just 2 epochs
- Maintains minority class improvements
- Restores majority class performance
- Achieves balanced accuracy across all classes

#### 3. Evaluation
- Confusion matrix analysis
- Per-class accuracy metrics
- Loss curves visualization
- Identification of commonly confused pairs

### Requirements
##### Hardware
- GPU: NVIDIA GPU with 16GB+ VRAM (Tesla T4 or better)
- RAM: 32GB recommended
- Storage: ~150GB for dataset and processed data

##### Software
- Python 3.8+
- PyTorch 2.0+
- CUDA 11.0+ (for GPU acceleration)

##### Key Libraries
- torch & torchvision - Deep learning framework
- opencv-python - Video processing and face detection
- numpy - Numerical operations
- pandas - Data management
- scikit-learn - Train/test splitting
- scikit-image - Image similarity metrics
- matplotlib & seaborn - Visualization
