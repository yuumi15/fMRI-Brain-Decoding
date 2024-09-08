# Brain Decoding Using FMRI
<img align="right" width="100" height="100" src="https://github.com/user-attachments/assets/53aa999c-dd9c-416f-a23a-c68c3142dfa5" alt="image"> 

_This project represents the culmination of my learning during the Arabs in Neuroscience (AiN) 'Computational Neuroscience Summer School' (August 2024)._  

This project investigates how the brain processes sensory information by mapping the relationship between visual stimuli and neural responses. Using the fMRI dataset from Horikawa et al., we decode brain activity to predict the visual stimuli a person is perceiving. This figure explains the entire process: Subject views an Image > fMRI activity recorded > Brain activity data is processed by a decoding algorithm > The algorithm identifies the most likely category or pattern > We compare whether the predicted category matches the subject's perception.

![Paper Figure to upload](https://github.com/user-attachments/assets/53488778-6e33-46f8-8760-607eda016b18)


The dataset contains a large amount of fMRI data of images shown to subjects. Some images were presented multiple times to the subject while other images are shown once. However, different images often belong to the same category, as illustrated below (note: these images are not necessarily the ones in the dataset):

![fig 2 pics](https://github.com/user-attachments/assets/73251ba1-1e06-483c-a361-eaa12e3885df)

## Methodology & Results
We explored various ML techniques, including support vector machines (SVM), logistic regression, and linear regression with L1 (Lasso) and L2 (Ridge) regularization, to decode brain activity from fMRI data.

**I. Linear Regression with L1 and L2 Regularization:**
- We applied linear regression models with no regularization, L1, and L2 to predict brain activity (and compare betwetween them to stick with the best one).
- Cross-validation was used to assess the models, and the R2 score was calculated to evaluate performance across folds.

**II. Logistic Regression for Decoding:**

- Logistic regression was employed with No, L1, and L2 regularizations
- We compared test accuracies for models trained using each regularization type. Accuracies were visualized using a bar chart.

**III. Support Vector Machine (SVM) Decoding:**

- An SVM with a linear kernel was applied to decode brain activity across different regions of interest (ROIs), specifically focusing on the 'V3' region.
Cross-validation and test accuracy were computed for each fold, and the final model was trained on the entire training set to evaluate performance on the _unseen_ data.

**IV. Decoding Accuracy Across ROIs:**
- Logistic regression was used to assess decoding accuracy across different ROIs (V1, V2, V3, V4, LOC, FFA, and PPA) and image types ('similar', 'different', 'imagery').
- Cross-validation was performed on the training set, and the model was then fitted on the entire training data to predict test set accuracy.
- Results visualized below through bar plots to compare decoding accuracy across ROIs and image types.
![image](https://github.com/user-attachments/assets/59230fcb-ab25-48ce-abf8-dafea52cf27f)

### Implementation Details (for the sake of reproducibility)
- Numpy Random Generator Seed: 0
- Scikit Learn Random State: 7
- Test Ratio: 30%
- K-Fold: 5 folds (no stratifying, no shuffling)
- Applied Cross-Validation on the training data to tune the parameters and test using unseen Testing Data
## Conclusion
- V1 and V2 don't show accuracy for imagery data because these regions focus on basic visual features.
- Imagery involves higher-level processing, which engages regions like V4, LOC, FFA, and PPA. Therefore, V1 and V2 aren't involved in decoding mental imagery, leading to no accuracy in these areas.
- Overall, there is hierarchy of processing across ROIs, with primary regions excelling in basic image recognition higher regions handling more complex visual information.

### Team Members/ Contributors
- Nada O. Salah (Me)
- Nouran Khattab
- Sama Ehab, Salma Waleed, Yasmin Gebril, Khitam Aqel, Fatma Ragab

## References
- Arabs in Neuroscience (AiN) Computaional Neuroscience Summer School Project
- Kamitani, Yukiyasu, and Frank Tong. "Decoding the visual and subjective contents of the human brain." Nature neuroscience 8.5 (2005): 679-685.
- Horikawa, Tomoyasu, and Yukiyasu Kamitani. "Generic decoding of seen and imagined objects using hierarchical visual features." Nature communications 8.1 (2017): 1-15.
- Shen, Guohua, et al. "Deep image reconstruction from human brain activity." PLoS computational biology 15.1 (2019): e1006633.
