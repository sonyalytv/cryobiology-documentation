# Cryobiology Project: Data Science Documentation & Codebase

This repository systematically documents and structures the technical solutions developed by our data science teams over several semesters for cell segmentation on microimages. 

The primary goal of this repository is to provide a reproducible methodological base, including comprehensive code, text documentation, and video instructions, allowing new participants to easily onboard and work with the used models.

## 📑 Table of Contents
1. [Project Overview](#project-overview)
2. [Repository Structure](#repository-structure)
3. [Data Annotation & Management](#data-annotation--management)
4. [Pipelines and Workflows](#pipelines-and-workflows)
   - [Data Preprocessing](#data-preprocessing)
   - [InstanSeg Model Pipeline](#instanseg-model-pipeline)
   - [3D Spheroid Processing](#3d-spheroid-processing)
5. [Getting Started](#getting-started)
6. [Documentation & Video Tutorials](#documentation--video-tutorials)

## 🔬 Project Overview
This project focuses on identifying, segmenting, and analyzing cells and spheroids in various microscopy modalities. 
* **Target Data:** Microimages in `.lsm`, `.tiff`, `.jpg`, and `.png` formats featuring L929 and SK-N-DZ cell lines, as well as Z-stacks of spheroids.
* **Core Models:** InstanSeg, YOLO11x, and StarDist.
* **Reference Datasets:** Custom annotated datasets and open-source datasets like LIVECell.

## 📂 Repository Structure
*(Note: This structure will be updated)*
```text
├── notebooks/
│   ├── 01_data_preprocessing_evaluation.ipynb
│   ├── 02_instanseg_custom_dataset_training.ipynb
│   └── 03_3d_spheroid_pipeline.ipynb (To be added)
├── scripts/
│   └── (Standalone Python scripts for YOLO11x, InstanSeg, StarDist)
├── docs/
│   └── (Architecture documentation, CVAT guidelines, specifications)
├── tutorials/
│   └── (Links to Ukrainian video instructions and text guides)
└── README.md
```

## 🗂 Data Annotation & Management
* **Annotation Tool:** Ground-truth annotations are created using the CVAT tool.
* **New Data Regulations:** The repository includes a defined protocol for transferring new images to students for annotation and creating custom training datasets.

## ⚙️ Pipelines and Workflows

### Data Preprocessing
The repository includes dedicated tools to clean and standardize microscopy images before feeding them into models.
* **Format Standardization:** Converts standard images (PNG/JPG) to TIFF formats, fixes bit-depth issues (e.g., `int8` to standard `uint8`), and ensures images have the required 3 RGB channels.
* **Image Resizing & Enhancement:** Includes functions to dynamically scale high-resolution images (e.g., towards 512x512) to fit memory constraints and apply contrast enhancement to make cellular structures more visible.

### InstanSeg Model Pipeline
We provide an end-to-end pipeline for utilizing the InstanSeg model for both brightfield and fluorescence microscopy.
* **Dataset Creation:** Scripts to compile `.pth` datasets from custom data (handling TXT/YOLO coordinates to 2D binary masks) or standard formats like LIVECell.
* **Training:** Supports transfer learning from pre-trained weights with customizable parameters (`num_epochs`, `target_segmentation`, `early_stopping`).
* **Testing & Exporting:** Features built-in testing scripts to calculate metrics and extract visual overlays, alongside utilities to export optimized PyTorch models via TorchScript for deployment.

### 3D Spheroid Processing
* **Z-Stack Processing:** The project includes scripts to process `.lsm` Z-stacks to build and analyze 3D models of cellular spheroids.

## 🚀 Getting Started
1. Clone the repository and navigate to the root directory.
2. Follow the installation scripts (`install.bat`, `runme.bat`) to set up the required environment. 
3. Core dependencies include `torch`, `torchvision`, `monai`, `instanseg`, `stardist`, and `imagecodecs`.
4. Open the `notebooks/` directory to begin running specific pipelines. 

## 📚 Documentation & Video Tutorials
Extensive documentation and step-by-step video tutorials (available in Ukrainian) are provided for every stage of the project. These cover:
* How to annotate images of various cell types and spheroids.
* Creating training and testing datasets.
* Running model training and testing experiments.
* The pipeline for processing and building 3D spheroid models.