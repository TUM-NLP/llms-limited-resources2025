# llms-limited-resources2025

The GitHub repo for the Shared Task on LLMs with Limited Resources for Slavic Languages @ WMT2025 

## Overview
We present a shared task to train LLMs under **limited data and compute resources** for three Slavic languages: Ukrainian (uk), Upper Sorbian (hsb) and Lower Sorbian (dsb).

The objective of this Shared Task is to develop and improve LLMs for these languages. We consider two tasks that are to be evaluated jointly: **Machine Translation** (MT) and **Multiple-Choice Question Answering** (QA).


Ukrainian has roughly 40 million first language (L1) speakers spread all over the world and is a mid-resource language in NLP.
Upper and Lower Sorbian are very low-resource, Slavic minority languages, spoken in the Eastern part of Germany with 30k and 7k L1 speakers, respectively.
In this task, we aim to test and improve the performance of LLMs on these languages.

More practical details on the Shared Task can be found on the official webpage [here](https://www2.statmt.org/wmt25/limited-resources-slavic-llm.html).


## Datasets
Datasets and details about both Upper Sorbian and Lower Sorbian can be found in the `Sorbian` folder. 

Datasets and details about Ukrainian can be found in the `Ukrainian` folder. 


## Evaluation Methods

We will use **chrF++** to evaluate machine translation and **accuracy** to evaluate question answering.

The final ranking in the leaderboard will consider the scores from MT and QA equally.

For consistency with the previous WMT 2022 Shared Task, we also report BLEU for MT.



## Contact / Organisers
Please join our Google group for further information: https://groups.google.com/g/slavic-llms-mt2025.

All names are sorted in alphabetical order. 

TUM Heilbronn:
- Daryna Dementieva
- Marion di Marco
- Lukas Edman
- Alexander Fraser
- Kathy Hämmerl
- Shu Okabe

Witaj-Sprachzentrum (for both Upper and Lower Sorbian):
- Beate Brězan 
- Anita Hendrichowa 
- Marko Měškank
- Tomaš Šołta (language certificate)

## Acknowledgements
We thank the UNLP 2024 Shared Task 2024 team
- Roman Kyslyi
- Mariana Romanyshyn
- Oleksiy Syvokon

for kindly sharing the Ukrainian QA resources. 
Please acknowledge their work by citing the following paper:

Mariana Romanyshyn, Oleksiy Syvokon, and Roman Kyslyi. 2024. [The UNLP 2024 Shared Task on Fine-Tuning Large Language Models for Ukrainian](https://aclanthology.org/2024.unlp-1.9/). In *Proceedings of the Third Ukrainian Natural Language Processing Workshop (UNLP) @ LREC-COLING 2024*, pages 67–74, Torino, Italia. ELRA and ICCL.
