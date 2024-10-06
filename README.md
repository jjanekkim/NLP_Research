# NLP Research

## Overview

This repository is dedicated to researching and exploring transfer learning models in Natural Language Processing (NLP). The key topics covered in this research include Named Entity Recognition (NER), Relevance, Prompt Leakage, and Grammar.

The data for this project was collected using Copilot. I generated chat data by engaging in conversations on various topics, including Greek mythology, travel, tech recommendations, and more.

## Research Topics

### Named Entity Recognition

For Named Entity Recognition (NER), spaCy and Flair models are compared. For spaCy, I experimented with the 'en_core_web_sm', 'en_core_web_lg', and 'en_core_web_trf' models. The accuracy evaluation for each model can be found in the [spaCy documentation](https://spacy.io/models/en#en_core_web_sm).

|Model|F-score|
|------------|--------|
|en_core_web_sm|0.84|
|en_core_web_lg|0.86|
|en_core_web_trf|0.90|
|Flair (default)|0.93|

After testing with transfer learning, spaCy's 'en_core_web_trf' model proved to be the most accurate for Named Entity Recognition (NER). While spaCy is generally faster and more precise, Flair also demonstrated strong accuracy compared to spaCy’s 'en_core_web_sm' and 'en_core_web_lg' models. However, Flair's processing speed was significantly slower, taking several minutes to produce results, whereas spaCy models generated output in just a few seconds.

For both speed and accuracy, spaCy's 'en_core_web_trf' is the best choice. One issue with the other two spaCy models was their tendency to misclassify unknown names as miscellaneous entities, organizations, or people, leading to inaccuracies. In contrast, 'en_core_web_trf' handled these cases more accurately.

*Note: The 'en_core_web_trf' model could not run on a local machine and was instead executed using Google Colab.*

### Relevance

Overall, detecting relevance in this NLP research proved challenging due to the significant length discrepancy between the user's (myself) short questions and the chatbot's (Copilot) lengthy responses. Initially, TF-IDF was used to calculate relevance scores, but the results averaged around 0.19. To establish a baseline, we re-tested by mixing questions and answers. The average relevance score for the mixed chats was 0.079, showing only a slight difference from the original score, where questions and answers were not mixed.

![image](https://github.com/user-attachments/assets/a43b231b-fce4-40d2-845b-4ef4830c12b1)

Although CountVectorizer wasn't originally intended for relevance detection, I experimented with it to explore how it would handle the large disparity in length between the user's input and the chatbot's output. However, it also failed to provide a significant difference: the original data's average score was 0.28, while the mixed data averaged 0.13.

To further improve relevance detection, exploring models like Word2Vec and GloVe could provide better results.

### Prompt Leakage

This aspect of the research was particularly challenging due to the inability to inject a prompt into the chatbot.

### Grammar

In this part of the research, the language_tool_python library was used to detect grammar errors in the debate between 2024 presidential candidates Kamala Harris and Donald Trump.

|Candidate|Min|Max|Median|Average|
|-------|-----|---|---|---|
|Kamala Harris|0|7|2|3.14|
|Donald Trump|0|17|5.5|6.57|

For a more interesting analysis of the presidential debate, please refer to the [presidential-debate2024 repository](https://github.com/jjanekkim/presidential-debate2024).
