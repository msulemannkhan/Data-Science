### Links
Working of GBM with eg - https://www.kdnuggets.com/2018/07/intuitive-ensemble-learning-guide-gradient-boosting.html


GBM starts with a weak model for making predictions. The target of such a model is the desired output of the problem. After training such model, its residuals are calculated. If the residuals are not equal to zero, then another weak model is created to fix the weakness of the previous one. But the target of such new model will not be the desired outputs but the residuals of the previous model. That is if the desired output for a given sample is T, then the target of the first model is T. After training it, there might be a residual of R for such sample. The new model to be created will have its target set to R, not T. This is because the new model fills the gaps of the previous models.









