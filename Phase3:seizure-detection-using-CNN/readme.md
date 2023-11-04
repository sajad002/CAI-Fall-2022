<!DOCTYPE html>
<html>
<body>

<h1>Final Phase of Computational Intelligence Project</h1>

<p>In this final phase, you are required to apply your knowledge from the previous phases, along with implementing a neural network to differentiate seizure data from normal data in a new dataset. This project can be carried out in groups of two.</p>
<p><a href="https://drive.google.com/drive/folders/1owPXAQxT8yDFJzPdjghyaM1bV4Fi1tTa?usp=sharing/"> - Implemented Code and Dataset on Google Drive</a></p>

<h2>1- Dataset Preparation</h2>

<p>In the initial stage, you must load the dataset and prepare it for classification. You can access the dataset from the following link:</p>

<p><a href="https://physionet.org/content/chbmit/1.0.0/">Dataset Link</a></p>

<p>Following the instructions provided in the exercise-solving class and video, load the data, remove noise, and work with the final data. Make sure to:</p>

<ol>
    <li>Load the data adequately.</li>
    <li>Balance the dataset after loading.</li>
    <li>Ensure that at least 25% of the normal data comes from records containing seizures.</li>
</ol>

<h2>2- Classification</h2>

<p>In this stage, you need to implement your classification algorithm. Your algorithm should include a convolutional neural network (CNN) combined with features extracted in the previous stage. The method of combining should involve appending features to the feature layer, with further details provided in the exercise-solving class.</p>

<p>The selection of the window length (data size for classification) is up to you. In this stage, you must reach a meaningful conclusion and demonstrate that the chosen network structure is appropriate. You should show that changing the size of the network affects its performance (to do this, you need to show that increasing or decreasing the network size reduces efficiency).</p>

<h2>3- Presentation of Results</h2>

<p>Finally, you are required to present your results. For this, calculate the metrics you've learned in previous sections for the test data. Then, calculate accuracy in detecting seizure intervals according to the explanations in the exercise-solving class. Afterward, obtain the false alarm rate and the distribution of the duration of false alarms.</p>

<p>Given the tools and knowledge you have, along with the previous phases, present a comprehensive solution for building a seizure detection system within one page. Assume that your system is intended to be implanted in the patient's body, where data is continuously fed into it. When your system detects a seizure, it releases a drug that, although has side effects, immediately stops the seizure.</p>

<h2>4- Extra Credit</h2>

<p>Extra credit will be awarded to individuals who achieve higher accuracy and employ creative methods. Note that if you intend to earn extra credit, the data selection should be based on the explanations provided in the exercise-solving class.</p>

</body>
</html>
