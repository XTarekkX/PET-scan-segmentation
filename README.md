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

- **Image Format**: RGB (3 channels), resized to `(640, 640)`
- **Mask Format**: Binary (1 channel), resized to `(640, 640)`
- **Unique Mask Values**: `[0.0, 1.0]`

> ⚠️ The uniformity in image and mask shape is crucial to ensure compatibility with the model and consistency in training. Binary mask values help in clear and interpretable loss and metric calculations.

---

## ⚙️ Training Configuration

- **Learning Rate**: `1e-4`
- **Batch Size**: `8` (Kaggle GPU memory optimized)
- **Epochs**: `50`
- **Early Stop Patience**: `7`
- **LR Scheduler Patience**: `3`
- **Data Loaders**: `num_workers = 2`

---

## 🧪 Validation & Test Performance

| Metric        | Value    |
|---------------|----------|
| **Train Loss**    | `0.1309` |
| **Val Loss**      | `0.1820` |
| **Val IoU**       | `0.7789` |
| **Test Loss**     | `0.1702` |
| **Test IoU**      | `0.8025` |
| **Test Dice**     | `0.8905` |

> 🟢 Early stopping was triggered at **epoch 33**, ensuring optimal performance without overfitting.

---

## 🔄 Augmentation Strategy

Data augmentation was performed using the **Albumentations** library to enhance generalization:

- Geometric transforms: rotate, flip, elastic deformation, grid distortion
- Intensity transforms: brightness/contrast shift, blur
- All inputs were normalized to ImageNet mean and std.

---

## 📌 Future Improvements

- Integrate volumetric (3D) PET data for more spatial context
- Expand dataset diversity for better generalization
- Deploy as a web-based inference tool for clinicians

---

## 📁 Project Structure

