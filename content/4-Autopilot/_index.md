---
title: "Create SageMaker Autopilot"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 4.1 </b> "
---

### Overview

Amazon SageMaker Autopilot is a feature-set that automates key tasks of an automatic machine learning (AutoML) process. It explores your data, selects the algorithms relevant to your problem type, and prepares the data to facilitate model training and tuning.

A few of the many things SageMaker Autopilot does behind the scenes for you:
- Automatically handles missing data.
Provides statistical insights about columns in your dataset.
- Automatically extracts information from non-numeric columns, such as date and time information from timestamps.
- Automatically handles imbalance in your data.
- Automatically creates feature engineering (FE) pipelines most adapted to your problem. Those FE pipelines consist of FE transformations coming from both native and [custom](https://github.com/aws/sagemaker-scikit-learn-extension) scikit-learn-compatible FE transformations invented and open-sourced by Amazon.
- Automatic model selection.
- Automatically infers the type of predictions that best suit your data, such as [binary classification](https://docs.aws.amazon.com/machine-learning/latest/dg/binary-classification.html[) , ]multi-class classification](https://docs.aws.amazon.com/machine-learning/latest/dg/multiclass-classification.html) , or [regression](https://docs.aws.amazon.com/machine-learning/latest/dg/regression.html) .
- [Explores high-performing algorithms](https://aws.amazon.com/blogs/aws/amazon-sagemaker-Autopilot-fully-managed-automatic-machine-learning/) such as gradient boosting decision trees, feed-forward deep neural networks, and logistic regression, and trains and optimizes hundreds of models based on these algorithms to find the model that best fits your data.
- Tries different ensembling strategies to arrive at the best winning combination of learners.
- Automatically cross validates data to flag problems like over-fitting or selection bias and gives insights on how the model will generalize to an independent dataset.
- Performs automatic model Hyper Parameter Optimization (HPO).
- Runs epsilon-greedy bandit tests for each of the FE pipelines, and progressively invests more HPO budget on the most rewarding FE pipeline.
- Automatically creates a leaderboard that ranks the candidate models based on user provided success metric such as accuracy, precision, recall, or area under the curve (AUC).
- Lets you automatically deploy the best model for real-time and batch inference.
Automatic notebook generation for exploratory data analysis.
- Uses SageMaker Clarify under the covers to provide model agnostic feature attribution metrics using [SHAPley values](https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-shapley-values.html).
- Uses SageMaker Experiments behind the scenes to automatically capture data and model lineage for each of the candidate models trained during the process.

### Creating an Autopilot Experiment
To create a SageMaker Autopilot experiment, we'll be using the transformed dataset that we saved in the final step of previous exercise using Data Wrangler. This data was saved to S3.

- The image below shows the last step we performed in Data Wrangler.
![SageMaker](/images/2-CreateS3Bucket/image12.png?featherlight=false)

- To create an Autopilot experiment, the **Experiment and data details** page is already auto-populated for you.
![SageMaker](/images/2-CreateS3Bucket/image13.png?featherlight=false)

- In the next page **Target and features** - you can select the target column as **loan_status** and do feature selection if needed. For our exercise, let's use all columns other than the target column.
- Choose the target column as **loan_status**. 
![SageMaker](/images/2-CreateS3Bucket/image14.png?featherlight=false)
- Next, choose the training method. Here, you have 3 options - **Auto, Ensembling** or **HPO**. By default, **Auto** is chosen as the training method.
- SageMaker Autopilot can automatically select the training method based on the dataset size, or you can select it manually. The choices are as follows:
- - Ensembling – Autopilot uses the AutoGluon library to train several base models. To find the best combination for your dataset, ensemble mode runs 10 trials with different model and meta parameter settings. Then Autopilot combines these models using a stacking ensemble method to create an optimal predictive model. For a list of algorithms that Autopilot supports in ensembling mode, see the following Algorithm support section.
- - Hyperparameter optimization (HPO) – Autopilot finds the best version of a model by tuning hyperparameters using Bayesian optimization or multi-fidelity optimization while running training jobs on your dataset. HPO mode selects the algorithms that are most relevant to your dataset and selects the best range of hyperparameters to tune your models. To tune your models, HPO mode runs up to 100 trials (default) to find the optimal hyperparameters settings within the selected range. If your dataset size is less than 100 MB, Autopilot uses Bayesian optimization. Autopilot chooses multi-fidelity optimization if your dataset is larger than 100 MB. In multi-fidelity optimization, metrics are continuously emitted from the training containers. A trial that is performing poorly against a selected objective metric is stopped early. A trial that is performing well is allocated more resources.
- - Auto – Autopilot automatically chooses either ensembling mode or HPO mode based on your dataset size. If your dataset is larger than 100 MB, Autopilot chooses HPO. Otherwise, it chooses ensembling mode. 
![SageMaker](/images/2-CreateS3Bucket/image15.png?featherlight=false)

- Press _Next: Deployment and advanced settings_ and complete the values as shown in the diagram below.
- You can either set the problem type yourself (binary classification) or set it to _Auto_ to let Autopilot automatically identify the problem type based on the provided dataset.
- You can also tag an Autopilot experiment with key value pairs of information.
![SageMaker](/images/2-CreateS3Bucket/image16.png?featherlight=false)

- Once we populate all the values, let us hit _Next: Review and create_ then _Create Experiment_ to kickoff the Autopilot experiment.
![SageMaker](/images/2-CreateS3Bucket/image17.png?featherlight=false)

- Once we launch the experiment, we are taken to a newer interface (as shown below) that show the status of the different steps of the experiment as they are run.
![SageMaker](/images/2-CreateS3Bucket/image18.png?featherlight=false)

- Once the experiment is complete, you can see a leaderboard with all the models ranked in descending order of their performance (shown below).
- You can also see a button called "Open data exploration notebook" at the top right corner. Clicking this button opens up a notebook which encapsulates all the automated analyses and data insights Autopilot has generated for you. 
![SageMaker](/images/2-CreateS3Bucket/image19.png?featherlight=false)

Let's look into the results of this data exploration notebook.
- Dataset summary provides you with a breakdown of all the different types of features and their corresponding share (%), number of duplicate rows, percentage of missing target labels etc. 
![SageMaker](/images/2-CreateS3Bucket/image20.png?featherlight=false)

- Target analysis shows how balanced your class distribution is with the percentage of classes and missing data. 
![SageMaker](/images/2-CreateS3Bucket/image21.png?featherlight=false)

- Data Sample shows a slice of the sample data. 
![SageMaker](/images/2-CreateS3Bucket/image22.png?featherlight=false)

- Cross Column Statistics provides a correlation matrix which we can use to identify highly correlated features in our dataset. We had already previously established this in Data Wrangler. The correlation matrix mostly looks good.
![SageMaker](/images/2-CreateS3Bucket/image23.png?featherlight=false)

- In addition, we also get information on the cardinality of data, anamolies in data, descriptive statistics of the feature columns and more as shown below in this notebook. 
![SageMaker](/images/2-CreateS3Bucket/image24.png?featherlight=false)

![SageMaker](/images/2-CreateS3Bucket/image25.png?featherlight=false)

Next, we can also look into the model details to understand the various important insights Autopilot generates for you.
- First, Autopilot generates explainability report generated via [Amazon SageMaker Clarify](https://aws.amazon.com/sagemaker/clarify/) , making it easier to understand and explain how the models make predictions. Explainability reports include feature importance values so you can understand how each attribute in your training data contributes to the predicted result as a percentage. The higher the percentage, the more strongly that feature impacts your model’s predictions. You can download the explainability report as a human readable file, view model properties including feature importance in SageMaker Studio, or access feature importance using the [SageMaker Autopilot APIs](https://docs.aws.amazon.com/sagemaker/latest/dg/autopilot-reference.html).
- You can access these insights by clicking on "View model details".
![SageMaker](/images/2-CreateS3Bucket/image26.png?featherlight=false)

- You can also look at all the parameters and hyperparameters for the best model.
[SageMaker](/images/2-CreateS3Bucket/image27.png?featherlight=false)

The report also gives you metrics like confusion matrix, PR and RoC curves like shown below. 
[SageMaker](/images/2-CreateS3Bucket/image28.png?featherlight=false)

[SageMaker](/images/2-CreateS3Bucket/image29.png?featherlight=false)

- You can also look at the pointers to all the artifacts for the best model.
[SageMaker](/images/2-CreateS3Bucket/image30.png?featherlight=false)

{{% notice note %}}
Explainability results are not shown for the secondary (non-winning) models.
{{% /notice %}}

### Model deployment and inference
- Once the experiment is complete and a winning model has been established, you can deploy the model directly for inference from the UI.
[SageMaker](/images/2-CreateS3Bucket/image31.png?featherlight=false)

- You can deploy it as a real-time RESTful endpoint.
[SageMaker](/images/2-CreateS3Bucket/image32.png?featherlight=false)

- Or alternatively, you can also use the Autopilot best model to run batch scoring on your unlabeled data directly via the UI.
[SageMaker](/images/2-CreateS3Bucket/image33.png?featherlight=false)

- Autopilot models can also be shared with SageMaker Canvas users via the Share Model button as shown below.
[SageMaker](/images/2-CreateS3Bucket/image34.png?featherlight=false)

- Suppose you deployed the model as a real-time endpoint, you should be able to see the deployed endpoints under the Deployments section in the left pane as shown in the figure below.
[SageMaker](/images/2-CreateS3Bucket/image35.png?featherlight=false)

1. Early stopping for HPO mode
You can also stop the Autopilot experiment after a certain number of trials (e.g. 20) instead of the default 250 max trials and still get results. By default, Autopilot tries to explore up to 250 trials with default settings. Suppose Autopilot starts consistently creating trials with an objective metric value greater than 0.90 accuracy (which is your desired goal) after the first 10 to 15 trials. You can click ‘Stop the experiment’ at this point for the purposes of this experiment.

2. Handling missing values
For numeric feature columns, Autopilot doesn't interpret zeros as missing values and treats them as valid zero values. If they represent missing values then Autopilot should produce better results if you encode them as missing values by replacing them with an empty string. Generally, when using Autopilot, you should only impute missing values when you have some domain specific knowledge. It's usually better to leave missing values as missing values e.g., empty strings.

3. Programmatic Access via SageMaker SDK
All operations (actions) performed in this demo via the SageMaker UI can be achieved using [SageMaker APIs](https://docs.aws.amazon.com/sagemaker/latest/dg/autopilot-reference.html) .
