# Cancer Prediction with Lifestyle Factors

This project aims to develop a predictive model for cancer level based on lifestyle factors. The project is divided into three phases:

## Phase 1: Data Preprocessing

### Tasks

* Handle missing values
* Identify and remove outliers for numerical data
* Perform data reduction if necessary
* Convert numerical data to categorical data if necessary
* Perform stemming, lemmatizing, and stop-word removal for text data if necessary
* Conduct a series of statistical comparisons based on the dataset

## Phase 2: Extracting Frequent Patterns

### Tasks

* Extract frequent patterns from the clean dataset obtained from Phase 1
* Utilize relevant frequent pattern mining libraries, such as mlxtend

## Phase 3: Classification and Clustering

### Tasks

* Transform clean text data into vectors using BERT if data is text-based
* Perform clustering on the dataset using appropriate algorithms
* Implement classification based on the defined classification problem for each group
* Reserve a portion of the dataset for testing the implemented classification

## Requirements

* Python
* TensorFlow
* scikit-learn
* nltk (for text preprocessing)
* mlxtend (for frequent pattern mining)
* Hugging Face or sentence-transformers (for BERT text embedding)

## Installation

```bash
pip install tensorflow scikit-learn nltk mlxtend
