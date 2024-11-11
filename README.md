# Bayesian Neural Network with SWAG for Satellite Image Classification

## Task Overview

Implement a Bayesian Neural Network (BNN) that provides well-calibrated predictions for satellite image classification, detecting ambiguous samples using confidence levels. The model applies SWA-Gaussian (SWAG) for approximate inference and is calibrated to make reliable predictions, especially critical in high-stakes domains.

## Background

Bayesian Neural Networks improve upon traditional neural networks by incorporating uncertainty in predictions. This project uses a BNN with SWAG to classify land usage in 60x60 RGB satellite images, distinguishing well-defined and ambiguous samples. The model outputs either a class label or a “don’t know” response, with the goal of minimizing prediction costs and Expected Calibration Error (ECE).

## Task Breakdown

SWAG Implementation: Implement SWAG for both diagonal and full approximations to capture model uncertainty. \
Calibration: Ensure that the model’s predicted confidence aligns with its actual performance, measured using ECE. \
Prediction Cost Minimization: Output a class label or "don't know" with the goal of minimizing the mean prediction cost plus an ECE penalty.

### Data

Training Set: 1,800 labeled satellite images, each assigned a single land usage type. \
Validation Set: 20 images per class for well-defined types and 20 ambiguous images. \
Test Set: Contains images with multiple land usage types or unobserved features, like snow or clouds. \

Note: Data is not provided in this repository.

### Expected Calibration Error (ECE):

Measures alignment between prediction confidence and actual performance, calculated over 20 confidence bins.

### Prediction Cost:

Cost is based on the accuracy of predictions; predicting the wrong label or assigning a label to ambiguous samples incurs higher costs.

### Initialize SWAG: 

Review the SWAG method (Maddox et al., 2019) and start with implementing SWAG-Diagonal.

### Model Calibration:

Adjust post-hoc calibration methods, map predicted confidences accurately, and fine-tune SWAG hyperparameters.

### Template Constraints:

Implement your solution in solution.py without altering other handout files, focusing on the SWAGInference class and marked TODO sections.

## Checker:

Use Docker to run and check your solution. \
Run runner.sh (Linux/macOS) or docker build/docker run (Windows) to validate your solution.

Set EXTENDED_EVALUATION to True in solution.py to generate additional reliability diagrams and confidence plots.

## TODOS

- [x] Implement SWAG-Diagonal
- [x] Implement SWAG-Full
- [x] Implement calibration methods (Temperature scaling)
- [ ] Implement a model for Cloud and Snow classes
- [ ] Implement a custom learning rate scheduler that has enough exploration for a good SWAG approximation (Check calibration branch for ideas)
- [ ] Implement a advanced decission rule for the "don't know" class

## References

Maddox et al., 2019 (SWAG)
Izmailov et al., 2018 (SWA)
Guo et al., 2015 (ECE Calculation)