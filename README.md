# Wine_Quality_Prediction
Predicting the Quality of Red Wine using Machine Learning Algorithms for Regression Analysis, Data Visualizations and Data Analysis.

# Description
The two datasets are related to red and white variants of the Portuguese "Vinho Verde" wine. Due to privacy and logistic issues, only physicochemical (inputs) and sensory (the output) variables are available (e.g. there is no data about grape types, wine brand, wine selling price, etc.).

These datasets can be viewed as classification or regression tasks. The classes are ordered and not balanced (e.g. there are much more normal wines than excellent or poor ones).

What might be an interesting thing to do, is aside from using regression modelling, is to set an arbitrary cutoff for your dependent variable (wine quality) at e.g. 7 or higher getting classified as 'good/1' and the remainder as 'not good/0'. This allows you to practice with hyper parameter tuning on e.g. decision tree algorithms looking at the ROC curve and the AUC value. Without doing any kind of feature engineering or overfitting you should be able to get an AUC of .88 (without even using random forest algorithm)

KNIME is a great tool (GUI) that can be used for this. 1 - File Reader (for csv) to linear correlation node and to interactive histogram for basic EDA. 2- File Reader to 'Rule Engine Node' to turn the 10 point scale to dichtome variable (good wine and rest), the code to put in the rule engine is something like this:

q
u
a
l
i
t
y
 > 6.5 => "good"
TRUE => "bad" 3- Rule Engine Node output to input of Column Filter node to filter out your original 10point feature (this prevent leaking) 4- Column Filter Node output to input of Partitioning Node (your standard train/tes split, e.g. 75%/25%, choose 'random' or 'stratified') 5- Partitioning Node train data split output to input of Train data split to input Decision Tree Learner node and 6- Partitioning Node test data split output to input Decision Tree predictor Node 7- Decision Tree learner Node output to input Decision Tree Node input 8- Decision Tree output to input ROC Node.. (here you can evaluate your model base on AUC value)

