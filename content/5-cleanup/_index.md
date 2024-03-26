---
title: "Clean up resources"
date: "`r Sys.Date()`"
weight: 6
chapter: false
pre: " <b> 6. </b> "
---

{{% notice note %}}
Training jobs and logs cannot be deleted and are retained indefinitely.
{{% /notice %}}

{{% notice warning %}}
If you plan to explore other exercises in this guide, you might want to keep some of these resources, such as your Amazon SageMaker Studio, S3 bucket, and IAM role.
{{% /notice %}}

To avoid incurring unnecessary charges, use the AWS Management Console to delete the endpoints and resources that you created while running the exercises in this workshop.

Open the Amazon SageMaker Console  and delete the following resources:
1. The endpoint configuration.
- Under Inference, choose Endpoint configurations. 
![SageMaker](/images/image20.png?featherlight=false)

- Choose the endpoint configuration that you created in the example, choose Actions, and then choose Delete. 
![SageMaker](/images/image12.png?featherlight=false)

2. The endpoint. Deleting the endpoint also deletes the ML compute instance or instances that support it.
- Under Inference, choose Endpoints. 
![SageMaker](/images/image15.png?featherlight=false)
- Choose the endpoint that you created in the example, choose Actions, and then choose Delete.
![SageMaker](/images/image13.png?featherlight=false)

3. The model.
- Under Inference, choose Models. 
![SageMaker](/images/image19.png?featherlight=false)
- Choose the model that you created in the example, choose Actions, and then choose Delete.
![SageMaker](/images/image24.png?featherlight=false)

4. Amazon SageMaker Studio
- Ensure that your Amazon SageMaker studio has been shutdown by selecting Shutdown from the File menu, followed by Shut Down All 
![SageMaker](/images/image10.png?featherlight=false)

1. Choose Control Panel on the left side of the page to open the SageMaker Domain Control Panel.
2. Repeat the following steps for each user in the User name list.
- Choose the user.
- On the User Details page, for each non-failed app in the Apps list, choose Delete app.
- On the Delete app dialog, choose Yes, delete app, type delete in the confirmation field, and then choose Delete.
- When the Status for all apps show as Deleted, choose Edit.
- From the Edit User page, choose Delete user.
- On the Delete user dialog, choose Yes, delete user, type delete in the confirmation field, and then choose Delete.
  
{{% notice warning %}}
When a user is deleted, they lose access to the Amazon EFS volume that contains their data, including notebooks and other artifacts. The data is not deleted and can be accessed by an administrator.
{{% /notice %}}

7. When all users are deleted, choose Delete Domain.
8. On the Delete Domain dialog, choose Yes, delete Domain, type delete in the confirmation field, and then choose Delete.
9. Open the [Amazon S3 Console](https://console.aws.amazon.com/s3/) , and then delete the bucket that you created for storing model artifacts and the training dataset.
10.  Open the [Amazon CloudWatch Console](https://console.aws.amazon.com/cloudwatch/) , and then delete all of the log groups that have names starting with /aws/sagemaker/.
11.  Amazon SageMaker Studio will create an EFS volume that contains the user data, this will incur costs and if you are sure you no longer need the data, do delete the EFS volume by going to the [Amazon EFS Console page](https://console.aws.amazon.com/efs/)
- Select the EFS volume and press the Delete button.


Thank you for taking your time to finish this workshop!!!
