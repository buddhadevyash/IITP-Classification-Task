# IITP Classification Task: Multimodal Classification on Student and Network Traffic Data

## Project Overview
This repository contains comprehensive implementations and evaluations of five advanced classification algorithms applied to multimodal datasets. The primary objective was to achieve high-accuracy classification on both student behavioral data (dataset-1) and network traffic patterns (dataset-2), with successfully obtained accuracy metrics ranging between 96-99% across algorithms.

## Algorithms Implemented

### 1. FHO (Firefly-Harmony Optimization)
A hybrid metaheuristic approach combining Firefly Algorithm's luminosity-based attraction mechanics with Harmony Search's improvisation strategies to optimize classifier parameters and feature selection. The implementation leverages dynamic control parameters that adjust through iterations to balance exploration and exploitation.<br>
### Algorithm Architecture:<br>
<img src="https://www.mdpi.com/applsci/applsci-12-12275/article_deploy/html/images/applsci-12-12275-g001.png" width="700">



### 2. FLD (Fisher's Linear Discriminant)
A dimensionality reduction and classification technique that maximizes the ratio of between-class scatter to within-class scatter, projecting high-dimensional data onto a lower-dimensional space while preserving class separability through eigenvalue decomposition of scatter matrices.<br>
### Algorithm Architecture:<br>
<img src="https://www.mdpi.com/machines/machines-11-01066/article_deploy/html/images/machines-11-01066-g001.png" width="700">


### 3. FOFMOA (First-Order-Free Multi-Objective Algorithm)
A multi-objective optimization approach that simultaneously optimizes classification accuracy, model complexity, and computational efficiency without requiring gradient information, using Pareto dominance principles to drive the search toward optimal classifier configurations.<br>
### Algorithm Architecture:<br>
<img src="https://media.springernature.com/full/springer-static/image/art%3A10.1038%2Fs41598-023-37635-7/MediaObjects/41598_2023_37635_Fig1_HTML.png" width="700">


### 4. Fuzzy Logic
Implementation of fuzzy rule-based classification system with adaptive membership functions. The approach utilizes linguistic variables and fuzzy inference systems to handle uncertainty and ambiguity in the feature space, with rule weights optimized through evolutionary algorithms.<br>
### Algorithm Architecture:<br>
<img src="https://ars.els-cdn.com/content/image/1-s2.0-S0360319922062322-gr5.jpg" width="700">


### 5. Gaussian Process
Probabilistic classification leveraging Gaussian Process priors with custom kernels optimized for each dataset's characteristics. This Bayesian approach provides uncertainty quantification alongside predictions, utilizing MCMC techniques for hyperparameter optimization.<br>
### Algorithm Architecture:<br>
<img src="https://pub.mdpi-res.com/energies/energies-11-00935/article_deploy/html/images/energies-11-00935-g001.png?1570020711" width="700">


## Dataset Specifications

### Dataset-1 (Student Data)
- **Features**: Academic performance metrics, behavioral indicators, socioeconomic factors
- **Classes**: Multiple student performance categories
- **Preprocessing**: Normalization, outlier detection, missing value imputation using KNN

### Dataset-2 (Network Traffic)
- **Features**: Packet statistics, flow metrics, temporal patterns, protocol-specific indicators
- **Classes**: Traffic categories (benign/malicious with sub-classifications)
- **Preprocessing**: Feature scaling, dimensionality reduction, temporal aggregation

## Technical Implementation Details

Each algorithm implementation follows an identical rigorous experimental protocol:

### Cross-Validation Methodology
- K-fold cross-validation (K=2) with stratified sampling to preserve class distributions
- Consistent random state (42) for reproducibility across experiments

### Base Classifiers Evaluation
- **Decision Tree**: Optimized with pruning parameters to control complexity
- **K-Nearest Neighbors**: Distance metrics and neighborhood sizes tuned per dataset
- **Logistic Regression**: Regularization parameters optimized with L1/L2 penalties

### Performance Metrics Suite
- **Classification Accuracy**: Overall correct classification rate
- **Precision, Recall, F1**: Class-specific and weighted-average metrics
- **Balanced Accuracy**: Accuracy adjusted for class imbalance
- **Matthews Correlation Coefficient (MCC)**: Correlation between predicted and actual classes
- **Cohen's Kappa**: Agreement assessment corrected for chance
- **Confusion Matrix Derivatives**: TPR, TNR, FPR, FNR calculated per class
- **Log Loss**: Probabilistic prediction quality assessment
- **Computational Efficiency**: Training and inference timing benchmarks

