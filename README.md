# Housing Price Forecasting

The following table provides an overview of each econometric model and machine learning algorithm used to derive h-period ahead forecasts. Each model follows a single equation (S.E.) or multi-equation (M.E.) structure. Single equation models are univariate and appear autoregressive. Multi-equation models are multivariate and appear vector autoregressive. Each model is estimated on one-of-three different information sets of increasing size. Univariate models are built upon a single predictor. Small information set models are constructed from a set of 8 predictors. Large information set models depend upon the principal components extracted from 218 predictors. Principal component analysis is carried out using one-of-two methods. Pure factor augmented models extract seven principal components from the large information set prior to multi-equation model estimation. Blockwise factor augmentation extracts a single principal component from seven different data block partitions of the large information set. Each data block partition is meant to proxy a specific attribute of the overall macroeconomy. Lastly, each model is estimated using one-of-four different regularization methods (e.g. OLS, Ridge, Lasso, & Elastic Net). 

Optimal lag lengths and reasonable regularization parameters are identified using a grid search methodology that minimizes test set root mean squared error (RMSE). Walk foreword cross-validation is carried out using an expanding window of one period. The training set increments by one period. Thus, the most recent observation is added to the new training set, which is used to update the model weights after every period is observed. Each model is linearly defined. Therefore, multistep ahead forecasts are produced by foreword iteration of the linear model, which is done to avoid the estimation of a new model for each new forecast horizon. Forecast combinations are applied to the final set of optimally tuned predicted values. The purpose of forecast combining is to reduce prediction variation by linearly combining the predictions from multiple models. The predictions from all single equation models and multi-equation models are used to derive more accurate forecasts. 

The forecast accuracy of a proposed model is statistically compared to a baseline model using the one-sided Diebold & Mariano (1995) test for equal predictive accuracy. The null hypothesis indicates that two models produce forecast of comparable accuracy, while the alternative indicates that the proposed model outperforms the baseline model. In the table below the model mnemonics match the file paths that present the code. 

|          Mnemonic              |          Model Description (Estimation Method)        | Information Set Size | Model Structure |
|            :--                 |                :--                    |        :--:          |     :--:        |
|           (1) RW               |             Random Walk               |     Univariate       |     S.E.        |
|         (2) RW_Drift           |        Random Walk with Drift         |     Univariate       |     S.E.        |
|         (3) AR                 |           Autoregressive (OLS)        |     Univariate       |     S.E.        |
|         (4) ARMA               |  Autoregressive Moving Average (OLS)  |     Univariate       |     S.E.        |
|         (5) VAR                |      Vector Autoregressive (OLS)      |     Small            |     M.E.        |
|         (6) FAVAR              | Factor-Augmented Vector Autoregressive (OLS) | Large | M.E. |
| (7) BFAVAR | Blockwise Factor-Augmented Vector Autoregressive (OLS)| Large | M.E. |
| (8) AR\_Ridge |  Autoregressive (Ridge) |     Univariate       |     S.E.        |
| (9) AR\_Lasso | Autoregressive (Lasso) |     Univariate       |     S.E.        |
| (10) AR\_Elastic\_Net | Autoregressive (Elastic Net) |     Univariate       |     S.E.        |
| (11) VAR\_Ridge | Vector Autoregressive (Ridge) |     Small            |     M.E.        |
| (12) VAR\_Lasso | Vector Autoregressive (Lasso) | Small | M.E. |
| (13) VAR\_Elastic\_Net | Vector Autoregressive (Elastic Net) | Small | M.E. |
| (14) FAVAR\_Ridge | Factor-Augmented Vector Autoregressive (Ridge) | Large | M.E. |
| (15) FAVAR\_Lasso | Factor-Augmented Vector Autoregressive (Lasso) | Large | M.E. |
| (16) FAVAR\_Elastic\_Net | Factor-Augmented Vector Autoregressive (Elastic Net) | Large | M.E. |
| (17) BFAVAR\_Ridge | Blockwise Factor-Augmented Vector Autoregressive (Ridge) | Large | M.E. |
| (18) BFAVAR\_Lasso | Blockwise Factor-Augmented Vector Autoregressive (Lasso) | Large |  M.E. |
| (19) BFAVAR\_Elastic\_Net | Blockwise Factor-Augmented Vector Autoregressive (Elastic Net) | Large |  M.E. |
| (20) SE\_Median | Univariate (S.E.) Median Forecast Combination | | 
| (21) ME\_Median | Multivariate (M.E.) Median Forecast Combination | | 
| (22) SE\_Mean | Univariate (S.E.) Mean Forecast Combination | | 
| (23) ME\_Mean | Multivariate (M.E.) Mean Forecast Combination | |
| (24) SE\_Linear\_Regression | Univariate (S.E.) Forecast Combination (OLS) | |
| (25) ME\_Linear\_Regression | Multivariate (M.E.) Forecast Combination (OLS) | |
| (26) SE\_Ridge | Univariate (S.E.) Forecast Combination (Ridge) | |
| (27) ME\_Ridge | Multivariate (M.E.) Forecast Combination (Ridge) | |
| (28) SE\_Lasso | Univariate (S.E.) Forecast Combination (Lasso) | |
| (29) ME\_Lasso | Multivariate (M.E.) Forecast Combination (Lasso) | |
| (30) SE\_Elastic\_Net | Univariate (S.E.) Forecast Combination (Elastic Net) | |
| (31) ME\_Elastic\_Net | Multivariate (M.E.) Forecast Combination (Elastic Net) | |
