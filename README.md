# Semantic-Segmentation-Cityscapes-Training/Finetuning
# UNet Model for Semantic Segmentation

This repository contains the implementation, training, and fine-tuning of a UNet model for semantic segmentation on the Cityscapes dataset after preprocessing. It includes:

- Training from scratch using a clean UNet implementation.
- Fine-tuning with class imbalance handling and augmentation strategies.
- Inference and evaluation pipeline.
- Reproducibility setup for Linux-based systems.

---

## 📁 Repository Structure
├── notebooks/ │ ├── Model_Training_UNet_From_scratch.ipynb │ ├── Fine_tuning_with_Weighted_CE_and_Augmentation.ipynb │ └── Fine_tuning_with_combined_CE_and_DICE_Loss.ipynb │  ├── report/ │ └── UNet_Model_Training_Report.pdf ├── requirements.txt └── README.md

---

##  Model Architecture

We use the **UNet** architecture, chosen for its ability to capture both spatial and contextual information through symmetric skip connections — making it ideal for dense pixel-wise prediction tasks.

---

##  Model Training & Fine-Tuning

###  Training from Scratch
Trained on preprocessed Cityscapes images using standard `CrossEntropyLoss`. Basic data augmentation was applied.

###  Fine-Tuning Strategies

1. **Weighted Cross Entropy + Occlusion Augmentation**
   - Class weights computed from label distribution.
   - Occlusion masks simulate real-world scenarios and improve robustness.

2. **Combined Cross Entropy + Dice Loss + Occlusion Augmentation**
   - Optimizes for both pixel-wise and region-wise accuracy.
   - Boosts performance on small objects and boundaries.

---



##  Inference Examples

Validation set predictions include:
- Input image
- Ground truth mask
- Predicted mask

See the report or notebooks for visualizations.

---

##  Preprocessing Pipeline

Preprocessing includes:
- Resizing all images and masks to **256×256**
- **Normalization** of RGB images to [0, 1]
- **Nearest-neighbor interpolation** for segmentation masks to preserve class IDs

Processed images are saved as `.npy`, and masks as `.png`.

---

## ⚙️ Computational Resources

- OS: Windows/ Kaggle 
- GPU: GPU P100
- Python: 3.8+
- Frameworks: PyTorch, NumPy, OpenCV, Pillow, WandB

---

##  Reproducibility

Follow these steps on a Linux machine:

```bash
# 1. Clone the repository
git clone https://github.com/your-username/unet-segmentation.git
cd unet-segmentation

# 2. Create and activate a virtual environment
python3 -m venv venv
source venv/bin/activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Preprocess the data
python preprocessing/Image_segmentation_Preprocessing (1).py

# 5. Launch training notebooks
jupyter notebook notebooks/Model_Training_UNet_From_scratch.ipynb
jupyter notebook notebooks/Fine_tuning_with_Weighted_CE_and_Augmentation.ipynb
jupyter notebook notebooks/Fine_tuning_with_combined_CE_and_DICE_Loss.ipynb
