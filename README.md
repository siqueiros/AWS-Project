# AWS Project: Machine Learning with Amazon SageMaker Autopilot

## Introduction
As a Data Science major, I wanted my AWS Project to include knowledge that I have studied as apart of my Data Science degree. I followed Amazon's Hands-On Tutorial *Create a machine learning model automatically.* In this project, I implemented a machine learning model using one of Amazon's sample datasets. The goal of this project is to predict Job Title based on someone's age, marital status, education, house and etc using Amazon SageMaker Autopilot. I will be running a binary classifier.

## The Data

![Screen Shot 2020-11-23 at 6 40 49 PM](https://user-images.githubusercontent.com/38742519/100039715-a926ee80-2dba-11eb-9c8e-71676e535458.png)

## Setting up Amazon SageMaker Autopilot

![Screen Shot 2020-11-23 at 3 51 36 PM](https://user-images.githubusercontent.com/38742519/100040251-bf817a00-2dbb-11eb-9a9b-0230e28eeb5b.png)

## Downloading the Data

Once Amazon SageMaker Autopilot was ready, I proceeded to make a Python3 Data Science Notebook on Amazon SageMaker Autopilot which uses Jupyter Notebooks. This step was really simple. I downloaded the dataset as a csv and read the csv file as a Panda's dataframe to inspect the data. After downloading the data, I uploaded the csv into an Amazon S3 bucket. Amazon SageMaker creates this bucket.

## Creating an Amazon SageMaker Autopilot Experience

![Screen Shot 2020-11-23 at 2 06 46 PM](https://user-images.githubusercontent.com/38742519/100041293-e771dd00-2dbd-11eb-891d-60d3607527aa.png)

The Amazon SageMaker Autopilot Experience creates and runs the model. It preproccesses the data, analyzes data, runs feature engineering, and tunes the model. This make the machine learning process easier for a user. Typically I would do these steps myself. The Amazon SageMaker saves a lot time and it is also very friendly to users who have no data or machine learning knowledge. It is important to note that the Experience does take a while to run all of these steps.

## Deploying the Best Model

![Screen Shot 2020-11-23 at 3 49 22 PM](https://user-images.githubusercontent.com/38742519/100046607-5a328680-2dc5-11eb-9fca-1baf822860ee.png)

The Amazon SageMaker Autopilot Expereience ran 250 trials. I choose the best model and deployed it by making an HTTPS endpoint.

![Screen Shot 2020-11-23 at 3 49 30 PM](https://user-images.githubusercontent.com/38742519/100046935-2310a500-2dc6-11eb-8907-d091f92dac66.png)

## Predicting Job Title Using the Model

I predicted the first 2000 samples of the dataset using the endpoint. I also calculated accuracy, presion, recall and f1 score to analyze my results. The model performed very well.

Here are my results:

**Accuracy: 0.9880**

**Precision: 0.6552**

**Recall: 0.9048**

**F1 Score: 0.7600**

## Final Thoughts

The Amazon SageMaker Autopilot Experience makes machine learning easier and more efficient since it tunes and finds the best model. 

(A copy of the code is in the AWS_ML_Code.rst file)
