---
title: "Introduction"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

## Introduction

Experiment Faster with AWS Machine Learning - Low-Code ML tools for Data Scientists ussing SageMaker Autopilot:

![Architechture](/images/image22.png?featherlight=false)

## Solution Overview
The Machine Learning (ML) journey requires continuous experimentation and rapid prototyping to be successful. In order to create highly accurate and performant models, data scientists have to first experiment with feature engineering, model selection and optimization techniques. These processes are traditionally time consuming and expensive. In this workshop, you will learn how the Low-Code ML capabilities found in Amazon SageMaker Autopilot make it easier to experiment faster and bring highly accurate models to production more quickly and efficiently.

### What will you learn
- Learn how to simplify the process of data preparation and feature engineering, and complete each step of the data preparation workflow.
- Understand how to automatically build, train, and tune the best machine learning models based on your data, while allowing you to maintain full control and visibility.
- This track comprises of use-case covering: Tabular data

### Steps by steps

1. [Seup and Resources](2-SetupandResources/)

   In this step, we will setup Amazon Sagemaker Studio then focus on setup SageMaker Autopilot.

2. [Finacial Services Lab](3-Lab/)

   The Financial Services section of the workshop focuses on the Financial Services industry and introduces about this use-case lending loans to risky applicants.

3. [Creating SageMaker Autopilot](4-Autopilot/)

   Then we will create an Autopilot Experiment. We'll be using the transformed dataset that we saved in the final step of previous exercise using Data Wrangler.

4. [Resource Cleanup](5-Cleanup/)

   Cleanup.

Let’s get started by logging in to the AWS console with your AWS account, it’s best to use an IAM Account with admin access, and then pick a region. I will use the ús-east-1 (N.Virginia) region in this workshop.
