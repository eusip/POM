## Table of Contents <!-- omit in toc -->
- [Overview](#overview)
  - [Level 2: Features](#level-2-features)
  - [Level 2: Video labels](#level-2-video-labels)
  - [Level 2: Words](#level-2-words)
  - [Level 3: Expression level dialogue labels](#level-3-expression-level-dialogue-labels)
  - [Considerations](#considerations)
  - [Download Link](#download-link)
  - [Contact Information](#contact-information)
  - [Citation information](#citation-information)

## Overview

This fine-grain annotated POM dataset was produced for opinion mining. It includes opinion annotations at the sentence, expression and token levels. Further details can be found in ([Garcia et al. 2019 (1)](https://arxiv.org/abs/1902.10102)). As part of preprocessing, punctuation was added to the original POM text corpus. The dataset is stored as a pickled pandas [MultiIndex DataFrame](https://pandas.pydata.org/pandas-docs/stable/user_guide/advanced.html#hierarchical-indexing-multiindex).

The hierarchical structure can be understood according to the array which forms the MultiIndex. The first element of the index is one of the following values: 'level_0', 'features', 'labels', 'words' or 'seq_level_labels_lvl1'.

The value 'level_0' provides a MultiIndex Series containing the following tuple of labels: ['index_text', 'id_sentence', 'level_1'] where 'index_text' indexes the raw filename for each movie review, 'id_sentence' indexes the sentences in the review, and 'level_1' indexes each word in each sentence. This MultiIndex Series indexes the rows of each of the following Dataframes.

### Level 2: Features

Dataset features (columns) are indexed according to the tuple ('features', [feature name], dimension) where the number of dimensions count the number of columns that comprise a particular feature.

| feature name          | feature type          | dimensions |
| --------------------- | --------------------- | ---------- |
| feature_COAVAREP      | audio                 | 43         |
| feature_FACET 4.1     | video                 | 43         |
| feature_FACET 4.2     | video                 | 36         |
| feature_glove_vectors | text                  | 300        |
| intervals             | word start, word stop | 2          |


### Level 2: Video labels

Dataset video labels (columns) are indexed according to the tuple ('labels', [label name], dimension) where the number of dimensions counts the number of columns that comprise a particular label.

| label name              | dimensions |
| ----------------------- | ---------- |
| label_video_personality | 16         |
| label_video_persuasion  | 1          |
| label_video_sentiment   | 1          |

### Level 2: Words

Dataset words (columns) are indexed according to the tuple ('words', 'feature_words').

### Level 3: Expression level dialogue labels

Expression level dialogue labels are indexed according to the tuple ('seq_level_labels_lvl1', 'seq_level_labels_lvl2', [predefined target]).

| predefined target                     |
| ------------------------------------- |
| 4_levels_polarity                     |
| Actor                                 |
| Atmosphere and mood                   |
| Character design                      |
| Composer - Singer - Soundmaker        |
| Director                              |
| Music and Sound effects               |
| Negative                              |
| Negative_levels                       |
| Neutral                               |
| Other                                 |
| Other people involved in movie making |
| Overall                               |
| Polarity                              |
| Positive                              |
| Positive_levels                       |
| Price                                 |
| Producer                              |
| Screenplay                            |
| Target                                |
| Token                                 |
| Very\\\\_Negative                     |
| Very\\\\_Positive                     |
| Vision and Special effect             |

### Considerations

Researcher should keep in mind that this dataset differs from the original POM dataset due to the follow data process:

1. Annotators did not take into account the video portion of the dataset during annotation. Only the transcripts of each review were considered.
2. While the original dataset contained punctuation (e.g. silent pauses), this dataset does not contain punctuation and only provides sentence segmentation. This could be of significant importance for those who want to use certain audio features from the CMU SDK -- such as pause ([Park et al. 2014](https://dl.acm.org/doi/pdf/10.1145/2663204.2663260)).
3. Because punctation has been removed the Levenshtein distance was used in order to re-match the annotated transcripts with the transcripts of the original dataset.
4. Finally the annotated transcripts were re-integrated with the remaining features in the original POM dataset.

### Download Link

The dataset is available for download through registration at the following link: 

http://service.tsi.telecom-paristech.fr/cgi-bin/user-service/subscribe.cgi?form=&license=1&ident=POM

If prompted to sign in simply click 'Cancel' in order to navigate to the registration page.

### Contact Information

Please direction any questions or concerns regarding this dataset to Tanvi Dinkar (tanvi.dinkar@telecom-paris.fr) or Ebenge Usip (ebenge.usip@telecom-paris.fr).

### Citation information

```
@article{garcia2019multimodal,
  title={A multimodal movie review corpus for fine-grained opinion mining},
  author={Garcia, Alexandre and Essid, Slim and d'Alch{\'e}-Buc, Florence and Clavel, Chlo{\'e}},
  journal={arXiv preprint arXiv:1902.10102},
  year={2019}
}

@article{garcia2019token,
  title={From the token to the review: A hierarchical multimodal approach to opinion mining},
  author={Garcia, Alexandre and Colombo, Pierre and Essid, Slim and d'Alch{\'e}-Buc, Florence and Clavel, Chlo{\'e}},
  journal={arXiv preprint arXiv:1908.11216},
  year={2019}
}

@inproceedings{park2014computational,
  title={Computational analysis of persuasiveness in social multimedia: A novel dataset and multimodal prediction approach},
  author={Park, Sunghyun and Shim, Han Suk and Chatterjee, Moitreya and Sagae, Kenji and Morency, Louis-Philippe},
  booktitle={Proceedings of the 16th International Conference on Multimodal Interaction},
  pages={50--57},
  year={2014}
}
```






