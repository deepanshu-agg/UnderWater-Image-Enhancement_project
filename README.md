# UnderWater-Image-Enhancement Project

Welcome to the **UnderWater-Image-Enhancement** repository! This project explores both **classical** and **deep learning** methods to enhance underwater images, which often suffer from color distortion, low contrast, and hazy appearance. By applying the techniques in this repository, you can significantly improve the visibility and quality of underwater images for various applications such as marine biology, environmental monitoring, and underwater exploration.

---

## Table of Contents
1. [Project Overview](#project-overview)  
2. [Repository Structure](#repository-structure)  
3. [Dataset](#dataset)  
4. [Classical Approaches](#classical-approaches)  
5. [GAN-Based Approaches](#gan-based-approaches)  
6. [How to Run](#how-to-run)  
7. [Results](#results)  
8. [Potential Improvements & Future Work](#potential-improvements--future-work)  
9. [Contributing](#contributing)  
10. [License](#license)

---

## Project Overview

Underwater images are often challenging to work with because:
- **Light absorption and scattering** can cause hazy or blurry images.
- **Color distortion** (especially loss of red wavelengths).
- **Low contrast** that obscures important details.

### What This Repository Offers
1. **Classical Approaches**  
   - Color correction (channel compensation, white balancing)  
   - Histogram-based contrast enhancement (e.g., global histogram equalization)  
   - Fusion-based techniques (Averaging and PCA)

2. **Deep Learning Approaches**  
   - **GAN** (basic generative adversarial network)  
   - **DCGAN** (deep convolutional GAN)  
   - **CycleGAN** (image-to-image translation without requiring paired data)

By comparing these methods, you can decide which approach suits your application needs.

---

## Repository Structure

```
UnderWater-Image-Enhancement_project/
│
├── Data/
│   ├── raw-890/            # Contains raw underwater images
│   ├── reference-890/      # Contains reference/enhanced images
│   └── ... (any additional data folders)
│
├── Classical Approach/
│   ├── ...
│   └── (Notebooks or scripts for color correction, fusion, etc.)
│
├── GAN Approaches/
│   ├── DP_CycleGAN_300.ipynb
│   ├── DP_CycleGAN_Final_200.ipynb
│   ├── DP_DCGAN.ipynb
│   ├── DP_GAN.ipynb
│   └── ...
│
└── README.md  # You are here!
```

- **Data**: Place your raw underwater images in `raw-890` and corresponding reference images in `reference-890`.
- **Classical Approach**: Contains code for traditional image enhancement methods.
- **GAN Approaches**: Contains Jupyter notebooks implementing different GAN variants.

---

## Dataset

We use the [UIEB (Underwater Image Enhancement Benchmark)](https://li-chongyi.github.io/proj_benchmark.html) for training and evaluation.  

1. **Download** the dataset from the above link.  
2. **Place** the unzipped images into `UnderWater-Image-Enhancement_project/Data/`, separating them into `raw-890` (raw underwater images) and `reference-890` (corresponding reference or enhanced images).  

> **Tip**: Make sure the folder structure is consistent with the code in the notebooks (or adjust the paths in the code accordingly).

---

## Classical Approaches

1. **Color Correction**  
   - Compensates for red and blue channel attenuation relative to green.  
   - Performs white balancing (e.g., Gray World) to normalize the overall color distribution.

2. **Contrast Enhancement**  
   - Histogram Equalization (often applied in the Value channel of HSV space).  
   - Unsharp Masking to highlight edges and improve local details.

3. **Fusion-Based Methods**  
   - **Averaging Fusion**: Combines multiple enhanced versions of an image by simply averaging pixel values.  
   - **PCA Fusion**: Uses principal component analysis to blend two or more images (or image components), preserving the most significant information.

These classical methods are relatively fast and straightforward but may lack adaptability to very diverse underwater conditions.

---

## GAN-Based Approaches

### 1. Basic GAN
- A simple generator-discriminator setup.
- Can enhance images but may struggle with complex underwater features.

### 2. DCGAN
- Uses convolutional layers in both generator and discriminator.
- Generally produces better results than a basic GAN, but might still lose some structural details.

### 3. CycleGAN
- Learns mappings **both ways** (raw → enhanced and enhanced → raw) using **cycle-consistency**.
- Works well even when paired data is not perfectly aligned.
- Often yields the most visually appealing results among the GAN variants tested here.

---

## How to Run

1. **Clone or Download** this repository.  
2. **Open** the Jupyter notebooks of interest (e.g., `DP_CycleGAN_300.ipynb`) in the `GAN Approaches` or `Classical Approach` folder.  
3. **Check** that the dataset paths match your local directory structure (`Data/raw-890`, `Data/reference-890`).  
4. **Run** the cells in order:
   - Data loading and preprocessing
   - Model definition (for GANs) or function definitions (for classical methods)
   - Training or direct inference
   - Visualization of results

> **Note**: Some notebooks might already include pre-trained model checkpoints. If you want to train from scratch, ensure you have enough GPU memory (if using a GPU).

---

## Results

Various metrics can be used to evaluate the enhancements:

- **MSE (Mean Squared Error)**: Lower is better.  
- **PSNR (Peak Signal-to-Noise Ratio)**: Higher is better.  
- **SSIM (Structural Similarity)**: Closer to 1 is better.  
- **UIQM (Underwater Image Quality Measure)**: Higher indicates better underwater visual quality.  
- **FID (Fréchet Inception Distance)** for GAN outputs: Lower indicates more “realistic” generation.

### Observations
- **Classical Methods**:
  - Show notable improvements in color balance and contrast.
  - Quick to run, but less adaptable to different water conditions.
- **GAN Methods**:
  - **Basic GAN & DCGAN** can enhance images but may introduce artifacts or lose detail.
  - **CycleGAN** typically yields the best results, balancing color correction, contrast enhancement, and structural preservation.

---

## Potential Improvements & Future Work
- **Hybrid Methods**: Combine classical preprocessing with GAN-based training for improved stability and color accuracy.  
- **Advanced Architectures**: Incorporate attention mechanisms or multi-scale feature extraction in GANs to handle diverse underwater scenes.  
- **Real-Time Deployment**: Optimize or prune models for faster inference on embedded devices (e.g., ROVs/AUVs).

---

## Contributing
Contributions are welcome! Here’s how you can help:
1. **Fork** this repository.
2. **Create a new branch** for your changes.
3. **Open a pull request** describing your modifications and improvements.

Feel free to open an issue if you encounter bugs or have suggestions.

---

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

**Thank you for checking out the UnderWater-Image-Enhancement project!**  
If you have any questions or ideas, please open an issue or reach out. We hope you find these methods useful for your underwater image enhancement tasks.
