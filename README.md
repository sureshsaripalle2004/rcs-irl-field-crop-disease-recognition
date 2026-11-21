# RCS-IRL: Reliability-Guided Context-Suppressed Feature Fusion for Multi-Label Field Crop Disease Recognition

## Overview

This repository contains the implementation and experimental results of RCS-IRL, a reliability-guided feature fusion framework for multi-label field crop disease recognition.

The proposed approach combines global image representations and annotation-guided region-of-interest (ROI) features. It incorporates context suppression, reliability estimation, feature fusion and prediction-stability regularization to investigate robust crop disease recognition under feature perturbations.

## Research Objectives

- Investigate global and local visual information for field crop disease recognition.
- Develop context-suppressed feature fusion.
- Incorporate a reliability estimation mechanism.
- Evaluate prediction stability under synthetic feature perturbations.
- Compare the proposed framework against feature-level baselines and ablation variants.

## Dataset

This study uses the FieldPlant dataset published by bloox2 on Kaggle.

**Dataset:** https://www.kaggle.com/datasets/bloox2/fieldplant

The dataset contains field crop images with bounding-box annotations.

The experimental preprocessing pipeline includes image-level metadata construction, duplicate-image auditing, conflicting annotation handling, multi-label preparation and iterative stratified splitting.

The primary benchmark contains 4,816 images and 19 disease or healthy-condition labels.

### Dataset Splits

| Split | Images |
|---|---:|
| Training | 3,369 |
| Validation | 719 |
| Testing | 728 |
| Total | 4,816 |

The original dataset is not redistributed in this repository. Users should obtain it from the original Kaggle source and follow its applicable licence terms.

## Proposed Framework

RCS-IRL investigates the integration of:

1. Global feature extraction using ResNet-18.
2. Annotation-guided ROI feature extraction.
3. Context suppression between global and ROI representations.
4. Reliability estimation for contextual feature weighting.
5. Feature fusion and multi-label classification.
6. Prediction-stability regularization under feature perturbations.

The implementation uses a two-stage training procedure consisting of a pilot ResNet-18 stage and a subsequent feature-level RCS-IRL stage.

## Experimental Results

Final held-out test-set results using a fixed classification threshold of 0.5:

| Metric | Result |
|---|---:|
| Macro Precision | 0.5401 |
| Macro Recall | 0.7740 |
| Macro F1 | 0.6022 |
| Micro Precision | 0.6160 |
| Micro Recall | 0.8979 |
| Micro F1 | 0.7307 |
| Mean Average Precision | 0.6856 |
| Macro ROC-AUC | 0.9815 |
| Hamming Loss | 0.0361 |

These values represent the recorded experiment results for the specified dataset split and implementation.

## Repository Structure

```text
rcs-irl-field-crop-disease-recognition/
│
├── README.md
├── RCS_IRL_Complete_Implementation.ipynb
│
└── results/
    ├── figures/
    │   ├── fig1_per_class_performance.png
    │   ├── fig2_baseline_comparison.png
    │   ├── fig3_ablation_study.png
    │   ├── fig4_robustness_analysis.png
    │   ├── fig5_feature_training_curves.png
    │   ├── fig6_pilot_training_curves.png
    │   ├── fig7_test_multilabel_confusion_matrices.png
    │   ├── fig8_class_distribution_by_split.png
    │   └── fig9_validation_leaf_roi_examples.png
    │
    └── tables/
        ├── final_test_metrics.csv
        ├── final_test_per_class_results.csv
        ├── baseline_comparison_summary.csv
        ├── ablation_summary.csv
        ├── repeated_seed_robustness_summary.csv
        └── other experimental result tables
```

## Implementation

The primary implementation is provided as a Google Colab notebook:

`RCS_IRL_Complete_Implementation.ipynb`

The notebook includes dataset loading, preprocessing, model implementation, training, validation, testing, baseline comparisons, ablation studies, robustness experiments and visualization.

The experiments were executed using a CPU-compatible configuration.

## Important Experimental Limitations

- The experiments use a single dataset source.
- The held-out test split does not establish generalization to unseen farms or geographic domains.
- Feature perturbation experiments are synthetic and should not be interpreted as direct real-world environmental robustness tests.
- Baseline and ablation comparisons are feature-level experiments.
- The implementation is a two-stage feature-learning pipeline rather than a fully end-to-end model.
- No claim of superiority over external published state-of-the-art methods is made.

## Reproducibility

The notebook and result tables are provided to support inspection and reproduction of the reported experiments.

Reproduction requires access to the original FieldPlant dataset, compatible Python dependencies and the documented experimental configuration.

## Citation

If you use this implementation, please cite the associated research paper after its publication.

## Author

**S. Suresh**

M.Tech Researcher  
Department of Information Technology / AI and Robotics  
Chaitanya Bharathi Institute of Technology (CBIT), Hyderabad, India

## Dataset Reference

FieldPlant dataset by bloox2:

https://www.kaggle.com/datasets/bloox2/fieldplant
