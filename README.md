# 🧠 2D PET Scan Tumor Segmentation

This project focuses on **semantic segmentation of tumors** from 2D PET scan slices using a **U-Net** architecture with a **ResNet34 encoder pretrained on ImageNet**.

The goal is to accurately identify tumor regions from medical images using deep learning, enabling potential clinical applications in oncology diagnostics and treatment planning.

---

## 🚀 Highlights

- ✅ **Backbone**: ResNet34 (ImageNet weights)
- 📐 **Input Shape**: 640 × 640 (resized)
- 📊 **Binary Segmentation**: Mask values only 0 (background) and 1 (tumor)
- 🔁 **Early Stopping**: Training stopped at epoch 33 to avoid overfitting
- 📈 **Best Performance**:
  - **IoU**: `0.8025`
  - **Dice Coefficient**: `0.8905`
  - **Test Loss**: `0.1702`

---

## 🖼️ Data & Preprocessing

- **Number of Images**: `1067`
- **Number of Masks**: `1067`
- **Image Format**: RGB (3 channels), resized to `(640, 640)`
- **Mask Format**: Binary (1 channel), resized to `(640, 640)`
- **Unique Mask Values**: `[0.0, 1.0]`

> ⚠️ The uniformity in image and mask shape is crucial to ensure compatibility with the model and consistency in training. Binary mask values help in clear and interpretable loss and metric calculations.

---

## 📂 Dataset Information

The dataset used in this project is **manually collected from a hospital in Egypt** and represents **real-life clinical PET scan data**. It was anonymized and organized for academic research purposes.

> ❗ **Disclaimer**: This dataset is intended **strictly for academic and research purposes**. **Any misuse, redistribution, or commercial application is not permitted and is not the responsibility of the authors.**

### Dataset Structure
```python
base_path = '/kaggle/input/pet-segmentation-dataset'

images_path = os.path.join(base_path, 'image')
masks_path  = os.path.join(base_path, 'mask')
