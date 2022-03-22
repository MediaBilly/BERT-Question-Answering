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

This project is a university assignment for the course Deep Learning for Natural Language Processing.

## How I worked

* First of all, I fine-tune the bert-base-uncased on SQuAD 2.0 as I describe in this notebook:
[Models/qa-with-squad-2.0-dataset-and-bert-base.ipynb](./Models/qa-with-squad-2.0-dataset-and-bert-base.ipynb)
* Then, using the notebook [Evaluation Scripts/BERT_QA_with_SQuAD_2.0_evaluation.ipynb](./Evaluation%20Scripts/BERT_QA_with_SQuAD_2.0_evaluation.ipynb) I evaluated the performance of my model on paragraphs and questions I asked on them that were probably not contained in SQuAD dataset.
* After that, I converted the other 4 datasets described in the paper in SQuAD format and then I fine-tuned BERT on them using the same hyperparameters that gave the best score to the SQuAD 2.0 model (as the authors of the paper worked). The codes of corresponding models can be found in the [Models](./Models) folder.
* Finally, after fine-tuning all 5 models, I did the cross-evaluation as described in table 3 of the paper. The notebook with which I calculated the scores is [Evaluation Scripts/QA_cross-evaluation.ipynb](./Evaluation%20Scripts/QA_cross-evaluation.ipynb).

## Results

The paper equivalent table with the f1 scores I got is the following:

|          | SQuAD  | TriviaQA | NQ     | QuAC   | NewsQA |
| -------- | ------ | -------- | ------ | ------ | ------ |
| SQuAD    | 77.71% | 34.67%   | 51.39% | 14.45% | 44.28% |
| TriviaQA | 40.66% | 41.94%   | 37.60% | 8.93%  | 28.83% |
| NQ       | 60.02% | 32.41%   | 59.17% | 14.10% | 35.77% |
| QuAC     | 31.46% | 16.65%   | 31.06% | 27.53% | 24.25% |
| NewsQA   | 64.23% | 31.92%   | 48.44% | 15.08% | 54.16% |


## Hyperparameters used

The hyperparameters used are the following:

* Batch Size = 8
* Learning Rate = 1e-5
* Epochs = 3
* Max Token Sequence Length = 512

The training was done on [Kaggle](https://www.kaggle.com/) with an Nvidia Tesla P100 GPU

## Difficulties I faced during development

* The training time of the models was too long and the Google Colab GPU was throwing timeouts. So, the training of these models was done on [Kaggle](https://www.kaggle.com/).
* The NQ dataset was too huge in size, so I converted it to SQuAD format on Google Colab using this notebook: [Utilities/nq_to_squad.ipynb](./Utilities/nq_to_squad.ipynb). The other 3 were converted using my own computer following this guide provided in the paper: [https://github.com/amazon-research/qa-dataset-converter](https://github.com/amazon-research/qa-dataset-converter).

## Conclusion

As you can see from the table, all 5 models (QuAC not so much :/) generalize good between different datasets. The scores are similar to the paper ones but not so good, but personally I'm happy with the result. Some causes of low scores could be either the fact that sometimes the answers become truncated during tokenization (mainly in the TriviaQA dataset), or because the models have not learned to handle correctly cases where a question does not have any answer.

## Large files

Some large files which are too big to upload on gihub are here:
* The TriviaQA, NQ, QuAC, and NewsQA datasets in SQuAD format used in training can be found here: [https://drive.google.com/drive/folders/1IIXGeV6XHDsbZrrevTAy9Z-tZxs4ZWaG](https://drive.google.com/drive/folders/1IIXGeV6XHDsbZrrevTAy9Z-tZxs4ZWaG). 
* The saved models (state dicts only) can be found here: [https://drive.google.com/drive/folders/1Sa3-YZl4RW3WY2GFwtzIChd3VmHwqy74](https://drive.google.com/drive/folders/1Sa3-YZl4RW3WY2GFwtzIChd3VmHwqy74).
