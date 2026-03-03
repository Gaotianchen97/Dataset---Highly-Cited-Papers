# Dataset-LLM-for-Highly-Cited-Papers
This repository shares the data from the paper “Are Large Language Models able to Predict  Highly Cited Papers? Evidence from Statistical Publications” authored by Zhanshuo Ye, Yiming Shuo, Rui Pan, Tianchen Gao, and Hansheng Wang.

## Predicting Highly Cited Papers Using Large Language Models


This repository provides a reproducible example demonstrating how large language models (LLMs) can be used to predict whether an academic paper is likely to become highly cited, based only on information available at publication time.

The example is based on the methodology described in our research on citation prediction using LLMs.



---

## Overview



Predicting the future impact of academic papers is a long-standing challenge in scientometrics. Traditional approaches rely on citation networks, early citation counts, or statistical indicators, which are unavailable at publication time.



Large language models offer a new paradigm. By leveraging their semantic understanding of scientific text and accumulated knowledge of research trends, LLMs can evaluate a paper’s potential impact based solely on textual and contextual information.



This repository demonstrates how to:



- Construct structured prompts for citation prediction

- Call LLM APIs to obtain predictions

- Run predictions on real publication data

- Evaluate prediction performance using standard metrics



---



## Dataset



The dataset used in this example consists of academic publications from representative journals in Statistics, Econometrics, and related fields. The data were collected from the Web of Science database.



Each paper includes the following fields:



- `title`: paper title  

- `abstract`: paper abstract  

- `keywords`: keywords (may be empty)  

- `year\_cleaning`: publication year  

- `publisher`: journal or publication source  

- `Total Citations`: total citation count (for evaluation only)  

- `highly\_cited\_5%`: binary label indicating whether the paper belongs to the top 5% most cited papers in its cohort  



Importantly, the LLM prediction uses only:



- title  

- abstract  

- keywords  

- year\_cleaning  

- publisher  



Citation counts and labels are used only for evaluation.



---



## Prompt Design



The structured prompt used in this study consists of five components:



1\. Task framing  

&nbsp;  The model is positioned as an expert reviewer in statistics and econometrics.



2\. Evaluation guidelines  

&nbsp;  The model evaluates papers based on three criteria:

&nbsp;  - methodological innovation  

&nbsp;  - long-term scientific value  

&nbsp;  - problem significance  



3\. Temporal background  

&nbsp;  The prompt provides contextual information about research trends during the publication period, ensuring the model evaluates papers using knowledge appropriate to that time.



4\. Reference examples  

&nbsp;  Example papers labeled YES and NO are included to calibrate decision boundaries.



5\. Output constraints  

&nbsp;  The model is strictly instructed to output only:



&nbsp;  YES  

&nbsp;  or  

&nbsp;  NO  



This ensures predictions can be parsed automatically.



The full prompt template is implemented directly in the notebook.



---



## Example Notebook



The file  `demo 01-05.ipynb`  demonstrates the complete workflow:



- loading data  

- constructing prompts  

- calling the LLM API  

- running small-scale and large-scale prediction  

- evaluating performance using:



&nbsp; - Accuracy (ACC)  

&nbsp; - True Positive Rate (TPR)  

&nbsp; - False Positive Rate (FPR)  

&nbsp; - Confusion Matrix  



---



## Installation



Install required dependencies:



```bash
pip install openai pandas tqdm scikit-learn matplotlib




```
