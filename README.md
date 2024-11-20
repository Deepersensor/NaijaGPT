---
language:
- en
- yo
- ha
- ig
license: mit
size_categories:
- 100K<n<1M
task_categories:
- text-generation
dataset_info:
  features:
  - name: text
    dtype: string
  - name: link
    dtype: string
  - name: token_count
    dtype: int64
  - name: section
    dtype: string
  - name: int_score
    dtype: int64
  - name: language
    dtype: string
  - name: language_probability
    dtype: float64
  splits:
  - name: train
    num_bytes: 1094515650
    num_examples: 270137
  download_size: 648541168
  dataset_size: 1094515650
configs:
- config_name: default
  data_files:
  - split: train
    path: data/train-*
tags:
- finance
- legal
- music
- art
- medical
- chemistry
- biology
---
# Naijaweb Dataset 🇳🇬


**Naijaweb** is a dataset that contains over **270,000+ documents**, totaling approximately **230 million GPT-2 tokens**. The data was web scraped from web pages popular among Nigerians, providing a rich resource for modeling Nigerian linguistic and cultural contexts.

## Dataset Summary

| Features       | Data Types  |
|----------------|-------------|
| text           | string      |
| link           | string      |
| token_count    | int64       |
| section        | string      |
| int_score      | int64       |
| language       | string      |
| language_probability | float64 |

## Data Collection

The dataset was collected from **Nairaland.com**, extracting **about 30 million unique posts** from 19 different sections of the site. Additionally, **1,289,195 outbound links** were extracted from these posts. The content of these web pages was extracted using **Trafilatura**, a popular library for web scraping and content extraction.
The full data collection can be found [in this repo](https://github.com/saheedniyi02/Naijaweb), kindly give a star⭐
## Data Cleaning

The cleaning process was conducted using **[Datatrove](https://github.com/huggingface/datatrove)**, the same library employed in cleaning the **[FineWeb](https://huggingface.co/datasets/HuggingFaceFW/fineweb)** dataset, which is known for its high quality. The data cleaning process involved multiple stages of deduplication, filtering, and normalization to ensure the dataset's quality matches that of other high-performing datasets.

### Data Cleaning Procedure:
- **URL Filtering** 
- **Repitition and quality filtering:**
- **Personal Identifiable Information (PII) Removal** 

## Example Entry

Each data point contains the following fields:
- `text`: the main body of the post or web page
- `link`: the original URL of the source content
- `token_count`: the number of GPT2 tokens in the `text` field
- `section`: the Nairaland section where the post was found
- `int_score`: an integer representation of the 'educational quality'  of the data based on [fineweb's webpage educational classifier](https://huggingface.co/HuggingFaceFW/fineweb-edu-classifier)
- `language`: detected language of the text (e.g., `en`, `yo`, `ha`, `ig`)
- `language_probability`: the confidence score of the language detection algorithm

An example looks as follows:
```
{
'text': 'Governor Samuel Ortom of Benue State\nBy Peter Duru\nGovernor Samuel Ortom of Benue state has commended President Muhammadu Buhari for his directive to security agents to shoot anyone illegally bearing AK47 rifle in the country.\nThe Governor who gave the commendation Thursday in Makurdi said the President’s order would reduce the level of criminality, banditry and militia herders’ attacks on Benue communities as well as in other parts of the country.\nAccording to him, “the order would also make the communities safer for displaced farmers to return to their ancestral homes.\n“I wish to commend Mr. President for his recent order against those bearing AK47 rifles. This I am sure will reduce the high rate of criminality, banditary and militia herdsmen attacks on our farming communities,” the Governor said.\nHe noted that President Buhari had done the right thing by listening to the calls he and other concerned Nigerians made on the need for the Federal Government to act faster and decisively to save the country from degenerating to a state of anarchy.\n“I don’t only criticise, I also commend where necessary. And I want to say shame on those sycophants who were bashing me for writing to Mr. President because he has finally heeded my advice,” he added.\nGovernor Ortom said Nigeria belonged to all its citizens and only justice and equity anchored on the rule of law could guarantee the unity and stability of the country.\nComments expressed here do not reflect the opinions of Vanguard newspapers or any employee thereof.',
 'link': 'https://www.vanguardngr.com/2021/03/ortom-commends-buhari-on-shoot-at-sight-order-on-ak47-bearing-criminals/amp/',
 'token_count': 332,
 'section': 'Politics',
 'int_score': 1,
 'language': 'en',
 'language_probability': 0.9999465942382812
}
```

## Data Splits

- **Training Split:** 270,137 examples (620MB in size)

## How to Load the Dataset

To load the dataset using Hugging Face's `datasets` library:

```python
from datasets import load_dataset

dataset = load_dataset("saheedniyi/naijaweb")
```

## Social Impact

Naijaweb was created to make Nigerian web data more accessible, providing researchers and developers with a dataset rich in Nigerian contexts across various domains such as **Politics**, **Education**, **Business**, and **Health**.

## Bias and Ethical Considerations

Since the data is collected from publicly available web pages, inherent biases present in the sources may be reflected in the dataset. These biases can manifest in areas such as **language**, **ideology**, or **topic representation**. Users should be mindful of these potential biases when developing models, especially for sensitive areas like **legal** or **medical** information.

## Sections of the Dataset

The dataset comprises content from 19 different sections of **Nairaland.com**, covering topics such as **Politics**, **Education**, **Business**, and **Health**.

Citation
If you use the Naijaweb dataset in your research, please cite it as follows:
```

@dataset{naijaweb_2024,
  author    = {Saheed Azeez},
  title     = {Naijaweb: A Web Scraped Nigerian Context Dataset},
  year      = {2024},
  publisher = {Hugging Face Datasets},
  version   = {1.0.0},
  url       = {https://huggingface.co/datasets/saheedniyi/naijaweb},
}
```