# Predicting Band Gaps in 2D Materials using Machine Learning
This repository contains a Python implementation of using machine learning to predict band gaps in 2D materials as reported in this [paper](https://drive.google.com/file/d/1ESBwnPQyLl9UDGUV3vwUOMYf2XH0OY3v/view?usp=sharing).

## Installation
To install, press the green "Code" button, download, and extract the zip. 

## Usage
If [python](https://www.python.org/downloads/) is installed on the system with a run-time environment, navigate to extracted files. There, you will find ```edadev.ipynb``` and ```2dEgML.ipynb```. ```edadev.ipynb``` is used to clean and explore the dataset imported from [2dmatpedia](http://www.2dmatpedia.org/about). It then adds 136 compositional and elemental descriptors for machine learning using the [MAGPIE](https://www.nature.com/articles/npjcompumats201628) framework.

```2dEgML.ipynb``` is used to train and evaluate the performance of several machine learning models based on descriptors define in ```edadev.ipynb``` including: [LASSO](https://en.wikipedia.org/wiki/Lasso_(statistics)), [Random Forest](https://en.wikipedia.org/wiki/Random_forest), [Support Vector](https://en.wikipedia.org/wiki/Support_vector_machine#Regression), and [Gradient Boost](https://proceedings.neurips.cc/paper_files/paper/2000/file/8d9fc2308c8f28d2a7d2f6f48801c705-Paper.pdf) regression as well as an [artificial neural network](https://en.wikipedia.org/wiki/Neural_network_(machine_learning)). Exhaustive randomized and grid search hyperparameter
 tuning was performed for all regression models using [sklearn](https://scikit-learn.org/stable/) and a Bayesian optimization scheme across a parameter grid was used for the neural network using [TPOT](https://epistasislab.github.io/tpot/latest/). Feature value importance was extracted using [SHAP](https://shap.readthedocs.io/en/latest/example_notebooks/overviews/An%20introduction%20to%20explainable%20AI%20with%20Shapley%20values.html)

 *As some tasks are computationally expensive, we recommend using [Google Colab](https://colab.research.google.com/) with [GPU](https://saturncloud.io/blog/how-to-activate-gpu-computing-in-google-colab/) hardware accelerator at runtime. 

 ## Results
 The data set mostly consists of materials with band gaps between 0-1.89 eV as shown:
 
![image](https://github.com/user-attachments/assets/13893154-778a-4777-a4a7-a8e88deeb531)

After adding descriptors, we find some features have relatively high correlation with each other (area for future improvement) as shown:

![image](https://github.com/user-attachments/assets/8c822efc-992e-40ac-a9e5-d7062b00ce27)

After training all the models, find that gradient boost regression performs the best as highlighted below:

![image](https://github.com/user-attachments/assets/7e8138bb-5cd7-4f28-8521-c21806ffc606)

We find that melting temperature ($T_{m}$) and electronegativity ($\chi$) among the most important features in prediciting band gaps in 2D materials as shown:

![image](https://github.com/user-attachments/assets/e2d9e49a-40d7-45cb-969c-4e1e8a6e2e56)

## Future
We would like to optimize the number of features used to bring down model training times. We would also like to experiment with graph neural networks which use geometry-based descriptors, which have shown great promise in [materials discovery literature](https://www.nature.com/articles/s43246-022-00315-6), to increase predictive ability. 

