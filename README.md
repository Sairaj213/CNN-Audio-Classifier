# <ins>CNN-Audio-Classifier<ins>
<br>

## UrbanSound8K Audio Classification with CNN

CNN(Convolutional Neural Network) for Audio Classification using [UrbanSound8K Dataset](https://urbansounddataset.weebly.com/urbansound8k.html). Audio clips are transformed into Mel spectrograms, then Image Array, and used as inputs combined with labels fed to CNN to classify 10 types of urban sounds.
<br>

## 🔊 Dataset

**UrbanSound8K**

- 8732 labeled sound excerpts 
- 10 classes: `air_conditioner`, `car_horn`, `children_playing`, `dog_bark`, `drilling`, `engine_idling`, `gun_shot`, `jackhammer`, `siren`, `street_music`
- Pre-sorted into 10 folds

More details: [UrbanSound8K Dataset](https://urbansounddataset.weebly.com/urbansound8k.html)
<br>
<br>

## 🧠 Model Architecture

This CNN treats Mel spectrograms as 2D grayscale images:

```text
Input (128x128x1)
├── Conv2D(32) + ReLU
├── BatchNormalization
├── MaxPooling2D
├── Conv2D(64) + ReLU
├── BatchNormalization
├── MaxPooling2D
├── Dropout(0.3)
├── Conv2D(128) + ReLU
├── BatchNormalization
├── MaxPooling2D
├── Dropout(0.3)
├── Flatten
├── Dense(128) + ReLU
├── Dropout(0.4)
└── Dense(10) + Softmax
```

## 🛠️ Preprocessing Pipeline

1. Load audio clips (≤4 seconds)
2. Convert to Mel spectrogram (128 mel bands)
3. Normalize and scale to [0, 1]
4. Resize to 128x128 pixels
5. Add channel dimension for CNN input


## 🧪 Training

- **Train/Validation/Test Split**: 70% / 15% / 15% 
- **Loss**: Sparse Categorical Crossentropy
- **Optimizer**: Adam
- **Epochs**: 30 (Early Stopping applied)


## 📈 Performance

| Metric        | Score       |
|---------------|-------------|
| Train Accuracy| ~96.0%      |
| Val Accuracy  | ~87.7%      |
| Test Accuracy | ~86.4%      |




