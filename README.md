\# Solar Flare Forecasting from Solar Magnetograms



A machine learning research project for forecasting solar flares using Solar Dynamics Observatory (SDO) / Helioseismic and Magnetic Imager (HMI) line-of-sight (LOS) magnetogram images.



\## Overview



Solar flares are sudden releases of energy from the Sun that can affect space weather and, in severe cases, disrupt satellite communications, navigation systems, and other technological infrastructure.



This project investigates whether machine learning models can identify solar active regions that are likely to produce a solar flare within the next 24 hours.



The current work focuses on an image-based approach using solar magnetograms and follows the active-region split provided with the dataset to avoid mixing observations from the same active region across training, validation, and test sets.



\## Dataset



The primary dataset is based on the study by Boucheron et al. (2023) and contains preprocessed SDO/HMI line-of-sight magnetogram images.



\### Dataset characteristics



\* Image size: `224 × 224`

\* Image type: PNG

\* Observation region: within ±60° longitude/latitude

\* Forecast horizon: 24 hours

\* Flare threshold: C1.0

\* Approximately 950,000 magnetogram images

\* 1,570 solar active regions

\* Training, validation, and test sets are separated by active region



The dataset is used for binary flare forecasting:



\* `0` = no C1.0+ flare within the forecast window

\* `1` = C1.0+ flare within the forecast window



\## Experimental Design



The project is being developed progressively:



1\. Dataset inspection and exploratory analysis

2\. Image preprocessing and label verification

3\. Baseline machine learning experiments

4\. CNN-based image classification

5\. Evaluation using solar-flare forecasting metrics

6\. Temporal modeling using sequences of magnetograms

7\. Comparison with established baselines

8\. Analysis of model behavior and potential data leakage



The main goal is not simply to maximize accuracy, but to evaluate whether the models provide meaningful discrimination between flaring and non-flaring active regions.



\## Evaluation Metrics



Because flare forecasting is an imbalanced classification problem, accuracy alone is not sufficient.



The project considers:



\* \*\*TSS\*\* - True Skill Statistic

\* \*\*HSS\*\* - Heidke Skill Score

\* \*\*ROC-AUC\*\*

\* \*\*PR-AUC\*\*

\* \*\*Brier Score\*\*

\* \*\*Brier Skill Score\*\*

\* Confusion matrix and class-specific performance



Thresholds are selected using the validation set rather than the test set.



\## Baseline



The experiments include comparisons with previously reported approaches using the same active-region split where applicable.



A reduced-resolution linear SVM baseline and a frozen VGG16 transfer-learning baseline are used as reference points for the image-based experiments.



\## Current Direction



The current experimental direction is:



\*\*Magnetogram images → CNN → flare probability\*\*



The next stage investigates temporal information:



\*\*Magnetogram sequence → CNN feature extraction → temporal model → flare probability\*\*



This is motivated by the fact that solar active regions evolve over time, so a sequence of magnetograms may contain information that is not available from a single image.



\## Repository Structure



```text

Solar-flare-forecasting/

│

├── solar-flare-forecasting.ipynb

└── README.md

```



The main notebook contains the current experimental workflow, analysis, model training, and evaluation.



\## Reproducibility



The experiments use fixed random seeds where appropriate and preserve the official active-region separation between training, validation, and test data.



Special attention is given to preventing temporal and label leakage, particularly when constructing historical flare features and temporal sequences.



\## References



Boucheron, L. E., et al. (2023). Solar flare forecasting using machine learning and SDO/HMI magnetograms. \*Scientific Data\*.



Williams, T. D. (2025). Machine learning flare forecasting dataset and analysis. \*The Astrophysical Journal\*, 980, 102.



\## Author



\*\*Esayas Melaku\*\*



Data Scientist \& Machine Learning Engineer



GitHub: https://github.com/EsayasDS



\---



> This repository represents an ongoing research project. Results and methodology may change as additional experiments and validation are completed.



