# LLMs with Limited Resources for Slavic Languages

The GitHub repo for the Shared Task on LLMs with Limited Resources for Slavic Languages @ WMT2025 

## Overview
We present a shared task to train LLMs under **limited data and compute resources** for three Slavic languages: Ukrainian (uk), Upper Sorbian (hsb) and Lower Sorbian (dsb).

The objective of this Shared Task is to develop and improve LLMs for these languages. We consider two tasks that are to be evaluated jointly: **Machine Translation** (MT) and **Multiple-Choice Question Answering** (QA).


Ukrainian has roughly 40 million first language (L1) speakers spread all over the world and is a mid-resource language in NLP.
Upper and Lower Sorbian are very low-resource, Slavic minority languages, spoken in the Eastern part of Germany with 30k and 7k L1 speakers, respectively.
In this task, we aim to test and improve the performance of LLMs on these languages.

More practical details on the Shared Task can be found on the official webpage [here](https://www2.statmt.org/wmt25/limited-resources-slavic-llm.html).


## Datasets
Datasets and details about both Upper Sorbian and Lower Sorbian can be found in the `Sorbian` folder. We recall that the WMT 2022 datasets (parallel and monolingual data) for Upper and Lower Sorbian MT can be found in [this repository](https://github.com/mariondimarco/WMT22_UnsupVeryLowResMT_Data/).

Datasets and details about Ukrainian can be found in the `Ukrainian` folder. 


## Evaluation Methods

We will use **chrF++** to evaluate machine translation and **accuracy** to evaluate question answering.

The final ranking in the leaderboard will consider the scores from MT and QA equally.

For consistency with the previous WMT 2022 Shared Task, we also report BLEU for MT.

We provide this [repository](https://github.com/TUM-NLP/wmt25-lrsl-evaluation) to help with the evaluation. It is a fork of [lm-evaluation-harness](https://github.com/EleutherAI/lm-evaluation-harness) and can be used to reproduce the baseline results and run evaluation script.


## Baseline results (development datasets)
For information purposes, we provide the baseline (zero-shot) results of Qwen2.5-3B-Instruct on all the development datasets (MT & QA). 

### Upper and Lower Sorbian

| Tasks | Metric | Value | Stderr |
| - | - | - | - |
| Sorbian | acc | 0.4832 | 0.0269 |
| - deu-dsb | bleu | 0.5768 | 0.1207 |
| - deu-dsb | chrf++ | 11.9169 | 0.1488 |
| - deu-hsb | bleu | 0.7668 | 0.1519 |
| - deu-hsb | chrf++ | 13.3062 | 0.1416 |
| DSB QA | acc | 0.4671 | 0.0385 |
| - dsbqa-a1 | acc | 0.4333 | 0.0920 |
| - dsbqa-a2 | acc | 0.7143 | 0.0869 |
| - dsbqa-b1 | acc | 0.3636 | 0.0734 |
| - dsbqa-b2 | acc | 0.3571 | 0.0646 |
| HSB QA | acc | 0.4993 | 0.0375 |
| - hsbqa-a1 | acc | 0.7000 | 0.0851 |
| - hsbqa-a2 | acc | 0.6429 | 0.0922 |
| - hsbqa-b1 | acc | 0.3864 | 0.0743 |
| - hsbqa-b2 | acc | 0.2679 | 0.0597 |

### Ukrainian

| Tasks | Metric | Value | Stderr |
| - | - | - | - |
| Ukrainian | acc | 0.3018 | 0.0186 |
| - cze-ukr | bleu | 6.8134 | 0.1512 |
| - cze-ukr | chrf++ | 27.2625 | 0.2568 |
| - eng-ukr | bleu | 8.2124 | 0.1674 |
| - eng-ukr | chrf++ | 27.0139 | 0.2574 |
| UKR QA | acc | 0.3018 | 0.0186 |

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
