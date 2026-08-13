# Caltech101 Image Classification Using HOG Features and SVM

## Project Overview

This project implements a classical computer vision pipeline for object
classification on the Caltech101 dataset using Histogram of Oriented
Gradients (HOG) feature extraction and Support Vector Machine (SVM)
classification.

The objective is to evaluate the performance of handcrafted image
features combined with machine learning methods for multi-class object
recognition.

Pipeline:

Caltech101 Dataset\
→ Image preprocessing\
→ Grayscale conversion\
→ Resize to 64×64\
→ HOG feature extraction\
→ Feature standardization\
→ SVM training\
→ GridSearchCV optimization\
→ Accuracy evaluation\
→ PCA visualization

## Dataset Information

Dataset: Caltech101 Object Categories

The Background_Google class was removed.

Final dataset:

-   Number of classes: 101
-   Number of images: 8677
-   Image size: 64×64
-   Image representation: Grayscale

## Image Preprocessing

Each image was:

1.  Converted from RGB to grayscale
2.  Resized to 64×64 pixels
3.  Converted into a numerical array

Result:

    Images shape:
    (8677, 64, 64)

## HOG Feature Extraction

Histogram of Oriented Gradients (HOG) was used to extract shape and edge
information.

Parameters:

    orientations = 9
    pixels_per_cell = (8,8)
    cells_per_block = (2,2)
    block_norm = L2-Hys

Results:

    HOG features shape:
    (8677, 1764)

    HOG images shape:
    (8677, 64, 64)

## Dataset Split

The dataset was divided using an 80/20 stratified split.

Training:

    (6941, 1764)

Testing:

    (1736, 1764)

## Feature Standardization

StandardScaler was applied before SVM training.

Results:

    Mean:
    -1.5032679904848832e-17

    Std:
    1.0000000000000004

## SVM Classification

SVM was used as the classifier.

GridSearchCV was applied to optimize:

    C:
    0.01, 0.1, 1

    Gamma:
    scale, 0.01, 0.1

    Kernel:
    linear, rbf

Total experiments:

    18 configurations × 3 folds = 54 fits

## Best SVM Model

The best model obtained was:

    SVC(C=0.01, kernel='linear')

Best parameters:

    C = 0.01
    Gamma = scale
    Kernel = linear

## Classification Results

Cross-validation accuracy:

    0.6569657577833156

    65.69%

Final test accuracy:

    0.6756912442396313

    67.57%

Number of support vectors:

    5665

## PCA Visualization

PCA was used to reduce the 1764-dimensional HOG space into three
dimensions.

Original dimension:

    1764

PCA output:

    (6941,3)

Explained variance:

    [
    0.05189807,
    0.04325328,
    0.02750935
    ]

Total explained variance:

    0.12266070302932025

    12.27%

## 3D Decision Region Visualization

A 3D PCA grid was created for visualization.

Grid points:

    3375

Converted back to original HOG space:

    (3375,1764)

The trained SVM successfully predicted all grid points and generated the
decision region visualization.

## Experimental Results Summary

  Parameter             Result
  ------------------- --------
  Images                  8677
  Classes                  101
  Image size             64×64
  Feature method           HOG
  Feature dimension       1764
  Training samples        6941
  Testing samples         1736
  Best kernel           Linear
  Best C                  0.01
  CV Accuracy           65.69%
  Test Accuracy         67.57%
  Support vectors         5665
  PCA dimensions             3
  PCA variance          12.27%

## Limitations

-   Background information affects some images.
-   Color information was removed.
-   Fixed image resolution may remove details.
-   Only limited HOG and SVM parameters were tested.

## Future Improvements

Possible improvements:

-   Background removal before feature extraction
-   Data augmentation
-   Combining HOG with LBP or color features
-   Larger SVM hyperparameter search
-   Comparison with CNN and transfer learning methods

## Conclusion

The implemented HOG + SVM approach provides a complete classical machine
learning solution for Caltech101 classification.

The final model achieved 67.57% test accuracy on 101 object categories
using only handcrafted features and SVM, demonstrating that traditional
computer vision techniques can still provide meaningful results for
object recognition tasks.
