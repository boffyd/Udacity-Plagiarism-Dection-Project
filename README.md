# Plagiarism Project, Machine Learning Deployment

This repository contains code and associated files for deploying a plagiarism detector using AWS SageMaker.

## Project Overview

In this project, you will be tasked with building a plagiarism detector that examines a text file and performs binary classification; labeling that file as either *plagiarized* or *not*, depending on how similar that text file is to a provided source text. Detecting plagiarism is an active area of research; the task is non-trivial and the differences between paraphrased answers and original work are often not so obvious.

This project is broken down into three main notebooks:

---

## Notebook 1: Data Exploration
* Load in the corpus of plagiarism text data.
* Explore the existing data features and the data distribution.

The data contains a dataset with multiple text files, which characterised 
 
 * as per the task (A- E), which is a topic that might be included in a curriculum, i.e "What is inheritance in object oriented programming?"
 * a plagiarism label/category
 > 1. `cut`: An answer is plagiarized; it is copy-pasted directly from the relevant Wikipedia source text.
 > 2. `light`: An answer is plagiarized; it is based on the Wikipedia source text and includes some copying and paraphrasing.
 > 3. `heavy`: An answer is plagiarized; it is based on the Wikipedia source text but expressed using different words and structure. Since this doesn't copy directly from a source text, this will likely be the most challenging kind of plagiarism to detect.
> 4. `non`: An answer is not plagiarized; the Wikipedia source text is not used to create this answer.
> 5. `orig`: This is a specific category for the original, Wikipedia source text. We will use these files only for comparison purposes.

The number of files is 100, 95 of these are answers and 5 are original source texts.

---

## Notebook 2: Feature Engineering

* Clean and pre-process the text data.
* Define features for comparing the similarity of an answer text and a source text, and extract similarity features
> `Containment Features` The longest common subsequence is the longest string of words (or letters) that are the same between the Wikipedia Source Text (S) and the Student Answer Text (A). This value is also normalized by dividing by the total number of words (or letters) in the Student Answer Text.

> `Longest Common Sequence` which is a method to determine overlap in word usage between two documents, The longest common subsequence is the longest string of words (or letters) that are the same between the Wikipedia Source Text (S) and the Student Answer Text (A). This value is also normalized by dividing by the total number of words (or letters) in the Student Answer Text.
* Once feature engineering capability has been enabled, these functions are applied against the base data set and a final data set with select "good" features, are chosen by analyzing the correlations between different features.
* Create train/test `.csv` files that hold the relevant features and class labels for train/test data points.

---

## Notebook 3: Train and Deploy Your Model in SageMaker

* The data set is uploaded your train/test feature data to S3.
* Define a binary classification model and a training script, for this model a random forest model was chosen
* Train your model and deploy it using SageMaker.
* Evaluate your deployed classifier.  The accuracy was greater than 90%

---

Please see the [README](https://github.com/udacity/ML_SageMaker_Studies/tree/master/README.md) in the root directory for instructions on setting up a SageMaker notebook and downloading the project files (as well as the other notebooks).

