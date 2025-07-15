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

Notes: 
- The licences in both subfolders differ.
- External datasets can be used on top of the provided corpora. For fairness and reproducibility, they should, however, be publicly available.


## Evaluation Methods

We will use **chrF++** to evaluate machine translation and **accuracy** to evaluate question answering.

The final ranking in the leaderboard will consider the scores from MT and QA equally.

For consistency with the previous WMT 2022 Shared Task, we also report BLEU for MT.

We provide this [repository](https://github.com/TUM-NLP/wmt25-lrsl-evaluation) to help with the evaluation. It is a fork of [lm-evaluation-harness](https://github.com/EleutherAI/lm-evaluation-harness) and can be used to reproduce the baseline results and run evaluation script.

## Test sets

### Upper and Lower Sorbian
The test sets for both Sorbian languages are released in the same fashion:
- for MT, the test file has a test prefix (`test.de-{hsb|dsb}.de`) and contains the German source sentences (in their respective MT folder)
- for QA, the five test files (available in CSV and JSON formats) are in the `test` folder, with a test_ prefix (e.g., `test_{HSB|DSB}_A1.{csv|json}`). There are the same A1-B2 level questions and additionally a C1 level file (in their respective QA folder). 

### Ukrainian
The test sets for Ukrainian are in their respective folders: 
- for MT, `test.{cs|en}_uk.jsonl`
- for QA, `test.json`

We note here that the MT datasets come from the General MT Shared Task (WMT). Hence, they are in a format different from the development sets.


## Baseline results (development datasets)
For information purposes, we provide the baseline (zero-shot) results of Qwen2.5-3B-Instruct on all the development datasets (MT & QA). 

### Upper and Lower Sorbian

| Tasks | Metric | Value | Stderr |
| - | - | - | - |
| Sorbian |   |   |   |
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
| Ukrainian |   |   |   |
| - cze-ukr | bleu | 6.8134 | 0.1512 |
| - cze-ukr | chrf++ | 27.2625 | 0.2568 |
| - eng-ukr | bleu | 8.2124 | 0.1674 |
| - eng-ukr | chrf++ | 27.0139 | 0.2574 |
| UKR QA | acc | 0.3018 | 0.0186 |


## Submission procedures

### Output format
The output format for the Shared Task is a standardised **JSONL** file across languages and tasks, with four fields per instance:
- For MT, each output should contain: `dataset_id` (`wmtslavicllm2025_{lang_pair}`), `sent_id`, `source`, and `pred`
- For QA, each output should contain: `dataset_id` (`wmtslavicllm2025_qa_{lang}`), `question_id`, `question`, and `pred`

Below is the description of the four fields:
- `dataset_id`: this field is needed to assign your submission to the right track (i.e., language+task). It consists of `wmtslavicllm2025_` with the language pair for MT (`de-{hsb|dsb}` or `{cs|en}-uk`) and the language for QA (`qa_{hsb|dsb|uk}`)
- `sent_id` or `question_id`: this is a unique ID per instance. In some datasets, it is already present (Upper and Lower Sorbian QA). For the others, it is simply an ascending ID
- `source` or `question`: this comes from the input file with the source sentence (for MT) or the question (for QA) to check the correspondence between inputs and outputs
- `pred`: the output from your system (string or integer for Sorbian QA)

Moreover, please note that the Upper and Lower Sorbian QA outputs should be concatenated into one file in order of difficulty (A1, A2, B1, B2, C1).

To make the output format conversion easier, we provide two resources. 
First, dummy outputs are present in the `dummy_submission` folder of this GitHub repository. 
Second, if you are using our fork of `lm-evaluation-harness` (see above), the [conversion script](https://github.com/TUM-NLP/wmt25-lrsl-evaluation/blob/main/testphase-eval/convert_output_formats.py) has been updated to the final output format.

Summary of the modifications to make in the output:
- Ukrainian MT: changing the `dataset_id` for our shared task (`wmtslavicllm2025_{cs-uk|en-uk}`), changing the `doc_id` field name into `sent_id` and the `src_text` field name into `source`
- Ukrainian QA: adding the dataset_id (`wmtslavicllm2025_qa_ukr`) and `question_id` (e.g., `question-XXXX`); the prediction should be a **string** (not a list)
- Upper and Lower Sorbian MT: adding the dataset_id (`wmtslavicllm2025_de-{hsb|dsb}`) and sent_id (e.g., `de-hsb-XXXXX`)
- Upper and Lower Sorbian QA: adding the dataset_id (`wmtslavicllm2025_qa_{hsb|dsb}`), concatenating all QA files in increasing order of difficulty (A1, A2, B1, B2, C1)

For a full participation in our Shared Task, there will be seven files: 3 files for the Ukrainian track (CS-UK, EN-UK MT & UK QA), 2 files each for Upper and Lower Sorbian (DE-DSB|HSB MT & DSB|HSB QA).

### Submission platform
Thanks to the main Shared Task organisers, the submissions for our Shared Task can also be handled by the **OCELoT platform**: https://ocelot-wmt.azurewebsites.net/.

Tutorial:
1. After selecting our Shared Task, please register your team (yellow button). You need a team name and an email. You will then receive an email with a unique token to use (akin to a password).
2. Output files can be uploaded using the ‘create submission’ button (green button). Please select the corresponding test file (i.e., task + language) for your submission (warning: the names are quite similar, so please double check the selected file). You can choose whether this is your primary submission or not (it can be changed later).
3. Each output file must be submitted separately. Please remember that a submission is valid for us only when **both MT and QA outputs** are uploaded.
4. Once you have submitted your files, you will see a publication details section to fill in (with the institution name, the system name, and a small description of the system). The platform also needs a short paragraph describing your system, which we will use for our findings article. Please detail the models, datasets, and main techniques that you relied on. 

For better reproducibility, we highly recommend providing a link to your model in the system description paragraph by uploading it to HuggingFace (and mentioning external public datasets, when used).

To check whether your submissions are correctly taken into account by the system, OCELoT displays some automatic metrics: BLEU and chrF for MT and accuracy for QA (except for CS-UK MT). Please note that **these leaderboards are not the final ones**; we will provide the final ranking shortly after the submissions phase is closed.

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
