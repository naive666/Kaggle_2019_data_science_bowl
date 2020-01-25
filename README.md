# [Kaggle_2019_data_science_bowl](https://www.kaggle.com/c/data-science-bowl-2019)
<div align=center><img width='1000', height='200' src='/header.png' /></div>

## Content
   - [Introduction](#introduction)
   - [Description](#description)
   - [Feature Engineering](#feature-engineering)
   - [Model](#model)
   - [Contributors](#contributors)
   
## Introduction
This is my first formal Kaggle competition, and the environment in the competition forum is quite different from that of completed competitions. Thanks to the help from the discussion board, I can quickly get involved at the begining. The feature engineering process from some pioneers makes a real big contribution to most competitors' kernels, and it also shows a deep understanding of the aim of this project.
My best result in private leaderboard is 0.535, which is around top 10%, but unfortunately I do not choose this as my final submission, and my result is 0.530, which drops to about top 25%.


## Description
Illuminate Learning. Ignite Possibilities.
Uncover new insights in early childhood education and how media can support learning outcomes. Participate in our fifth annual Data Science Bowl, presented by Booz Allen Hamilton and Kaggle.
PBS KIDS, a trusted name in early childhood education for decades, aims to gain insights into how media can help children learn important skills for success in school and life. In this challenge, you’ll use anonymous gameplay data, including knowledge of videos watched and games played, from the PBS KIDS Measure Up! app, a game-based learning tool developed as a part of the CPB-PBS Ready To Learn Initiative with funding from the U.S. Department of Education. Competitors will be challenged to predict scores on in-game assessments and create an algorithm that will lead to better-designed games and improved learning outcomes. Your solutions will aid in discovering important relationships between engagement with high-quality educational media and learning processes.
Data Science Bowl is the world’s largest data science competition focused on social good. Each year, this competition gives Kagglers a chance to use their passion to change the world. Over the last four years, more than 50,000+ Kagglers have submitted over 114,000+ submissions, to improve everything from lung cancer and heart disease detection to ocean health. 

## Feature Engineering
Feature engineering is also regarded as the most important part of Kaggle.
- **Generating New Features**  
  Based on the demand of project, several new features are generated manually. I have to admit that this is a arduous work, and most ideas come from an experienced kaggler [Bruno Aquino](https://www.kaggle.com/braquino/convert-to-regression), whose open sourced idea also save most competitors in this game  
  
- **Check Distribution**    
  Check feature distribution in train set and test set, if the distribution is obviously different, it is reasonable to eliminate such features. Also, I check if the feature contains too many zeros, which is ineffective for the final prediction  
  
- **Change Json**    
  It is not necessary in every model. I do so because some feature titles could not be recognized by lightgbm, and therefore needed to be changed in a readable format  
  
## Model
- Select Top Features  
Since there are over 900 features, and some of the features are not as crucial as others, reduce the influence of those feature may enhance the model performance. Therefore, I first use all features as input, and hypertune the parameters with Bayesian Optimization to get the best model with full features. Next, use this model to do 5 cross validations, and record the feature importance in each validation. Following that, calculate the average score in the 5 epochs of each feature, sort them afterward, and I get the rank of feature importance.   

- Top Features Cross Validation
It is very influencial to choose a threshold of feature importance, i.e. Above what average score should I choose the feature? After several trials, the features whose average importance score in the interval of 5 and 600 show impressive result. Then, use the selected features to cross validation. Owing to excessive data, runing the model in PC is seemingly not a good choice, I use the Kernel provided by Kaggle, but it still takes a lonf time to finish running.   

- Result Transformation
This is a multi-category problem, but the method above I use regression method, and thus the final step is to transfer the raw results to categories. Thanks to some Kaggle contributors, they apply percentile method to transfer data.

## Result
It is surprising that the CV score touchs 0.60, which is relatively high as compared to other competitors' CV score, but the result in public Leaderboard is not that impressive, only 0.532, roughly rank 1200 in public leaderboard. However, in another model (Kernel Version 11), my public score gets to 0.538, which is chosen as final submission. Unfortunately, the so-called best model score drops to 0.527 while the previous one lift from 0.532 to 0.535, which is top 10%. 

## Contributors
<a href="https://github.com/naive666"><img src="https://avatars2.githubusercontent.com/u/53068274?s=40&v=4&button=True" /></a>










