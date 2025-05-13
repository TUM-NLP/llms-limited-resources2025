# Datasets description for Ukrainian

We compiled the datasets for the Ukrainian language from various opensource resources that kindly allowed us to use the data for the shared task.

## Machine Translation

We provide pairs for two translation tasks:
* Chezh -> Ukrainian (cs-uk);
* English -> Ukrainian (en-uk)

The development data is the compilation of [WMT](https://www2.statmt.org/wmt25/index.html) datasets from 2022-2024 editions.

Datasets size:

|        Pair        | Dev  |
|--------------------|------|
| CS-UK (Czech–Ukrainian)   | 6263 |
| EN-UK (English–Ukrainian) | 5108 |

For **training**, we recommend to refer to [WMT2025 main track setup](https://www2.statmt.org/wmt25/mtdata/) with the details on various datasets useful for WMT systems fine-tuning.

### Data License

Apache-2.0

## Question Answering

We re-use the data from [UNLP2024 Shared Task](https://github.com/unlp-workshop/unlp-2024-shared-task) dividing it into train and dev sets.

The original dataset contains machine-readable questions and answers from Ukrainian External independent testing (called ЗНО/ZNO in Ukrainian).

The structure of the data is the following:
* `question`: the textual description of the questions;
* `answers`: possible answers to the questions with `marker` and `text`;
* `correct_answers`: the marker to the correct answer to the question;
* `subject`: the category of the questions.

Question subjects are:
* History of Ukraine
* Ukrainian language and literature

Overall, dataset contains of 3063 question/answers from 2006-2019 exams. Our division:

|        Splits        | History Subject  | Ukr Lang and Lit | Total |
|--------------------|------|------|------|
| Train   | 910 | 1540 | 2450 |
| Dev | 228 | 385 | 613 |

### Data License

MIT
