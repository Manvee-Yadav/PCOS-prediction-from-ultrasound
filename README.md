# PCOS Detection Using Ultrasound Images (Ultrasound Modality)

This project focuses on **Polycystic Ovary Syndrome (PCOS) detection using ultrasound imaging**. A deep learning–based pipeline was developed to analyze ovarian morphology from ultrasound scans and classify images as **PCOS** or **Normal**, following radiologist-approved clinical criteria.

---

## 🎯 Objectives

* Collect and annotate ultrasound images for PCOS diagnosis.
* Perform robust image preprocessing to handle noise and variability in ultrasound scans.
* Prevent data leakage using patient-level dataset splitting.
* Train and evaluate deep learning models using transfer learning.
* Compare CNN architectures for reliable PCOS classification.

---

## 🖼️ Ultrasound Image Collection & Annotation

* Ultrasound images were collected from radiology departments using **transabdominal** and **transvaginal probes**.
* Each image was annotated and verified by a radiologist.

### Annotation Details

* Identification of **left and right ovaries**.
* Marking PCOS characteristics:

  * Presence of **12 or more follicles**, or
  * **Increased ovarian volume**.
* Each image was assigned a **binary class label**: `PCOS` or `Normal`.

---

## 🔀 Dataset Splitting Strategy

* **Patient-level image splitting** was applied using unique patient identifiers.
* All scans from the same patient were kept within a single dataset split to avoid data leakage.
* Dataset was divided into:

  * Training Set
  * Validation Set
  * Test Set

---

## ⚙️ Ultrasound Image Preprocessing Pipeline

Due to noise, contrast variation, and anatomical differences in ultrasound images, a structured preprocessing workflow was applied.

### 1️⃣ Image Resizing & Standardization

* All images converted to **RGB format**.
* Resized to **224 × 224 pixels** to match CNN input requirements.
* Ensured compatibility with models such as VGG16, MobileNetV2, DenseNet121, and ResNet50.
* Reduced variations caused by different ultrasound machines and acquisition settings.

### 2️⃣ Noise Removal & Contrast Enhancement

* Applied **Gaussian filtering** to reduce speckle noise while preserving structural edges.
* Enhanced image contrast to highlight follicles and ovarian boundaries.

### 3️⃣ Otsu Thresholding & Mask Generation

* Applied **Otsu thresholding** to segment ovarian regions.
* Generated binary masks to remove irrelevant background and probe artifacts.
* Focused model attention on clinically important ovarian structures.

### 4️⃣ ORB Keypoint Extraction

* Extracted **ORB (Oriented FAST and Rotated BRIEF) keypoints** to capture:

  * Follicle edges
  * Texture variations
  * Structural irregularities

### 5️⃣ Data Augmentation

* Applied only to the **training set** to prevent biased evaluation.
* Techniques used:

  * Rotation
  * Flipping
  * Zooming
  * Cropping
  * Brightness and contrast variations

### 6️⃣ Patient-Level Stratification

* Ensured all images from a single patient were present in only one dataset split.
* Prevented information leakage and ensured reliable performance evaluation.

---

## 🤖 Deep Learning Models

A total of **1,987 ultrasound images** were used to train CNN-based models with transfer learning.

### 🔹 VGG16

* Used as a baseline CNN model.
* Fine-tuned deeper layers to capture PCOS-specific features such as peripheral follicles and dense ovarian tissue.

### 🔹 MobileNetV2

* Lightweight and computationally efficient architecture.
* Effectively captured subtle follicular clustering patterns.
* Achieved fast convergence and strong performance.

### 🔹 DenseNet121

* Dense connectivity preserved low-level and high-level features.
* Improved detection of subtle texture and follicular variations.
* Performed well in distinguishing PCOS from normal ovaries.

### 🔹 ResNet50

* Utilized residual connections for deep feature learning.
* Required careful fine-tuning due to ultrasound noise and inter-patient variability.
* Learned structural patterns associated with PCOS, though with slower convergence.

---

## 🏆 Key Highlights

* Radiologist-verified annotations ensured clinical reliability.
* Patient-level splitting eliminated data leakage.
* Advanced preprocessing improved feature learning.
* Transfer learning enabled effective PCOS detection from ultrasound images.

---

## 🛠️ Tech Stack

* **Programming Language:** Python
* **Libraries:** OpenCV, NumPy, TensorFlow / Keras, Scikit-learn, Matplotlib
* **Tools:** Jupyter Notebook, VS Code

---


⭐ If you find this project useful, consider starring the repository!
