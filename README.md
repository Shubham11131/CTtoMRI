# CTtoMRI
A research-based project that studies different approaches for efficiently converting CT to MRI scans, comparing models such as UNIT, CycleGAN, AGGAN, and others.

# 🧐 CT-to-MRI Conversion Using CycleGAN

This project focuses on translating **CT (Computed Tomography)** images into **MRI (Magnetic Resonance Imaging)** images using a **CycleGAN** (Cycle-Consistent Generative Adversarial Network). The goal is to enable medical imaging synthesis without requiring paired datasets, helping to bridge the gap between fast-acquired CT scans and high-contrast MRI scans.

---

## 🚀 Project Overview

- **Objective:** Synthesize realistic MRI images from unpaired CT scans using a CycleGAN architecture.
- **Motivation:** MRI scans offer better soft tissue contrast but are slower and more expensive. By generating MRI-like images from CT, this project supports faster diagnosis and MRI-only workflows.
- **Approach:** Implement CycleGAN with two generators and two discriminators to learn the mapping between CT and MRI domains in an unsupervised manner.

---

## 🧐 Model Architecture

CycleGAN consists of:

- **Generator CT → MRI (G<sub>CT→MRI</sub>)**
- **Generator MRI → CT (G<sub>MRI→CT</sub>)**
- **Discriminator for MRI (D<sub>MRI</sub>)**
- **Discriminator for CT (D<sub>CT</sub>)**

### Loss Functions:

- **Adversarial Loss:** Ensures the generated images are indistinguishable from real ones.
- **Cycle Consistency Loss:** Guarantees that CT → MRI → CT and MRI → CT → MRI loops preserve structure.
- **Identity Loss (optional):** Preserves color/contrast during translation.

---

## 📁 Dataset

- **Type:** Unpaired CT and MRI datasets.
- **Format:** NIfTI or DICOM converted to PNG or JPEG slices.
- **Preprocessing:**
  - Resampling to uniform resolution.
  - Intensity normalization.
  - Cropping and resizing to consistent shape.

> Note: Datasets like IXI, CHAOS, or RIRE are commonly used.

---

## ⚙️ Technologies Used

- **Framework:** PyTorch
- **Libraries:** `torch`, `numpy`, `matplotlib`, `SimpleITK`, `NiBabel`
- **Visualization:** `matplotlib`, `TensorBoard`
- **Environment:** Python 3.8+, CUDA for GPU acceleration

---

## 📊 Evaluation Metrics

- **SSIM (Structural Similarity Index)**
- **PSNR (Peak Signal-to-Noise Ratio)**
- **Visual Turing Test (Expert-based)**
- **Qualitative comparison with actual MRI scans**

---

## 📦 Project Structure

```
CT-to-MRI-CycleGAN/
├── data/               # Preprocessed CT and MRI images
├── models/             # CycleGAN model definition
├── checkpoints/        # Trained weights
├── utils/              # Helper scripts for loading, visualization, metrics
├── train.py            # Training loop
├── test.py             # Inference script
├── README.md
```

---

## 🥪 How to Run

```bash
# Install dependencies
pip install -r requirements.txt

# Train CycleGAN
python train.py --dataset_path ./data --epochs 200 --batch_size 1

# Run inference
python test.py --input_dir ./data/CT --output_dir ./results/MRI
```

---

## 📌 Results

- Achieved visually realistic MRI outputs from CT images.
- SSIM scores indicate strong structural similarity.
- Qualitative results show high contrast and anatomical preservation.

---
