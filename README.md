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
  //////////////////////////Hình chổ này
* **Double Resolution Framework:** To optimize the model for multi-scale feature learning, the dataset is structured into two resolution tiers:
  * **LH (High Resolution):** Contains the original, full-scale raw images captured directly by the UAV.
  * **LL (Low Resolution):** Contains sub-images cropped into $640 \times 640$ patches using a **sliding window technique**, preserving local small-target details for dense detection without overloading edge memory.
  //////////////////////////Hình chổ này

### Dataset Structure:

| Metric | Total Images | Train | Test | Validation |
| --- | --- | --- | --- | --- |
| **Number of Images Used** | 5,670 | 4,536 | 567 | 567 |
| **Percentage** | 100% | 80% | 10% | 10% |

## CODE

## MODELS

## EXPERIMENT

## VISUALIZATION RESEARCH



### 🚀 Enjoy your Air Quality System!
Thanks for checking out my project! If it helps you breathe easier (or just pass your graduation), my job here is done. Feel free to contribute, report issues, or give it a ⭐ if you liked it! 😊

## PAPER
