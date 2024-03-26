---
title: "Setup and Resources"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

### Overview

Welcome to the Amazon SageMaker Low-Code ML workshop. This workshop focuses on industry use cases: Industry Focussed - Financial Services Lab

The workshop is designed to be taken as required, feel free to complete the labs that pertain to you. In other words in any order, but there are somethings you need in place before you begin:
- Familiarity with the various Low-Code ML tools from AWS
- Amazon SageMaker studio environment
  
Let's begin with an overview of the tools that you will use.


{{% notice info %}}
The workshops below are designed to be run independently, so feel free to complete them in any order.
{{% /notice %}}

### Resources & Documentation

This workshop focus on experimenting with Low-Code Machine Learning (ML) tools from AWS. While this workshop will guide you through various use cases it is a good foundation to learn a little more about the tools you will be encountering.
You are welcome to skip this section if you are familiar with the services.
- [Introduction to Amazon SageMaker](https://www.youtube.com/watch?v=Qv_Tr_BCFCQ)
- [Introduction to SageMaker Data Wrangler - Documentation](https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler.html)
- [Introduction to SageMaker Autopilot - Documentation](https://docs.aws.amazon.com/sagemaker/latest/dg/autopilot-automate-model-development.html)
- [Introduction to SageMaker Jumpstart - Documentation](https://docs.aws.amazon.com/sagemaker/latest/dg/studio-jumpstart.html)
- [Workshop Demos - AWS Online Tech Talks](https://www.youtube.com/watch?v=GG1CsryLOFw)
  
Now that you are familiar with the tools you will be using continue to the next page to get started with Amazon SageMaker Studio.

### Setup Amazon Sagemaker Studio

 {{% notice Important %}}
  If this is not, a pre-arranged AWS Workshop or Immersion Day, you may be required to use your own AWS Account to perform these steps. This may incur some charges. Make sure to cleanup all resources that are created as part of this workshop after your data science experimentation.
  {{% /notice %}}

#### Launch/Setup Amazon SageMaker Studio
[Amazon SageMaker Studio](https://aws.amazon.com/sagemaker/studio/) is a web-based, integrated development environment (IDE) for machine learning that lets you build, train, debug, deploy, and monitor your machine learning models. Studio provides all the tools you need to take your models from experimentation to production while boosting your productivity.

Follow the steps below to onboard to Amazon SageMaker Studio using Quick Start.

{{% notice Important %}}
  If this is not, a pre-arranged AWS If you already have a SageMaker Studio domain setup in your account, ensure it is updated to the latest version as per the instructions [here](https://docs.aws.amazon.com/sagemaker/latest/dg/studio-tasks-update.html) and skip the below steps.
  {{% /notice %}}

- Open AWS console and switch to AWS region you would like to use.
 - - SageMaker Studio is available in the following [regions](https://docs.aws.amazon.com/sagemaker/latest/dg/studio.html).

- In the search bar, type _SageMaker_ and click on _Amazon SageMaker_. 
  ![SageMaker](/images/image3.png?featherlight=false)

- Click on _Amazon SageMaker Studio_ (first option on the left pane). 
![SageMaker](/images/image11.png?featherlight=false)

- Click on _Quick start_.
- Define _User name_ as _sagemakeruser_ for example.

- Select _Create a new role_ under Execution role.
![SageMaker](/images/image8.png?featherlight=false)

- Keep the defaults and click _Create Role_.
![SageMaker](/images/image9.png?featherlight=false)

- You will see that the role is successfully created
You can see that the option _Enable Amazon SageMaker project templates and JumpStart for this account and Studio users_ is enabled. Keep this default setting.

- Choose the newly created role and click _Submit_.
![SageMaker](/images/image18.png?featherlight=false)

- The SageMaker Studio environment will stay in _Pending_ state for a few minutes. 
![SageMaker](/images/image6.png?featherlight=false)

- After a few minutes, the state will transition to _Ready_. 
![SageMaker](/images/image4.png?featherlight=false)

- Once Amazon SageMaker Studio is ready then click on Open Studio. The page can take 1 or 2 minutes to load when you access SageMaker Studio for the first time.
![SageMaker](/images/image7.png?featherlight=false)

- You will be redirected to a new web tab that looks like this: 
![SageMaker](/images/image5.png?featherlight=false)

Congratulations! You have successfully created a SageMaker Studio domain.

Let's get started with the workshops by downloading the required notebooks.
