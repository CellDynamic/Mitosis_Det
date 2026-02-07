# MitosisDet_RotUncertainty
The official codes of "Estimating rotation uncertainty for mitosis detection in phase-contrast microscopy images"

## Dataset
The method is evaluated on the C2C12-16 Dataset.
* **Source**: Official dataset from the CVPR2019 mitosis detection competition.
* **Modality**: Time-lapse phase-contrast microscopy images.
* **Characteristics**: The dataset captures C2C12 myoblast cells under four different culture conditions (Control, FGF2, BMP2, FGF2+BMP2). It presents significant challenges due to the dynamic morphological changes and the similarity between mitotic cells and non-mitotic interferences.

## Environment
This project is built on the PyTorch deep learning framework and implemented in Python.
### Hardware Configuration
The training, validation, and testing processes were conducted on a Linux-based server with the following specifications:
* **GPU**: 4 $\times$ NVIDIA TITAN RTX 3090 (24GB VRAM each)
* **CPU**: Intel Corporation Xeon E7 v4
* **RAM**: 128GB

## Code Structure
### fin_ellrotate.py
This module implements the **Elliptical Rotation Data Augmentation** and **Rotation Uncertainty Loss**.
* **Elliptical Rotation Data Augmentation**: Instead of standard rectangular rotation which introduces excessive background noise, we utilize an elliptical coordinate system to generate rotation-invariant samples. This ensures that the generated bounding boxes tightly enclose the mitotic cells regardless of their angle.
* **Rotation Uncertainty Loss**: During training, this module computes the discrepancy between the predicted orientation and the ground truth, optimizing the model to learn rotation-invariant features.

### crop_slide_test.py
* **Function**: Handles the high-resolution **Phase-Contrast Microscopy** sequences.
* **Mechanism**: Implements a **Sliding Window** strategy to crop raw image sequences into fixed-size patches (e.g., 320x320) with defined overlap, preparing them for the network input.

### detect.py
* **Function**: Performs inference on test patches using the trained weights.
* **Output**: Generates bounding boxes, class predictions, and confidence scores.

### result.py
* **Function**: Maps detection results from the patch level back to the original coordinate system.
* **Post-processing**: Applies Non-Maximum Suppression (NMS) to merge overlapping predictions and evaluates the model against Ground Truth using Precision, Recall, and F1-score.

  
## Detailed Code will be publicly available soon.
