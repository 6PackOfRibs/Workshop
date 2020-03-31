**Response: Nieves et al.**
O3/31/2020

Nieves et al. use the random forest machine learning method to predict what value globally?  Describe in detail how random forest works.  What is a dasymetric population allocation? Which geospatial covariates proved to be the most important when predicting global values of where humans reside?

Nieves et al. uses the random forest method to predict population densities.
Random forests is a statistical method that is non-parametric and nonlinear, and is an 'ensemble method'. Ensemble methods use multiple learning algorithms. It takes individual decision trees that are considered weak learners and combines them into a strong learner. The random forest generates a number of unpruned decision trees using 'bagging'. Once a decision tree is grown, the one-third of the bagged training data that the tree was not grown upon remain and are known as the ‘out-of-bag’ data, which I assume is the RF's validation data.
Daysmetric population allocation is a way of allocating densities to grid cells asymmetrically using the population density weighting layer created by the RF model.
Geospatial covariates that were used were intensity of night-time lights, energy productivity of plants, topographic elevation and slope, climatic factors, type of land cover, and presence/absence of roads, water features, human settlements
and urban areas, and facilities such as health centres and schools. What they found was that it was surprisingly how much human population density correlated with environmental and physical factors and tended to be the most important when predicting global values.
