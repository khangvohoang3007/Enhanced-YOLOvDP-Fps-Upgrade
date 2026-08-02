# ENHANCED-YOLOvDP: A LIGHTWEIGHT REAL-TIME DETECTION MODEL FOR UAV-BASED PLANT DISEASE MONITORING ON EDGE PLATFORMS

## OVERVIEW

This repository introduces an enhanced computing framework built upon the **YOLOvDP** architecture, originally proposed in the paper *"PDT: Uav Target Detection Dataset for Pests and Diseases Tree"* (Mingle Zhou, Rui Xing, Delong Han, Zhiyong Qi, Gang Li* - **ECCV 2024**). 

While the baseline YOLOvDP model provides robust accuracy, deploying it in practical scenarios introduces severe bottlenecks. This project bridges that gap by implementing targeted optimizations to address three critical challenges in modern aerial edge computing:

1. **Inference Speed Acceleration (FPS Upgrade):** Redesigning computational layers and optimizing the processing pipeline to eliminate latency, enabling real-time detection performance.
2. **Edge Device Deployability:** Optimizing the computational graph and applying model compression techniques (such as quantization and runtime conversion) to ensure smooth, high-speed execution directly on low-power edge hardware.
3. **High-Density Large Scale Detection:** Enhancing the feature extraction network to effectively detect dense, overlapping infected trees from high-resolution UAV forest imagery, preventing miss-detections in complex canopy structures.

## DATASET
This project utilizes the **PDT Dataset** obtained from the official repository: [ruixing123/pdt_cwc_yolo-dp](https://github.com/ruixing123/pdt_cwc_yolo-dp). 

The dataset consists of high-resolution aerial imagery captured by Unmanned Aerial Vehicles (UAVs) over a pine forest, specifically designed for evaluating object detection models in complex forestry scenarios.

### Dataset Characteristics & Specifications

* **Class Focus:** `Unhealthy` (Targeting infected or damaged pine trees within the forest canopy).

<p align="center">
  <img src="documents/target.png" width="500" alt="Class">
  <br>
</p>

* **Double Resolution Framework:** To optimize the model for multi-scale feature learning, the dataset is structured into two resolution tiers:
  * **LH (High Resolution):** Contains the original, full-scale raw images captured directly by the UAV.
  * **LL (Low Resolution):** Contains sub-images cropped into $640 \times 640$ patches using a **sliding window technique**, preserving local small-target details for dense detection without overloading edge memory.

<p align="center">
  <img src="documents/PDT_LL_LH.png" width="500" alt="Images Resolution">
  <br>
</p>

### Dataset Structure:

| Metric | Total Images | Train | Test | Validation |
| --- | --- | --- | --- | --- |
| **Number of Images Used** | 5,670 | 4,536 | 567 | 567 |
| **Percentage** | 100% | 80% | 10% | 10% |

## CODE

## MODEL ARCHITECTURE

<p align="center">
  <img src="documents/model.png" width="1000" alt="Model Structure">
  <br>
</p>

* **Backbone:** Replaced heavy **LSK modules** with standard **C3 blocks** to reduce parameters and computational burden.
* **Neck:** Removed the **P3 feature fusion branch** (upsampling, concatenation, and convolutions) to slash latency and boost FPS.

## EXPERIMENT

### 🧪 Experimental Setup & Results
* **Platform:** Kaggle Notebooks
* **GPU:** NVIDIA Tesla P100 (16GB VRAM)
* **Framework:** PyTorch >= 1.13.0, Python 3.10+
* * **Epochs:** 50
* **Batch Size:** 16 
* **Image Size:** 640

<p align="center">
  <img src="documents/model.png" width="500" alt="chart_training">
  <br>
</p>

### 📊 Performance Comparison

| Model | Precision (P) | Recall (R) | F1 Score | mAP@.5 | mAP@.5:.95 | Parameters | GFLOPs | FPS |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **YOLOvDP-Enhanced (Our)** | **0.887** | **0.831** | **0.858** | **0.901** | **0.603** | **6,099,030** | **12.8** | **116.28** |
| YOLOv5s | 0.877 | 0.815 | 0.845 | 0.882 | 0.605 | 7,012,822 | 15.8 | 81.97 |
| YOLOv5n | 0.873 | 0.808 | 0.839 | 0.880 | 0.588 | 1,760,518 | 4.1 | 80.00 |
| YOLOv8n | 0.8721 | 0.8455 | 0.8586 | 0.9247 | 0.6396 | 3,011,043 | 8.1942 | 78.465 |
| YOLOv11n | 0.875 | 0.8403 | 0.8573 | 0.9234 | 0.6394 | 2,590,035 | 6.4406 | 67.982 |
| YOLOv-DP | 0.862 | 0.794 | 0.827 | 0.863 | 0.571 | 4,993,774 | 11.1 | 51.02 |

## VISUALIZATION RESEARCH



### 🚀 Enjoy your Air Quality System!
Thanks for checking out my project! If it helps you breathe easier (or just pass your graduation), my job here is done. Feel free to contribute, report issues, or give it a ⭐ if you liked it! 😊

## PAPER
