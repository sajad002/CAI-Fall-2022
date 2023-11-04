<!DOCTYPE html>
<html>
<body>

<h1>Feature Evaluation and Selection - Task 2</h1>

<p>After extracting features, it's time to move on to feature selection. For this task, you need to implement a comprehensive feature selection method. In this process, we make use of various components of feature selection methods:</p>

<ul>
    <li>How well each feature acts on its own</li>
    <li>How different each feature is from the rest of the features in general</li>
</ul>

<p>Regarding the first point, you should examine how well a feature can distinguish the data on its own. To evaluate this, we use a decision tree classifier, attempting to classify the data with just one feature. The accuracy of the output will be a measurement of the quality of the feature.</p>

<p>For the second metric, we utilize the correlation metric to assess individual features (pairwise comparisons). A good feature is one that has the lowest correlation with the rest (additional note: comparison with all features, explained in the exercise-solving class).</p>

<p>Finally, the two values obtained must be combined. To combine these two values, first normalize them, and then employ a method similar to the F1 score calculation.</p>

<p>The primary output of this section will be the selected features. Additionally, in your report, describe the feature selection process and try to explain which features contained information and which ones were redundant.</p>

<h2>Improving Accuracy with Segmentation - Task 2</h2>

<p>Finally, in the last part, you should attempt to enhance the model's accuracy and speed using segmentation. In this phase, you'll first divide your data into different sections using a segmentation algorithm. Then, you'll train the previous system on each segment individually. During testing, based on which section the input data falls into, you'll use the corresponding subsystem. In the end, you'll have a unique system for seizure detection.</p>

<h2>Evaluation with Different Problems - Task 2</h2>

<p>As explained in the exercise-solving session, there are various problems within this dataset. According to the explanations, select three different 2-class and one 3-class problems, and evaluate your method on them.</p>

</body>
</html>
