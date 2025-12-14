
# Tree-or-Not

Binary image classification model to detect trees in images using PyTorch CNN.

## Dataset

- 292 training images, 97 validation images
- 256x256 RGB images from various locations and conditions
- Binary labels: tree vs. no tree

## Model Performance

**Baseline:** 65.74% → **Improved:** 74.07% (+8.33% accuracy with Early Stopping + Dropout)

Best Configuration:
- Early Stopping ✅
- Xavier Initialization ❌  
- LR Scheduler ❌
- Dropout (p=0.10) ✅

## Results

All 16 combinations of training improvements were tested:

| Early Stop | Init | LR Sched | Dropout | Val2 Acc |
|:----------:|:----:|:--------:|:-------:|---------:|
| ❌ | ❌ | ❌ | ❌ | 0.6574 |
| ❌ | ❌ | ❌ | ✅ | 0.6852 |
| ❌ | ❌ | ✅ | ❌ | 0.6574 |
| ❌ | ❌ | ✅ | ✅ | 0.7222 |
| ❌ | ✅ | ❌ | ❌ | 0.7407 |
| ❌ | ✅ | ❌ | ✅ | 0.7037 |
| ❌ | ✅ | ✅ | ❌ | 0.7222 |
| ❌ | ✅ | ✅ | ✅ | 0.6667 |
| ✅ | ❌ | ❌ | ❌ | 0.7222 |
| **✅** | **❌** | **❌** | **✅** | **0.7407** ⭐ |
| ✅ | ❌ | ✅ | ❌ | 0.7130 |
| ✅ | ❌ | ✅ | ✅ | 0.7222 |
| ✅ | ✅ | ❌ | ❌ | 0.6389 |
| ✅ | ✅ | ❌ | ✅ | 0.6389 |
| ✅ | ✅ | ✅ | ❌ | 0.6389 |
| ✅ | ✅ | ✅ | ✅ | 0.6481 |

## Key Findings

- **Early Stopping** prevented overfitting and improved generalization
- **Dropout** reduced train-validation gap  
- **LR Scheduler** caused overfitting to validation set
- **Xavier Init** had neutral/negative effect on this small network

## Usage

See `improvement.ipynb` for full training pipeline and model architecture
