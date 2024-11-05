# Insomnia 
This is an "end-of-phase" project that I am conducting within the Flatiron School curriculum. To start, I descriptive and inferential analysis on the data where I asked and answered question and also performed hypothesis tests.

## Demographic Questions

I started my analysis by asking a handful of demographic related questions to get an idea of who was included in this sample size. My question were related to gender, age, occupation, BMI index and sleeping disorder.

After gainning a base level of understanding for those demogrpahics, I began my descriptive analysis
## Descriptive Analysis

In my descriptive analysis, I asked and answered six descriptive question about my data. Those questions were the following:
* Which-Profession-in-my-dataset-receives-the-most-amount-of-sleep?
* Which Profession has the most recorded cases of a sleeping disorder?
* On average, how much sleep does a person in each BMI category recieve?
* On average, how much sleep does someone with a sleeping disorder recieve compared someone with no sleeping disorder?
* On average, what is the quality of sleep that someone with a sleeping disorder recieves compared to those without a sleeping disorder?
* What distribution of Males and Females in my dataset are diagnosed with sleeping disorders?
* What percentage of my dataset has Insomnia?
* Of those with Insomnia, What percentage is male vs female?
* What is the distribution of age for patients with insomnia in my dataset?

Once I answered these questions, I felt that I had a good enough grasp on the data to continue my data exploration

## Insomnia vs Everyone Else

Before moving onto the inferential analysis, I wanted to get a better idea of how different the lifes of individuals with sleeping disorders is in comparison to those without. To do so, I measured the means of sleep duration, quality of sleep, physcical activity level, daily steps and stress level of patients with and without Insomnia. Now I felt ready to move onto my inferential analysis where I performed many hypothesis test that gave me a better idea of which statistics have a relation with Insomnia.

## Inferential Analysis

### With vs Without Insomnia Two Sample T-Tests

These tests were two sample t-tests in which I grouped my data by patients with insomnia (I) and without insomnia (NI) and found the mean ($\mu$) for each test variable and tested for a significant difference with a significance level (alpha) of 0.05. 

Null Hypothesis ($H_0$): $\mu_{I}$ = $\mu_{NI}$

Alternate Hypothesis ($H_A$): $\mu_{I}$ $\neq$ $\mu_{NI}$
#### Sleep Duration

In this test, I calculated the means and performed a two sample t-test. In this test, the mean ($\mu$) refers to the mean sleep duration for each group.

Result: **Reject the Null Hypothesis.** Although we observed a significant enough difference in sleep duration to reject the null hypothesis, this does not mean that the reason for the significant difference in sleep duration is due to having insomnia or not having insomnia. We simply observed that the difference exists.
#### Quality of Sleep

In this test, I calculated the means and performed a two sample t-test. In this test, the mean ($\mu$) refers to the mean quality of sleep for each group.

Result: **Reject the Null Hypothesis.** Although we observed a significant enough difference in quality of sleep to reject the null hypothesis, this does not mean that the reason for the significant difference in quality of sleep is due to having insomnia or not having insomnia. We simply observed that the difference exists.
#### Physical Activity Level

In this test, I calculated the means and performed a two sample t-test. In this test, the mean ($\mu$) refers to the mean physical activity level for each group.

Result: **Reject the Null Hypothesis.** Although we observed a significant enough difference in physical activity level to reject the null hypothesis, this does not mean that the reason for the significant difference in physical activity level is due to having insomnia or not having insomnia. We simply observed that the difference exists.
#### Stress Level

In this test, I calculated the means and performed a two sample t-test. In this test, the mean ($\mu$) refers to the mean stress level for each group.

Result: **Reject the Null Hypothesis.** Although we observed a significant enough difference in stress level to reject the null hypothesis, this does not mean that the reason for the significant difference in stress level is due to having insomnia or not having insomnia. We simply observed that the difference exists.
#### Heart Rate

In this test, I calculated the means and performed a two sample t-test. In this test, the mean ($\mu$) refers to the mean heart rate for each group.

Result: **Fail to Reject the Null Hypothesis.** In this test,  we did not observe enough of a difference to differentiate the change in means that would naturally occur from randomness
#### Daily Steps

In this test, I calculated the means and performed a two sample t-test. In this test, the mean ($\mu$) refers to the mean daily steps for each group.

Result: **Reject the Null Hypothesis.** Although we observed a significant enough difference in daily steps to reject the null hypothesis, this does not mean that the reason for the significant difference in daily steps is due to having insomnia or not having insomnia. We simply observed that the difference exists.

## The Model
My model creation has many steps in the process so lets look at each one step by step

#### Step 1: Cleaning and Preprocessing
#### Step 2: Shotgun Method
#### Step 3: GridSearch
#### Step 4: Building the Pipeline
#### Step 5: Finalizing the Pipeline

### Step 1: Cleaning and Preprocessing

Data cleaning and preprocessing, in this stage, its all about getting the dataset ready to be tested on. There were multiple columns that in their raw form are simply unable to be interpretted by a machine learning model. This step is designed to make each and every column in my dataset legible for my model. 
### Step 2: Shotgun Method

The shotgun method is designed to get a preliminary idea of which models are best for our dataset by testing a bunch of different models. For this dataset, I tested 8 different model. I tested the following
- Logistic Regressor
- Random Forest Classsifier
- Gradient Boosting Classifier
- AdaBoosting Classifier
- Bagging Classifier
- KNeighbors Classifier
- Decision Tree Classifier
- Extra Trees Classifier

Out of these 8, I got relatively similar scores for 3 of the models that being Logistic Regressor, Bagging Classifier and Extra Trees Classifier which are all included in the next step
### Step 3: GridSearch

This step was designed to get a better idea of which model performed the best. Unlike the shotgun method, this step included better reports on the models such as classification reports and confusion matricies. Also new in this step was the implementation of SMOTE, to balance out the classes being tested upon, and scaling, in order to create a more even weighting across the features and lastly hyperparameter grids earches, these gridsearches go through thousadns of possible parameter combinations and pick out the best performing combination for the scoring metric given. Because I am extra, I decided to do 3 different scoring metric for each of the models. A metric based on overall accuracy, precision and recall.

To me, recall was the most important metric. If i was able to maximize recall without jepardizing the overall accuracy of my model then I would consider that a job well done as that would people that very few patients with insomnia would go undiagnosed. The easy way to do that is to say that everyone has insomnia but that would result in a severe decrease in accuracy. So my goal from here was to find the best tradeoff between accuracy and recall
### Step 4: Building the Pipeline
During the GridSearch Step, I would that Extra Trees Classifier had the best scores when predicting so that is what i am going to use for the remainder of my model. 

In this step I took what I found the be the top Extra Trees Classifier paramaters of my notebook thus far and added all the preprocessing method Ive done so far in combination with an addition of PCA (dimensionality reduction) and the addition of a threshold reducer. The idea with both is that I can make it a little bit easier for my model to correctly predict whether a patient has insomnia or not. 

After this step was complete I was relatively happy with my results and felt confident finalizing my pipeline with everything in one.
### Step 5: Finalizing the Pipeline

This was the most straightforward step of the entire model buidling procress. In this step, I simply copied everything that I found to be an improvement for my model and combined it into a single pipeline. I would consider that fianl pipeline to be my finalized model.
### Conclusion

I think this model still has plenty of room for improvement, ideally I would love to see the recall get to 100% without having the accuracy getting below 80% but I am not sure how feasable that is. While I dont know how applicable my model is in the real world I would love to further study how doctors and other medical professionals go about diagnosing diseases and disorders. 
