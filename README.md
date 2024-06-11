# Farsi Named Entity Recognition (NER) Datasets Collection

This repository contains a collection of datasets that are widely used for Named Entity Recognition (NER) tasks in Farsi (Persian). NER is a crucial component in Natural Language Processing (NLP) that involves identifying and classifying entities in text into predefined categories such as names of persons, organizations, locations, expressions of times, quantities, monetary values, percentages, etc.


## Datasets Overview

This section provides a brief overview of each dataset, including the source, the type of entities annotated, and the size of the dataset.

| Dataset Name | Source | Entity Types | Size | Description | F1 Measure |
|--------------|--------|--------------|------|-------------| ---------- |
| **ArmanPersoNERCorpus** | [LINK](https://raw.githubusercontent.com/HaniehP/PersianNER/master/ArmanPersoNERCorpus.zip) | PER, ORG, LOC,FAC, PRO, EVENT | 250,015 tokens | NERtags are in IOB format. | %84/23
| **PersianNer** | [LINK](https://github.com/Text-Mining/Persian-NER) | PER, ORG, LOC, EVE, DATE | 25milion tokens | NERtags are in IOB format. | ---
| **PEYMA** | [LINK](https://drive.google.com/uc?id=1EC121uhkOFlsPAvsPMJ9TvBAwus_UkhN) | DAT, ORG, PER, TIM, MON | 302,530 tokens | NERtags are in IOB format. | %84
| **ParsNER-Social** | [LINK](https://github.com/majidasgari/ParsNER/tree/master/persian/) | PERS, LOC, ORG, MISC | 205,373 tokens | Constructed from the social media. | %89/65

## How to Use

To use these datasets, you can download them from their respective sources and load them using common NLP libraries. Here’s an example using HuggingFace's `transformers` library:

Example in Python:

```python
from transformers import AutoTokenizer, AutoModelForTokenClassification
from transformers import pipeline

# Load a pre-trained model for Persian NER
model_name = "HooshvareLab/bert-fa-zwnj-base-ner"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForTokenClassification.from_pretrained(model_name)

nlp = pipeline("ner", model=model, tokenizer=tokenizer)
text = "علی دایی در تیم پرسپولیس بازی می‌کرد."
entities = nlp(text)

for entity in entities:
    print(entity)
