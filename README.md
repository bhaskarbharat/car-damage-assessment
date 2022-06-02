# car-damage-assessment

## Objective:
Automation of visual inspection as well as validation of damaged vehicles. 

## Motivation:
Car insurance processing involves physical inspection of damaged cars to reduce leakage of claims. It is a fairly long and time-consuming process. Hence, an automated system for visual inspection would help making this process efficient and reduce costs involved in the same.

## Scope:
The problem scope involves 3 stages:
- STAGE 1- Identifying damaged cars from the input images of cars.
- STAGE 2- Side of the car being damaged ( rear, front or side).
- STAGE 3- Intensity of car damage ( minor, moderate or severe).

## General Approach of Modeling

### Data Augmentation:
To deal with small size of development data at hand, various data augmentation techniques were employed to ensure that the models developed are robust enough.

### Transfer Learning Approach:
Transfer learning using SOTA models like VGG, Res-nets and Dense-nets were employed in the following forms:

#### Approach 1:
Using output from SOTA models ( before fully connected layers) as model features for fitting a simple regularized logistic regression ( implemented using final output layer in NN architecture). 

#### Approach 2:
Fine-tuning fully-connected layers of SOTA models.

### Class imbalance:
For stage 2 and stage 3 datasets, since class imbalance was observed, class weighted modelling approach was used in the above models.

### Performance Metrics:
Training data was split into train and validation datasets in the ratio 80% to 20%. Accuracy, Precision, Recall and Confusion matrices were the performance metrics on test data were used for final model selection.

## Main Results and Inferences

- The performances achieved using approach 2 using different architectures for any stage dataset are seen to be quite comparable to each other, particularly with respect to accuracy. 

- Approach 1 models were also explored. Improvement in model results  were not observed compared to final selected model using approach 2. However, the uplift in accuracy was not by a very high margin.

- Final model was selected based on better combinations of performance in terms of accuracy, precision and recall on test data.

- Misclassification of test images were further investigated using saliency maps. One of the potential reasons for stage 3 model misclassifications specifically was due to subjective labelling of intensity of damaged cars.

- Lastly,  web app was designed using streamlit for ease of exploration.
![streamlit app demo](https://drive.google.com/file/d/1x5h329jL8IR_8kv7pHuL0hG-4-uImLMM/view?usp=sharing)

## Future Work Recommendations for Model Improvement

- Better data collection strategies and creation of synthetic data for model development purposes for creation of robust models less prone to overfitting.

- For stage 2 and stage 3 modelling exercises, models did not seem to perform well on validation and test datasets. Following  actions are recommended for future to achieve better performance:

  - Stage 3 data consists of intensity of car damage. Upon further investigation of models and images being misclassified, it was observed that the model generally gets confused between moderate and severe damage of cars. The images being manually labeled, not much clarity is observed as to why an image is classified under moderate damage and not severe damage. Hence, for future work, 2 classes ( minor and severe) instead of 3, could be used  for better distinction between the classes. This is expected to enhance discriminatory power of models.

  - Due to resource limitations, not much fine tuning could be performed using state of the art models. Currently only Fully connected layers of SOTA models are fine tuned. However, for future use, in addition to fully connected layers, convolutional layers could also be fine-tuned .

  - Test accuracy could not be improved beyond 70-80% for stage 2 data and  65-70% for stage 3 data. This could also be indicative of distributional differences in the training and test data sets used.

- This problem statement is aimed towards making processing of claims undertaken by car  insurance industry more efficient.  Hence, to that extent, besides three stages of work defined under this scope, automated scanning of number plates for car authentication could also be integrated as part of future work.

- Currently SOTA models involving Convolutional Neural Networks are used for the task. Object detection techniques could be alternatively used for better detection and  detailed scanning of multiple damages observed in  damaged cars. 
