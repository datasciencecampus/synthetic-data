# Generaing Data using Synthetic Minority Oversampling Technique (SMOTE)

Synthetic Minority Over Sampling – SMOTE – synthesises new minority instances between existing (real) minority instances. The technique was proposed in 2002 (Chawla, Bowyer, Hall, & Kegelmeyer, 2002) an is now an established method, with over 85 extensions of the basic method reported in specialised literature (Fernandez, Garcia, Herrera, & Chawla, 2018). It is available in several commercial and open source software packages.

## Can SMOTE be used to generate synthetic data? 
The technique was used on a variety of real world datasets to asses this. The approach was:

* Take an existing dataset with _n_ entries, make imbalanced (by replicating the dataset and assigning a target class) or generate a dataset with different features and an imbalance of 2:1 (this results in a generated dataset with the same number of samples at the original)
* Run SMOTE (4 variants) to generate new data samples (_n_ new samples)
* Isolate the generated datasamples
* Compare against original dataset – perform a correlation matrix on all the original data, all the generated data and then subtract the two correlation matrices. The resulting correlation matrix should be all zero for well-matched generated data.
* Use the Bhattacharyya distance to measure the similarity between the original and generated probability distributions

#### This was implemented in Python using the imbalanced-learn module. Data sets
1. Randomly generated data
2. ICS Adult Census data
3. LSOA Atlas Census data
4. SciKit Learn Cancer data

#### Quality of the generated data was assessed using:
* Pearson R correlation, intersect and Bhattacharyya distance between the original and generated distributions for each feature. These measure how closely the synthetic data for each individual feature matches the real data.
* Cross correlation matrix difference – subtraction of the cross correlation matrix of the real dataset and the generated dataset. If the two datasets are well matched this will be close to zero for the whole matrix.

The Jupyter notebook and data plots and summary stats of the technique are stored in different folders for different datasets.
