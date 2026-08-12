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
