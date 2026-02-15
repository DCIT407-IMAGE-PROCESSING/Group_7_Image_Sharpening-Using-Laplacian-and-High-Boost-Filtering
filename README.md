 # Image Sharpening Using Laplacian and High-Boost Filtering

## Group Members
| # | Name                           | Student ID |
|---|--------------------------------|------------|
| 1 | Kofi Sarpei Lartey              | 11333137   |
| 2 | Theo Daniels                    | 11031981   |
| 3 | Nana Yentumey                   | 11339613   |
| 4 | Abdul Jabbar Eassiah Mahdi      | 11063705   |
| 5 | Prince Nana Kwesi Arthur        | 11078728   |
| 6 | Muiz Ajeola Bello               | 11068463   |
| 7 | Denis Bagresolzu Bayor          | 11252482   |
| 8 | Eshun Nhyira Abeeku              | 11013338   |


# Image Sharpening Using Laplacian and High-Boost Filtering

## Overview

This project investigates classical spatial-domain image sharpening techniques using **Laplacian sharpening** and **High-Boost filtering**. The objective is to evaluate how effectively each method enhances image quality and restores edge information in degraded images.

The evaluation employs two complementary approaches:

1. **Real-world Evaluation**: Sharp and blurry images from separate datasets are analyzed. Sharp images establish baseline sharpness ranges using Variance of Laplacian metrics, while sharpening techniques are applied exclusively to blurry images to assess their restoration capabilities.

2. **Controlled Augmentation**: Sharp images serve as ground truth references and are intentionally degraded using Gaussian blur to simulate defocus. Sharpening algorithms are then applied to these degraded images, and restoration performance is quantitatively evaluated against the original sharp images using multiple image quality metrics.

The goal is to determine which sharpening method more effectively recovers structural and edge information while preserving overall image fidelity across different degradation scenarios.

---

## Approach

### **Approach 1: Real-World Sharp vs Blurry Images**

This approach evaluates sharpening methods on naturally occurring blurry images:

1. **Baseline Establishment**  
   Sharp images are scored using Variance of Laplacian to establish reference sharpness ranges. No filtering is applied to these images—they serve purely as quality benchmarks.

2. **Blurry Image Restoration**  
   Sharpening techniques are applied exclusively to blurry images:
   - **Laplacian Sharpening**: Uses the second-order derivative (Laplacian operator) to detect and subtract edge information, enhancing high-frequency components.
   - **High-Boost Filtering**: Amplifies the original image while subtracting a Gaussian-smoothed version, with the boost factor (A=1.5) controlling enhancement strength.

3. **Performance Measurement**  
   Each method is evaluated using **Variance of Laplacian** as the sharpness metric. Improvement is measured by comparing the sharpness scores of filtered images against their original blurry state.

### **Approach 2: Controlled Augmentation Experiment**

This approach uses a controlled experimental framework for objective evaluation:

1. **Ground Truth Selection**  
   A dataset of sharp images serves as the reference standard for all comparisons.

2. **Controlled Degradation**  
   Gaussian blur (kernel size = 9×9) is applied to each sharp image to simulate defocus blur, creating a known degradation baseline.

3. **Sharpening Application**  
   Both restoration methods are applied to the blurred images:
   - **Laplacian Sharpening**: Enhances edges through Laplacian edge detection and subtraction
   - **High-Boost Filtering**: Enhances details by amplifying the difference between the original and its smoothed version

4. **Quantitative Evaluation**  
   Each restored image is compared to the original ground truth using multiple metrics:
   - **MSE (Mean Squared Error)** — measures pixel-wise reconstruction error (lower is better)
   - **PSNR (Peak Signal-to-Noise Ratio)** — quantifies reconstruction quality in dB (higher is better)
   - **SSIM (Structural Similarity Index)** — assesses perceptual structural fidelity on a scale of -1 to 1 (higher is better)
   - **Variance of Laplacian** — measures edge energy and sharpness

5. **Performance Comparison**  
   Improvement is measured relative to the blurred baseline. The method with higher average PSNR gain and SSIM values is considered more effective at restoring image quality.

### **Evaluation Strategy**

Both approaches provide complementary insights:
- **Approach 1** tests real-world applicability on naturally degraded images
- **Approach 2** provides controlled, reproducible measurements against known ground truth

This dual-methodology ensures that sharpening performance is assessed both objectively through quantitative metrics and practically through real-world image restoration scenarios, rather than relying solely on visual inspection.
