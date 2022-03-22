# BERT-Question-Answering

## Introduction

The purpose of this project was to fine-tune and cross-evaluate bert-base-uncased model in the following 5 Question Answering datasets:

1. [SQuAD 2.0](https://rajpurkar.github.io/SQuAD-explorer/)
2. [TriviaQA](https://nlp.cs.washington.edu/triviaqa/)
3. [NQ](https://ai.google.com/research/NaturalQuestions/download)
4. [QuAC](https://quac.ai/)
5. [NewsQA](https://github.com/Maluuba/newsqa)

More specifically, i had to first fine-tune and evaluate the BERT model on SQuAD 2.0 dataset and then do the on the other 4 and after that cross-evaluate between each model and dataset by calculating the corresponding f1 scores. 

In other words, the task was to reproduce the table 3 of the paper [What do Models Learn from Question Answering Datasets?](https://arxiv.org/pdf/2004.03490.pdf).

## How I worked

