# DMZ Surveillance AI

A proof-of-concept computer vision pipeline for human activity recognition in surveillance footage using pose estimation and temporal sequence modeling.

## Overview

This project explores whether human activities can be classified from skeletal pose information extracted from video. Rather than operating directly on image pixels, the system uses YOLO pose tracking to detect human keypoints and then applies machine learning models to classify actions based on movement patterns over time.

The project was inspired by surveillance workflows in the Korean Demilitarized Zone (DMZ), where personnel may spend significant time reviewing footage manually. The goal was to investigate whether common actions could be automatically identified using lightweight computer vision techniques.

## Pipeline

```text
Input Video
    ↓
YOLO Pose Tracking
    ↓
Human Keypoint Extraction
    ↓
Pose Sequence Construction
    ↓
Feature Vector Generation
    ↓
Activity Classification
      ├── MLP Baseline
      └── LSTM
# Human Activity Recognition from Pose Sequences
```

## Dataset

The dataset consists of approximately 30+ manually collected video clips containing examples of human activities.

Example activities include:
- Marching
- Saluting
- Walking
- Standing

Videos were processed using YOLO pose tracking to generate skeletal keypoints for each frame. These keypoints were converted into fixed-length temporal sequences suitable for training machine learning models.

## Models

### Multi-Layer Perceptron (MLP)

A non-temporal baseline model that receives pose features and predicts the activity class without explicitly modeling motion over time.

**Purpose:**
- Establish a baseline for comparison
- Evaluate the value of temporal information

### Long Short-Term Memory Network (LSTM)

A recurrent neural network designed to model temporal dependencies in sequential data.

**Purpose:**
- Capture motion patterns across multiple frames
- Learn activity-specific movement dynamics

## Results

| Model | Validation F1 Score |
|-------|---------------------|
| MLP   | 0.49                |
| LSTM  | 0.53                |

The LSTM achieved a validation F1 score of 0.53 compared to 0.49 for the MLP baseline, representing an approximately 8% relative improvement.

These results suggest that incorporating temporal information provides modest benefits for activity recognition in this dataset.

## Key Technologies

- Python
- PyTorch
- YOLO Pose Tracking
- NumPy
- Scikit-Learn

## Limitations

This project should be viewed as a proof of concept rather than a production-ready system.

Current limitations include:
- Small dataset size
- Limited activity classes
- Restricted environmental diversity
- Potential sensitivity to camera angle and lighting conditions

Future work could include:
- Larger and more diverse datasets
- Additional activity classes
- Real-time deployment pipeline
- Lightweight edge-device inference
- More advanced temporal architectures

## What I Learned

This project provided hands-on experience with:
- Human pose estimation
- Sequence modeling with LSTMs
- Activity recognition pipelines
- Dataset preparation and evaluation
- Comparing temporal and non-temporal machine learning approaches

## Repository Structure

```
.
├── data/
├── notebooks/
├── models/
├── training/
├── evaluation/
├── videos/
└── README.md
```

## Disclaimer

This project was developed as an educational computer vision project and research exploration. It is not associated with or deployed by any military organization.
