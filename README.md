# Water Quality Prediction

### Problem Statement
This problem comes from comes from a 2015 Kaggle, details [here](https://www.kaggle.com/c/predict-west-nile-virus). .The official problem statement for this Kaggle is, “**Can we predict which water samples are Potable or Non-Potable?**.”

### Background
Access to safe drinking-water is essential to health, a basic human right and a component of effective policy for health protection. This is important as a health and development issue at a national, regional and local level. In some regions, it has been shown that investments in water supply and sanitation can yield a net economic benefit, since the reductions in adverse health effects and health care costs outweigh the costs of undertaking the interventions.

### Goal
Using advanced data modelling techniques, we want to predict if the water is potable or not. Ultimately, we want to find ways we can use these predictions to help a government or the WHO to select identify sources of potable water, or monitor their quality via data-driven decisions.

### Methods

The dataset is fairly small, around 3k entries. Potability seems to be the column one would like to predict using the remaining columns and is a binary variable, implying in a binary classification problem. Columns are numeric characteristic of the water sample whose behaviour we want to predict (in 1 for positive or 0 for negative) .
We also note that there are 4.4% null values in the dataset in pH and sulfate, most of the distributions seem to be relatively close to normal, and most of the features are highly uncorrelated, sulfate and solids are the most correlated (negative). No clear distinctions among classes can be found among the two classes. 

We replaced the missing data with the mean of each class, sub-sampled rows to match the number of examples per class, and scale each variable via a normalisation (0,1). Subsequently, we did a train-test-split of 80-20 in order to train the ML models including:  Logstic Regression, Decision Tree-based,  Random Forest,  Gradient Boosting, K-Nearest Neighbors and Support Vector Machines. We judged our model based on Accuracy, Precision, Recall and F1 score.

### Results 

Using Random Forest we were able to achieve an accuracy of 64.26% which is considered a good score (the score ranges from 0.5, the equivalent of random guessing, to 1.0, always correct). To help understand the model, we utilised Shapley Values, where it was revealed that sulfates was the most important variable in the classification.  Sulfates are naturally occurring substances that are found in minerals, soil, and rocks. Sulfate concentration in seawater is about 2,700 milligrams per liter (mg/L). It ranges from 3 to 30 mg/L in most freshwater supplies, although much higher concentrations (1000 mg/L) are found in some geographic locations.

### Recommendation

The Model could be improved via other Boosted or Bagged DT, or ensembled models. A different feature engineering, such as different scaling or ratios among the variables, could improve results as well.  We identified the most important features and some general trends between them that would help in the building of a second version of the model.

### Risks and Assumptions
The results of this study depend greatly on certain assumptions. The authors of the dataset have not explained how and where the data was collected, and the types of water bodies. Other factors such as depth, temperature, dissolved oxygen, pesticides, or toxic and hazardous substances have not been measured. Thus, deploying this model should be done after testing with laboratory results of real life scenarios.

### Data Dictionaries

About water_potability.csv (525.19 KiB) file:

**ppm: parts per million**  
**μg/L: microgram per litre**  
**mg/L: milligram per litre**

Column description:

```
1. ph: pH of 1. water (0 to 14).
2. Hardness: Capacity of water to precipitate soap in mg/L.
3. Solids: Total dissolved solids in ppm.
4. Chloramines: Amount of Chloramines in ppm.
5. Sulfate: Amount of Sulfates dissolved in mg/L.
6. Conductivity: Electrical conductivity of water in μS/cm.
7. Organic_carbon: Amount of organic carbon in ppm.
8. Trihalomethanes: Amount of Trihalomethanes in μg/L.
9. Turbidity: Measure of light emiting property of water in NTU.
10. Potability: Indicates if water is safe for human consumption. Potable -1 and Not potable -0
```
Source: [Kaggle dataset](https://www.kaggle.com/datasets/adityakadiwal/water-potability)
