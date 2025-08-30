# Fracture-Detection-Without-Machine-Learning-My-Approach-
# Forearm Fracture Detection – Custom Image Processing Approach

This project is focused on **detecting forearm fractures in MRI images without using machine learning**.  
Instead of relying on pre-trained models, I designed my own image processing pipeline and algorithm to segment the bone, suppress tissues, and locate fractures.

---

## 🎯 Objective
The main goal was to **make the forearm bone more visible** in MRI scans, remove tissues, and automatically highlight fracture regions.  
I specifically aimed to **detect fractures without any machine learning**, using only classical image processing techniques.

---

## 🧪 Pipeline
The steps I applied sequentially:

1. **Normalization** – Standardizing intensity values.  
2. **CLAHE (Contrast Limited Adaptive Histogram Equalization)** – Enhancing bone contrast.  
3. **Adaptive Median Filtering** – Reducing noise.  
4. **Sharpening** – Emphasizing bone structures.  
5. **Brightness Reduction** – Suppressing unnecessary regions.  
6. **Convolution Filters** – Further enhancement of edges.  
7. **Range Filtering** – Isolating bone-like structures.  
8. **GMM (Gaussian Mixture Model) + LBP (Local Binary Patterns)** – Texture analysis.  
9. **Hough Transform + Edge Detection** – Extracting lines of the bone.  
10. **Extreme Point Detection** – Identifying discontinuities in bone structure.  

After these steps, the output images showed **the bone as white and the rest of the tissues as black**, making the fracture area stand out.

---

## 🧠 Custom Algorithm
To finalize the detection, I designed a custom rule-based algorithm:

- **Harris Corner Detection** was applied to the processed image.  
- Harris points accumulated at:
  - The elbow,  
  - The wrist,  
  - And at the fracture.  
- I then developed a counting algorithm:
  - **White points were counted**, and if too many accumulated in one area → mark with a **red box**.  
  - At first, this highlighted elbow, wrist, and fracture regions.  
  - To refine results, I added a rule:  
    - If the red boxes were located at the **sides** (elbow/wrist), discard them.  
    - If the boxes were located near the **center of the image** (assuming fracture is centered in MRI scans), keep them.  
- After adjustments, the algorithm successfully detected fractures.  
- In one test case, it achieved **100% accuracy** in locating the fracture.

---

## 📊 Results
- My pipeline and algorithm successfully detected fractures without using ML.  
- Final images highlight fracture regions with red boxes.  
- This method is **lightweight, explainable, and training-free** compared to ML-based methods.  

---

## 🚀 Future Work
- Extend the dataset with more MRI images.  
- Compare the performance of this method with ML-based approaches.  
- Further optimize rules for different fracture types.

---

## 📌 Summary
This project demonstrates that it is possible to **detect fractures in medical images without ML**, by carefully designing a preprocessing pipeline and a rule-based algorithm.  
It combines classical computer vision techniques with my own custom logic for robust results.

---
