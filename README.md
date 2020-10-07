# Detecting Ransomware Payments with Bitcoin Data
This repository contains the files related to a project with the goal of using publicly available data on Bitcoin transactions to train a model to detect ransomware payments. The idea of the project was taken from [this paper](https://arxiv.org/abs/1906.07852) by Cuneyt Gurcan Akcora, Yitao Li, Yulia R. Gel and Murat Kantarcioglu.

### data
The dataset for this project can be accessed at the [University of California Irvine Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/BitcoinHeistRansomwareAddressDataset). Each instance in the dataset represents a Bitcoin address over a 24 hour period. The dataset contains 2,916,697 instances, and includes all Bitcoin addresses receiving more than 0.3 Bitcoin in each 24 hour period from January 2009 to December 2018. Each instance is labelled as being associated to a certain type of ransomware or is labelled "white" meaning that it is not known to be associated with ransomware. These labels come from three studies at [Montreal](https://arxiv.org/pdf/1804.01341.pdf), [Princeton](https://nyuscholars.nyu.edu/en/publications/tracking-ransomware-end-to-end), and [Padua](https://arxiv.org/pdf/1804.04080.pdf), and only include ransomware addresses that have been reported. Features are engineered from the network of transaction feeding into the corresponding address over the corresponding 24 hour period. For more details on the features please see the slide deck below or the paper by Akcora et al.

---
## Folders
### notebooks
This folder contains the code for the project. Modelling was broken down into two rounds:

- Firstly, I trained a model to detect any addresses associated with ransomware payments. For this I created a Spark cluster using the EMT feature on Amazon Web Services and did my modelling there in Pyspark (this wasn't entirely necessary for the sake of the project but I wanted experience with Spark clusters and Pyspark). 

- Secondly, I clustered the different types of Ransomware into two clusters with similar behaviour, and used scikit-learn to train models focussed on each cluster. By grouping the ransomwares with similar behaviours I was able to greatly improve the ability to detect ransomware addresses.

Each notebook has a section for cleaning, balancing and labelling data, and a section for modelling.


### slides
This folder contains the slide deck I used when presenting on this project.


### presentation
This folder contains an mp4 of me presenting on this project.
