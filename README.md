# Road Damage Detection Using RF-DETR

## Overview

This project implements a road damage detection system using the RF-DETR (Region-based Fast DEtection TRansformer) model, specifically the RF-DETR Nano variant. The model is trained to detect and classify five types of road surface damages from images: Longitudinal Crack, Transverse Crack, Alligator Crack, Other Corruption, and Pothole.

The project is based on the Road Damage Detection 2022 (RDD2022) dataset and was developed as part of the Crackathon competition.

## Author

Akash A

## Model Architecture

- **Model**: RF-DETR Nano
- **Backbone**: ResNet with Feature Pyramid Network (FPN)
- **Parameters**: Approximately 30.16M
- **Training Features**: Exponential Moving Average (EMA), Mixed Precision, Gradient Checkpointing

## Dataset

- **Source**: Road Damage Detection 2022 (RDD2022)
- **Classes**:
  - 0: Longitudinal Crack
  - 1: Transverse Crack
  - 2: Alligator Crack
  - 3: Other Corruption
  - 4: Pothole
- **Format**: YOLO TXT for labels, converted to COCO JSON for training

## Training Details

- **Epochs**: 10
- **Learning Rate**: 0.0001
- **Batch Size**: 16 (effective 32 with gradient accumulation)
- **Optimizations**: Mixed precision, gradient checkpointing, EMA

## Results

Validation Metrics (EMA weights):

| Epoch | mAP@50:95 | mAP@50 |
|-------|-----------|--------|
| 0     | 0.208     | 0.429  |
| 3     | 0.264     | 0.528  |
| 6     | 0.284     | 0.557  |
| 9     | 0.294     | 0.574  |

The model outperformed baseline approaches using SAM3 and YOLO.

## Files

- `trainning.ipynb`: Jupyter notebook for training the model
- `submission.ipynb`: Jupyter notebook for generating predictions on test set
- `checkpoint_best_ema.pth`: Best model checkpoint
- `technical_report.tex`: Detailed technical report in LaTeX
- `submission/`: Folder containing prediction files for submission
- `baidu-rtdetr-model-overview.avif`: Model architecture diagram

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/road-damage-detection-rf-detr.git
   cd road-damage-detection-rf-detr
   ```

2. Install dependencies (assuming Python environment):
   ```bash
   pip install -r requirements.txt
   ```

   (Note: You may need to create `requirements.txt` based on the libraries used in the notebooks, such as PyTorch, torchvision, etc.)

## Usage

### Training

Run the `trainning.ipynb` notebook to train the model on the RDD2022 dataset.

### Inference

Run the `submission.ipynb` notebook to generate predictions on the test set. The predictions will be saved in the `submission/` folder.

## Submission

The `submission/` folder contains the prediction files in the required format for the competition. Compress this folder into `submission.zip` for submission.

## License

[Add license if applicable]

## Acknowledgments

- Crackathon competition organizers
- RDD2022 dataset providers
- RF-DETR model developers