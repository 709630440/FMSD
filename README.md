# FMSD

**Forgery-aware Layer Masking and Multi-Artifact Subspace Decomposition for Generalizable Deepfake Detection**

FMSD is a generalizable deepfake detection framework designed to improve the robustness of deepfake detectors against unseen manipulation methods. The framework focuses on learning forgery-sensitive representations while preserving the semantic knowledge of pretrained vision models.

The project provides the implementation of FMSD together with a lightweight face image forgery detection demo.

---

## Overview

Deepfake detection models often achieve strong performance on known manipulation methods but suffer from significant performance degradation when encountering unseen forgery techniques.

FMSD addresses this problem from two perspectives:

* **Forgery-aware Layer Masking**
  Identifies layers that are more sensitive to forgery-related features and selectively updates them during training, reducing unnecessary modification of semantic representations.

* **Multi-Artifact Subspace Decomposition**
  Decomposes model parameters into semantic and forgery-related subspaces, enabling the detector to preserve general visual knowledge while learning discriminative manipulation artifacts.

The overall framework aims to improve cross-dataset and cross-manipulation generalization for deepfake detection.

---


## Framework

The overall architecture of FMSD is illustrated below.

<p align="center">
  <img src="framework.png" width="900">
</p>

FMSD consists of two main components: Forgery-aware Layer Masking and Multi-Artifact Subspace Decomposition.


## Demo

A simple face image forgery detection system is provided to demonstrate the inference process of FMSD.

The system takes a face image as input and outputs:

* Predicted class: **Real / Fake**
* Prediction confidence
* Visualization of the detection result

<p align="center">
  <img src="./FMSD.gif" width="800">
</p>

<p align="center">
  <b>FMSD Face Image Forgery Detection Demo</b>
</p>

---

## Features

* Generalizable deepfake detection
* CLIP-based visual backbone
* Forgery-aware layer selection
* Parameter-efficient model adaptation
* Multi-artifact feature modeling
* Support for cross-dataset evaluation
* Support for image-level deepfake detection
* Lightweight graphical detection demo

---

## Project Structure

```text
FMSD/
│
├── training/                 # Training and evaluation scripts
│   ├── train.py
│   ├── test.py
│   └── config/
│
├── preprocessing/            # Dataset preprocessing
│
├── detectors/                # FMSD detector implementation
│
├── demo/                     # Face forgery detection demo
│
├── docs/
│   └── assets/
│       └── FMSD.gif          # Demo GIF
│
├── requirements.txt
└── README.md
```

The exact directory structure may vary depending on the version of the repository.

---

## Environment

The project is implemented using **Python** and **PyTorch**.

Recommended environment:

```text
Python >= 3.8
PyTorch
torchvision
CUDA
OpenCV
NumPy
Pillow
tqdm
scikit-learn
```

Install the required dependencies with:

```bash
pip install -r requirements.txt
```

---

## Dataset Preparation

FMSD can be evaluated on commonly used deepfake detection datasets, including:

* FaceForensics++
* Celeb-DF
* DFDC
* DFDCP
* DeepFakeDetection

Please download the corresponding datasets from their official sources and configure the dataset paths according to the configuration files.

Example:

```yaml
dataset_root: /path/to/dataset
dataset_json_folder: /path/to/dataset_json
```

---

## Training

The detector can be trained using the provided training script.

Example:

```bash
python training/train.py \
    --detector_path ./training/config/detector/fmsd.yaml
```

Please modify the configuration file according to your dataset paths, training settings, and hardware environment.

---

## Evaluation

To evaluate a trained FMSD model:

```bash
python training/test.py \
    --detector_path ./training/config/detector/fmsd.yaml \
    --test_dataset "Celeb-DF-v2" \
    --weights_path ./weights/fmsd.pth
```

The evaluation script reports commonly used deepfake detection metrics such as:

* AUC
* Accuracy
* Average Precision
* EER

---

## Face Forgery Detection Demo

After downloading the trained model weights, the graphical demo can be used to detect whether an input face image is real or fake.

Example:

```bash
python demo/demo.py
```

Select an image through the interface and the system will display the predicted category together with the corresponding confidence score.

---

## Method

FMSD is designed to improve the generalization ability of pretrained vision models for deepfake detection.

### Forgery-aware Layer Masking

Instead of fine-tuning all layers of the pretrained model, FMSD evaluates the sensitivity of different layers to forgery-related information.

Layers containing stronger forgery-specific cues are selectively optimized, while other layers remain relatively stable to preserve semantic knowledge learned during large-scale pretraining.

### Multi-Artifact Subspace Decomposition

FMSD further decomposes model parameters into different feature subspaces.

The semantic subspace is kept relatively stable, while the forgery-related subspace is optimized for deepfake detection. This enables the detector to capture manipulation artifacts without severely damaging the general visual representation of the pretrained model.

---

## Results

FMSD is evaluated under cross-dataset settings to examine its ability to detect unseen manipulation methods.

The experiments demonstrate that the proposed method improves the generalization capability of deepfake detection models across multiple benchmark datasets.

Detailed experimental results will be provided in the corresponding paper.

---

## Pretrained Models

Pretrained model weights will be released after the paper and repository are fully organized.

The download link will be added here when available.

---

## Citation

If you find this project useful for your research, please consider citing our work:

```bibtex
@inproceedings{Zhang2026GeneralizableDD,
  title={Generalizable Deepfake Detection Based on Forgery-aware Layer Masking and Multi-artifact Subspace Decomposition},
  author={Xiang Zhang and Wenliang Weng and Daoyong Fu and Bei-Jing Chen and Zi-Qiang Li and Zi-Wen He and Zhangjie Fu},
  year={2026},
  url={https://api.semanticscholar.org/CorpusID:284488549}
}
```

The citation information will be updated after publication.

---

## Acknowledgements

This project is developed based on open-source deepfake detection frameworks and pretrained vision models.

We sincerely thank the authors and contributors of these projects for making their code and models publicly available.

---

## License

This repository is intended for **academic research and educational purposes only**.

Please follow the licenses of the corresponding datasets, pretrained models, and third-party libraries when using this project.

---

## Contact

If you have any questions about this project, please feel free to open an **Issue** in this repository.
