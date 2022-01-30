# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Arturo Polanco

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
I realized many of the algorithms used an ensemble to make predictions, since I accidentally run out of credits on AWS I had to implement my algorithm on Google Colab, a wonderful working environment. The step of generating a baseline model was very simple, just by assigning some values I was able to have a nice model. 

### What was the top ranked model that performed?
Best performing model was WeightedEnsemble_L3 with the score 0.598509. For this step I did not assign any hyper parameters. 
<img width="846" alt="first experiment" src="https://user-images.githubusercontent.com/16232171/151704821-b65a8bea-d132-4c64-b1e0-eb23839da7c5.png">


## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
I checked the distribution of my features, then I adjusted the type of the 'season' column to categorical, since that numerical value actually represents the four seasons (spring, summer, fall, winter) instead of a number. Finally, I took the date column, adjusted the type of variable and used it to include the year, month and day as features.  

### How much better did your model preform after adding additional features and why do you think that is?
The model actually performed a little bit worse, I assume having the complete date and also the year, month and day wasn't ideal. I decided to keep this appoach, just to see if it could improve in the phase of hyperparameter tunning.

<img width="846" alt="second experiment" src="https://user-images.githubusercontent.com/16232171/151704877-21cf3d3d-af08-4f7d-89ff-3a8190760055.png">


## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
Way better, I used a feed forward neural network and included the following hyperparmeters:
- Epochs: the number of times the algorithm makes one pass and learns from the full dataset. 
- Learning Rate: a number that determines how strong should the gradient of the algorithm affect the weights and biases of the network.
- Activation: an algorithm will be mostly fine only using a relu activation function, it's not linear and allows to create very complex decision boundaries.
- Layers: different number of neurons per layer.
- Dropout: parameter that helps avoid overfitting by randomly removing some neurons when they make predictions.

<img width="846" alt="third experiment" src="https://user-images.githubusercontent.com/16232171/151704905-543b10a3-8d97-4620-87ed-fd30e1868e96.png">



### If you were given more time with this dataset, where do you think you would spend more time?
Perhaps just adding more time to the training using neural networks, the dataset was big enough to create deep learning models and the performance was way better in comparisson to other traditional machine learning algorithms.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|600|default|default|0.598509|
|add_features|600|default|default|0.604720|
|hpo|1000|learning rate|layers|0.375633|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

<img width="653" alt="model score" src="https://user-images.githubusercontent.com/16232171/151704767-a7efe60d-b76e-4461-bac0-5f9ae696ab5e.png">


### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

<img width="653" alt="kaggle score" src="https://user-images.githubusercontent.com/16232171/151704748-900938ec-deb1-4a73-a0b5-1bfff069fc08.png">
## Summary
The previous line plots describe how the outstanding performance of hyperparameter tunning, according to this experiment, it's better to make effort in trying different configuration of deep learning algorithms and invest time so the algorithm can try different experiments.
