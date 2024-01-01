# [Gemini in Reasoning: Unveiling Commonsense in Multimodal Large Language Models](https://arxiv.org/abs/2312.17661)

This study conducts a thorough evaluation of Gemini Pro's efficacy in commonsense reasoning tasks, employing a diverse array of datasets that span both language-based and multimodal scenarios.

The official repository contains datasets, model descriptions, the full set of prompts used in experiments, and corresponding experimental results.

## Datasets
We experiment with 12 datasets related to different types of commonsense reasoning, which include 11 language-based datasets and one multimodal dataset. For evaluation purposes, we utilize the validation set corresponding to each task. The following figure provides an overview of the datasets, as well as example questions.

<div align="center">
    <img width="75%" alt="image" src="https://github.com/EternityYW/Gemini-Commonsense-Evaluation/blob/main/image_sources/datasets_overview.png">
</div>

All datasets used for experiments can be downloaded in the "[./datasets](./datasets/)" folder except VCR (Visual Commonsense Reasoning), which can be accessed through [here](https://visualcommonsense.com/download/).

## Models

We consider four popular LLMs for language-based dataset evaluation, including the opensource model [Llama-2-70b-chat](https://arxiv.org/abs/2307.09288), as well as the closed-source models [Gemini Pro](https://arxiv.org/abs/2312.11805), GPT-3.5 Turbo, and [GPT-4
Turbo](https://arxiv.org/abs/2303.08774). Specifically, we query Gemini through Google Vertex AI, the GPT models through the OpenAI API, and Llama2 through DeepInfra. 

For the multimodal dataset, we consider GPT-4V (gpt-4-vision-preview in API) and Gemini Pro Vision (gemini-pro-vision in API) in our experiments.

For all models, we apply greedy decoding (i.e., temperature = 0) for response generation.

## Prompts 

We evaluate language-based datasets using two prompting settings: (1) zero-shot standard prompting, which measures the models' inherent commonsense capabilities in linguistic contexts, and (2) few-shot chain-of-thought (CoT) prompting, designed to observe potential improvements in the models' performance. For the multimodal dataset, we employ zero-shot standard prompting to assess the genuine end-to-end visual commonsense reasoning abilities of multimodal large language models. The full set of prompts is available in the "[./results](./results/)" folder, where each .csv file contains 0shot_SP and 5shot_CoT, representing (1) and (2) respectively. In the multimodal VCR dataset, only 0shot_SP is used, in accordance with our setup.

## Experimental Results
The experimental results for each dataset can be found in "[./results](./results/)".

Please refer to our full [paper](https://arxiv.org/pdf/2312.17661.pdf) for more details. 

## Key Findings

(1) Overall, Gemini Pro’s performance is comparable to that of GPT-3.5 Turbo, demonstrating marginally better average results across 11 language datasets (1.4% higher accuracy), though it lags behind GPT-4 Turbo by an average of 8.2% in accuracy. Moreover, Gemini Pro Vision exhibits lower performance than GPT-4V on the multimodal dataset, except for temporal-related questions. 

(2) Approximately 65.8% of Gemini Pro’s reasoning processes are evaluated as logically sound and contextually relevant, indicating its potential for effective application in various domains. 

(3) Gemini Pro encounters significant challenges in temporal and social commonsense reasoning, indicating key areas for further development. 

(4) Our manual error analysis reveals that Gemini Pro often misunderstands provided contextual information, accounting for 30.2% of its total errors. Furthermore, Gemini Pro Vision struggles particularly with identifying emotional stimuli in images, especially those involving human entities, which constitutes 32.6% of
its total errors.

