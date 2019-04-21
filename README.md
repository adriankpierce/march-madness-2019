# Machine Learning for March Madness 2019
Adrian Pierce and Lotan Weininger's submission for the Google Cloud & NCAA® Machine Learning Competition 2019 (https://www.kaggle.com/c/mens-machine-learning-competition-2019). This model placed 79th out of 868 teams (top 10%/Kaggle Bronze Medal). 

See MEDIUM LINK for an article outlining the details of this submission and competition experience.

### Required Dependencies
* Tidyverse
* SciViews
* MLmetrics
* Raster
* Stringr

### Execution Instructions

Pre-requisites:
~~~~
Download data files from https://www.kaggle.com/c/mens-machine-learning-competition-2019/data and place into "march-madness-2019/data"
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

4. Test different combinations of the final variables with the logistic regression model (simulated competition results):
~~~~
4-model-selection.rmd
~~~~~~~~ 

5. Using the model with the lowest error, find the optimal "clamp" value:
~~~~
5-clamp-selection.rmd
~~~~~~~~ 

6. Merge training data into the correct submission format:
~~~~
6-create-submission-data.RMD
~~~~~~~~ 

7. Create final model and write predictions:
~~~~
7-create-final-model.Rmd
~~~~~~~~ 

##### To guarentee 1 correct prediction, a few additional steps must be taken

8. Create list of unique teams in the 2019 tournament:
~~~~
8-unique-teams.Rmd
~~~~~~~~ 

9. Manually label which teams are on "left side" of bracket vs "right side":
~~~~
see "output/unique-teams-LR.csv" for the 2019 file
~~~~~~~~ 

10. Modify final submission files: 
~~~~
9-submission-LR.rmd
~~~~~~~~ 

##### Optional

11. Merge team names to final prediction file for readability:
~~~~
10-predictions-named.Rmd
~~~~~~~~ 

### Predictor Details

| ﻿Variable | Description                     | Team  |
|----------|---------------------------------|-------|
| X1       | Pomeroy Ranking                 | Team1 |
| X2       | Pomeroy Ranking                 | Team2 |
| X3       | Offensive Rating                | Team1 |
| X4       | Offensive Rating                | Team2 |
| X5       | Defensive Rating                | Team1 |
| X6       | Defensive Rating                | Team2 |
| X7       | Net Rating                      | Team1 |
| X8       | Net Rating                      | Team2 |
| X9       | Tempo                           | Team1 |
| X10      | Tempo                           | Team2 |
| X11      | Possession Time Per Game (sec.) | Team1 |
| X12      | Possession Time Per Game (sec.) | Team2 |
| X13      | Adjusted Pomeroy Ranking        | Team1 |
| X14      | Adjusted Pomeroy Ranking        | Team2 |

### Model Selection

| ﻿Model | Variable Composition                                    | Error   |
|-------|---------------------------------------------------------|---------|
| 1     | X1, X2, X3, X4, X5, X6, X7, X8, X9, X10                 | 0.55346 |
| 2     | X3, X4, X5, X6, X7, X8, X9, X10                         | 0.58481 |
| 3     | X1, X2, X3, X4, X5, X6, X7, X8                          | 0.55322 |
| 4     | X1, X2, X7, X8                                          | 0.55342 |
| 5     | (X1 - X2), X7, X8                                       | 0.55345 |
| 6     | (X1 - X2), (X7 - X8)                                    | 0.55291 |
| 7     | (X1 - X2), (X3 - X4), (X5 - X6), (X7  - X8)             | 0.55257 |
| 8     | (X1 - X2)^3, (X3 - X4)^3, (X5 - X6)^3, (X7 - X8)^3      | 0.58617 |
| 9     | (X1, X2, X3, X4, X5, X6, X7, X8)^2                      | 0.56862 |
| 10    | (X1 - X2), (X3 - X4), (X5 - X6)                         | 0.58856 |
| 11    | X3, X4, X5, X6                                          | 0.58472 |
| 12    | X1, X2, X3, X4, X5, X6, X7, X8, X11, X12                | 0.55551 |
| 13    | (X3 - X4), (X5 - X6), (X7 - X8)                         | 0.58462 |
| 14    | (X3 - X4), (X5 - X6), (X7 - X8), (X11 - X12)            | 0.58793 |
| 15    | (X3 - X4), (X5 - X6), (X7 - X8), X13, X14               | 0.54982 |
| 16    | (X3 - X4), (X5 - X6), (X7 - X8), (X13 - X14)            | 0.54966 |
| 17    | (X1 - X2), (X3 - X4), (X5 - X6), (X7 - X8), (X11 - X12) | 0.55587 |
| 18    | X1, X2, (X3 - X4), (X5 - X6), (X7 - X8)                 | 0.55329 |

Winning model: #16
