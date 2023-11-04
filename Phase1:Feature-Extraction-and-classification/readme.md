<!DOCTYPE html>
<html>
<head>
    <title>Seizure Detection System</title>
</head>
<body>

<h1>Seizure Detection System</h1>

<h2>Project Description</h2>

<p>This project is part of the Computational Intelligence course, and it aims to implement an intelligent system for detecting seizures in epileptic patients from EEG signals. You are provided with an EEG dataset containing raw signals, and your task is to implement various stages of data processing. You'll need to preprocess the given signals, extract features from them, enhance the extracted features to achieve desired performance, and finally, classify the signals to achieve the ultimate goal of seizure detection. These tasks are the first phase of the project and will be carried out in two sub-projects. In the final phase of the project, you will further implement a system using your knowledge from this stage and deep learning methods.</p>

<h2>Dataset Details</h2>

<p>The dataset provided contains 500 segments of EEG signals, each approximately 23.6 seconds long, collected from a device with a sampling frequency of 173.61 Hz. Consequently, for each data point, you will have an input file of length 4097. The dataset is divided into five different categories, and you can find more details and access to the data in the following <a href="https://www.upf.edu/web/ntsa/downloads/-/asset_publisher/xvT6E4pczrBw/content/2001-indications-of-nonlinear-deterministic-and-finite-dimensional-structures-in-time-series-of-brain-electrical-activity-dependence-on-recording-regi?inheritRedirect=false&redirect=https%3A%2F%2Fwww.upf.edu%2Fweb%2Fntsa%2Fdownloads%3Fp_p_id%3D101_INSTANCE_xvT6E4pczrBw%26p_p_lifecycle%3D0%26p_p_state%3Dnormal%26p_p_mode%3Dview%26p_p_col_id%3Dcolumn-1%26p_p_col_count%3D1">link</a>.</p>

<h2>Preprocessing and Loading the Dataset</h2>

<p>The initial step in any data-driven project is to create a suitable structure for sequential data access. Throughout the implementation of your system, you will frequently need to access the dataset, and without a proper solution for loading the data, you will waste a lot of time on I/O operations. In this project, there is no need for you to implement a data loading solution since comprehensive explanations and codes will be provided in the exercise solving class.</p>

<p>After loading the data, you need to preprocess it. The general preprocessing steps usually involve data analysis, identifying the locations of essential information and noise in the data. However, it's worth noting that the preprocessing of the data is not the focus of this project. In this dataset, it's related to the fields of data mining and, more specifically, signal processing, and your task will not include these preprocessing steps.</p>

<h2>Feature Engineering (Task 1)</h2>

<p>The first major step in this project is the extraction of features from the EEG signals. Creating a suitable representation of the data is an essential step in building any intelligent system. Without this, the algorithms learned in class will not yield any specific results. In the first task, you need to advance the feature engineering part. In the exercise solving class, you will receive comprehensive explanations and introduction to various categories of general and specific feature types. It is expected that you implement at least 15 features from three different categories. The feature categories include:</p>

<ul>
    <li>Statistical</li>
    <li>Innovative</li>
    <li>Entropies</li>
    <li>LBP based features</li>
    <li>Time domain</li>
    <li>Frequency Domain</li>
</ul>

<h2>Signal Classification (Task 1)</h2>

<p>After feature extraction, you'll move on to classify these features. This dataset includes many problems, and you will receive detailed descriptions of them in the exercise-solving class. You need to implement three different algorithms, evaluate their performance using various metrics, and employ k-fold cross-validation with k set to 5 for performance evaluation. The algorithms you are required to implement are:</p>

<ul>
    <li>Support Vector Machine (SVM)</li>
    <li>Random Forest</li>
    <li>k-Nearest Neighbors (KNN)</li>
</ul>

<p>Analyze the effect of changing classifiers and the alteration of various classifier parameters. For each of these classifiers, report the following metrics:</p>

<ul>
    <li>Accuracy</li>
    <li>Precision</li>
    <li>Recall</li>
</ul>

<p>Additionally, for the best classifier, create a recall curve and calculate the confusion matrix. Test the impact of normalizing input data for each algorithm.</p>

</body>
</html>
