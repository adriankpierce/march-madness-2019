# March Madness 2019
Adrian Pierce and Lotan Weininger's submission for the Google Cloud & NCAA® Machine Learning Competition 2019 (https://www.kaggle.com/c/mens-machine-learning-competition-2019). This model placed 79th out of 868 teams (top 10%). 

See MEDIUM LINK for an article outlining their competition experience.

### Required Dependencies
* Tidyverse
* SciViews
* MLmetrics
* Raster
* Stringr

### Execution Instructions

Pre-requisites:
~~~~
Download data files from KAGGLE LINK and place into "march-madness-2019/data/"
~~~~

1. Calculate all required statistics:
~~~~
1-stats-averages.rmd
1-stats-sd.rmd
1-stats-tempo.rmd
1-stats-pom.rmd
1-stats-rating.rmd
1-stats-possession.rmd
~~~~

2. Conduct exploratory data analysis:
~~~~
2-eda.rmd
~~~~~~~~ 

3. Using the variables that best distinguish performant teams and non-performant teams, create training data:
~~~~
3-create-training-data.rmd
~~~~~~~~ 

4. Manually test various combinations of the final variables with logistic regression model (simulated competition results):
~~~~
4-model-selection.rmd
~~~~~~~~ 

5. Using the model with the lowest error, find the optimal "clamp" value
~~~~
5-clamp-selection.rmd
~~~~~~~~ 

6. Merge training data into the correct submission format:
~~~~
6-create-submission-data.RMD
~~~~~~~~ 

7. Create final model and write predictions
~~~~
7-create-final-model.Rmd
~~~~~~~~ 

8. Create list of unique teams in the 2019 tournament
~~~~
8-unique-teams.Rmd
~~~~~~~~ 

9. Manually label which teams are on "left side" of bracket vs "right side"
~~~~
see "output/unique-teams-LR.csv" for the 2019 file
~~~~~~~~ 

10. Modify final submission files: 
~~~~
9-submission-LR.rmd
~~~~~~~~ 

11. [Optional] Merge team names to final prediction file for readability 
~~~~
10-predictions-named.Rmd
~~~~~~~~ 

### File Details
In progress

### Visualization of Execution Process
In progress

### Predictor Details
In progress

### Final Model
In progress