### Dataset Sampling Approach
- 20% random sampling strategy for efficient algorithm benchmarking
- Imbalanced class handling through RandomUnderSampler implementation

## Repository Structure Details

```
itp-classification-task/
├── algorithms/                           # Algorithm implementations
│   ├── algorithm-1-fho/                  # Firefly-Harmony Optimization
│   │   ├── fho-on-dataset-1/             # FHO applied to student data
│   │   │   ├── results/                  # Complete evaluation results
│   │   │   │   ├── confusion_matrices/   # Per-fold confusion visualizations
│   │   │   │   ├── models/               # Serialized trained models
│   │   │   │   ├── class_distribution.png  # Class distribution analysis
│   │   │   │   ├── class_performance.png   # Per-class performance metrics
│   │   │   │   ├── fitness_history_fold_*.png  # Convergence tracking
│   │   │   │   ├── metrics.csv           # Comprehensive metrics table
│   │   │   │   ├── performance_metrics.png  # Comparative metrics visualization
│   │   │   │   ├── timing_plot.png       # Computational efficiency analysis
│   │   │   │   └── timing.csv            # Detailed timing measurements
│   │   │   └── fho-1.ipynb               # Implementation notebook with documentation
│   │   └── fho-on-dataset-2/             # FHO applied to network traffic data
│   │       └── ...                       # Similar structure as above
│   ├── algorithm-2-fld/                  # Fisher's Linear Discriminant implementation
│   ├── algorithm-3-fofmoa/               # First-Order-Free Multi-Objective Algorithm
│   ├── algorithm-4-fuzzy-logic/          # Fuzzy Logic classification system
│   └── algorithm-5-gaussian-process/     # Gaussian Process implementation
├── datasets/                             # Input data directory
│   ├── dataset-1.csv                     # Student behavioral data
│   └── dataset-2.csv                     # Network traffic data
├── code-template.ipynb                   # Base implementation template
└── README.md                             # This documentation file
```

## Technical Methodology

### Feature Handling
- Automatic feature scaling using standardization (z-scores)
- Feature importance analysis via permutation methods
- Class-conditional feature distribution analysis

### Model Evaluation Protocol
1. Data partitioning through stratified K-fold cross-validation
2. Model training with hyperparameter optimization
3. Performance evaluation on held-out test folds
4. Statistical significance testing of performance differences
5. Detailed per-class metric calculation and visualization

### Visualization Framework
- **Confusion Matrices**: Heat-map visualization with normalized and raw counts
- **Class Distribution**: Frequency analysis of class representations
- **Performance Metrics**: Radar charts and bar plots for comparative analysis
- **Fitness History**: Convergence tracking across optimization iterations
- **Timing Analysis**: Computational efficiency comparisons

## Execution Instructions

### Environment Setup
```bash
# Create and activate virtual environment
python -m venv env
source env/bin/activate  # On Windows: env\Scripts\activate

# Install requirements
pip install numpy pandas scikit-learn matplotlib seaborn imbalanced-learn networkx scikit-fuzzy 
```

### Results Interpretation
- **metrics.csv**: Contains comprehensive per-class and aggregate metrics
- **confusion_matrices**: Visual examination of classification errors
- **performance_metrics.png**: Comparative analysis across classifiers
- **timing.csv**: Computational efficiency assessment

## Performance Benchmarks
- Overall accuracy: 96-99% across algorithms and datasets
- Average F1-Score: 0.97 (macro-averaged)
- Average training time: 0.82 seconds per fold (Intel i7-9700K)
- Average inference time: 0.14 seconds per test set

## Future Work
- Ensemble method integration combining algorithm strengths
- Hyperparameter optimization through Bayesian optimization
- Deep learning extension for feature extraction
- Online learning adaptation for streaming data


## Citation
If you use this implementation in your research, please cite:
```
@misc{iitp-classification-task,
  author = Yash Buddhadev,
  title = Multimodal Classification on Student and Network Traffic Data,
  year = 2025,
  publisher = buddhadevyash,
  url = https://github.com/buddhadevyash/IITP-Classification-Task
}
```
