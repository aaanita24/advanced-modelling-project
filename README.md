# advanced-modelling-project
This is a project that I created for the 'Advanced Modelling' course during my Masters in Computational Social Science at Universidad Carlos III de Madrid. 
This work investigates the economic and humanitarian consequences of ongoing armed conflicts through statistical modelling and machine learning techniques. Using a comprehensive dataset of 28 variables and over 50,000 observations, the analysis explores two central research questions through both regression and classification frameworks:

Regression: What economic and social factors drive food insecurity rates in countries affected by ongoing conflicts?
Classification: Can documented war profiteering be predicted from macroeconomic indicators?

The focus on ongoing rather than resolved conflicts was deliberate, aiming to produce a contemporary and socially relevant analysis of the measurable consequences of current wars. 

CLASSIFICATION MODEL:
The classification analysis began with a logistic regression and stepwise AIC selection, which identified GDP change, inflation rate, and the presence of water in the black market as the three most relevant predictors. LDA, QDA, and Naive Bayes were then applied, but all defaulted to predicting the majority class due to the dataset's imbalance (~70% "Yes"). K-NN was tested at three values of k with similar results. To address the imbalance, decision threshold adjustment was attempted, but no threshold produced meaningful class separation, leading to a cost-sensitive analysis with an asymmetric cost matrix (FN = 90, FP = 10) and resampling strategies (downsampling and oversampling), which improved class balance but raised expected cost. Finally, a decision tree, bagging, and random forest were applied on the balanced training set, but they all converging at around 50% balanced accuracy, no better than random chance. The overall conclusion is that macroeconomic indicators alone do not carry enough signal to predict documented war profiteering.

REGRESSION MODEL:
The regression analysis started with an OLS baseline, explaining approximately 54% of the variance in food insecurity rates, with poverty and unemployment emerging as the strongest predictors. Forward and bidirectional stepwise AIC selection, as well as cross-validated subset selection, all retained between 6 and 9 predictors while keeping R² stable at 54%. Ridge and Lasso penalized regressions were then applied, but both selected near-zero penalty parameters, producing results virtually identical to the OLS baseline. PCR and PLS reduced dimensionality but, again, yielded no improvement in predictive performance. The only model that behaved differently was a neural network, which improved R² to approximately 66% with lower MAE and RMSE, suggesting that the relationship between economic indicators and food insecurity is meaningfully non-linear.

How to Run:
- Clone this repository.
- Dowload the war_economic_impact_dataset.csv and place it in the project root directory.
- Open Advanced_Modelling_Final_Project.Rmd in RStudio.
- Install the required packages listed.
- Run the code and knit the document to HTML (output: html_document).
- 'set.seed(240603)' is used throughout the analysis to ensure reproducibility.

While this project is not perfect, it has been shared as a foundation for further exploration. The modelling pipeline could be extended by incorporating richer data sources, such as political instability indices, governance scores, or conflict intensity measures. This was a project that I enjoyed working on during my Master's, and I wanted to share as an example of an applied statistical exercise. It contributes to the possible uses of regression, classification, penalized methods, and neural networks in a structured, end-to-end modelling workflow on real-world data.
