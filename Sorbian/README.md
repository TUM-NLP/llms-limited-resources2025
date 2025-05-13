# Dataset description for both Upper and Lower Sorbian

The resources in this repository have been provided by the WITAJ-Sprachzentrum for the shared task with a CC BY-NC-SA licence.
Each folder (`dsb` and `hsb`) contains two sub-folders for each task (`MT` and `QA`).
The files follow the same structure for both languages.

## Machine Translation

Each folder contains training (`train`) and development (`dev`) parallel corpora and monolingual sentences. It must be noted that parallel and monolingual sentences might contain some noisy sentences or sentence pairs.

For both Upper and Lower Sorbian, the training dataset is new compared to the one provided during the WMT 2022 Shared Task, while the development dataset is a combination of both old and new sentence pairs. 

The table below presents the number of sentences for each dataset:

|  | Upper Sorbian | Lower Sorbian |
|---|---|---|
| parallel train | 187,270 | 171,964 |
| parallel dev | 4,000 | 4,000 |
| monolingual | 47,758 (wiki) <br> 1,071,723 (witaj) | 120,501 |

Note: there are also a few overlapping sentence pairs for the training datasets in both languages compared to the 2022 edition.


## Question Answering

For both languages, the Question Answering datasets come from actual language certification exercises, with minimal format changes. 
We only release *development* datasets, which correspond to A1-B2 levels, as denoted in the file names. 
They are available in CSV and JSON formats (same content).

The dataset contains the following columns:
- `question_id`: the unique ID *per language* (e.g., `A1.1.H3`) composed of the level (e.g., A1), a source identifier (e.g., 1), a question type (e.g., H for listening, L for reading, and S for grammar exercises), and a question number (e.g., 3).
- `question_level`: the CEFR level of the question
- `context`: the context needed to answer the question, e.g., a text for reading comprehension or a dialogue transcription.
- `question`: the question to answer
- `possible_answers`: all the possible answers (each with a numeral and the actual answer; e.g., 1 pšawje
2 wopak) shown in the exercise; the number of answers depends on the exercise level and number.
- `correct_answer_num`: the numeral corresponding to the correct answer
- `question_type`: the ID for the question type (e.g., `listening_B2_3`) composed of the exercise type (e.g., listening comprehension), the exercise level (e.g., B2), and the number of the exercise (e.g., 3); this can help to understand the question types.

Here is a summary of the various question types:
- for the listening comprehension section, we provide the official transcription as context (e.g., a dialogue or a text which is read). The goal is to answer true or false questions (e.g., H2 questions for A1&A2 levels; H1 questions for B1&B2 levels) or multiple-choice questions (e.g., H3 questions for B1&B2)
- for the reading comprehension section, there are short and longer texts to read and corresponding multiple-choice questions to answer. In the B1&B2 levels, the first exercise (L1) is to find the most appropriate title for a given text.
- for the grammar section (only in the B1 and B2 levels), 12 blanks are present in the text and need to be filled with the correct word among all potential choices.

The number of questions *per language* is as follows (identical for both languages):
| level | A1 | A2 | B1 | B2 | total |
|---|---|---|---|---|---|
| N_questions | 30 | 28 | 44 | 56 | 158 |
