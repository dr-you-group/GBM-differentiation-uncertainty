# Deep ensemble differentiation of glioblastoma from solitary brain metastasis: Empirical estimation of uncertainty
Jupyter notebook files for training and testing deep ensembles for differentiating glioblastoma (GBM) from solitary brain metastasis (SBM) using MRI images. This model provides uncertainty and interpretability etimation. 

# Data 
Three different cohorts are used in the study: 
1. Internal cohort of 469 (GBM 300, SBM 169) patients was used for training and internal testing:   
  +  Training set (n=357; GBM 229, SBM 128)  
  + Validation set (n=41; GBM 26, SBM 15)  
  + Internal test set (n=71; GBM 45, SBM 26)  
2. External cohort of 143 (GBM 101, SBM 42) patients was used for external testing: 
+ External test set (n=143; GBM 101, SBM 42)
3. Out-of-distribution (OOD) dataset of 257 meningioma patients was used for OOD evaluation. 

# Data preprocessing
Python is used for MRI image preprocessing.  Two T2-weighted (T2) images and one postcontrast-T1 weighted image was concatenated to form 3 channel input.  
# Training and evaluation
Python is used for training and evaluation.   
## Model
We used ensemble ([Deep Ensembles](https://arxiv.org/pdf/1612.01474.pdf)) of five ImageNet pre-trained 2D convolutional neural network ([DenseNet121](https://arxiv.org/pdf/1608.06993.pdf)) to provide high quality preditive uncertainty estimates. 

## Evaluation
Model performace measured by AUROC, accuracy, sensitivity, specificity, precision, recall, F1 score, and weighted accuracy.   

# Uncertainty 
Model's predictive uncertainty is measured by entropy. 

# Interpretability
To provide prediction's interpretability, localization accuracy was measured by IoU (Intersection over Union) of prediction area and ground truth area.   
Prediction area was estimated by Grad-CAM as we can see where the model is focusing on when making prediction.  
Ground truth area was estimated by segmentation mask of the tumor.  

# Folder content
- `Preprocessing.ipynb` : Script for processing raw MRI images. Raw data in "nii.gz." format. 
- `TrainingTesting.ipynb` : Script for training and testing deep ensembles. Uncertainty and interpretability estimation codes are included. 
