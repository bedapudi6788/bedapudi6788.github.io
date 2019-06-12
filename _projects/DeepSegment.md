---
name: DeepSegment
tools: [Tensorflow, LSTM, Python]
image: /images/deepsegment_accuracy.png
description: Designed with ASR outputs in mind, DeepSegment uses BiLSTM + CRF for automatic sentence boundary detection. It significantly outperforms the standard libraries (spacy, nltk, corenlp ..) on imperfect text and performs similarly for perfectly punctuated text.
---

# DeepSegment

<!-- Place this tag where you want the button to render. -->
<!-- Place this tag in your head or just before your close body tag. -->
<script async defer src="https://buttons.github.io/buttons.js"></script>

<a class="github-button" href="https://github.com/bedapudi6788" data-size="large" data-show-count="true" aria-label="Follow @bedapudi6788 on GitHub">Follow @bedapudi6788</a>
<a class="github-button" href="https://github.com/bedapudi6788/deepsegment" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star bedapudi6788/deepsegment on GitHub">Star</a>
<a class="github-button" href="https://github.com/bedapudi6788/deepsegment/fork" data-icon="octicon-repo-forked" data-size="large" data-show-count="true" aria-label="Fork bedapudi6788/deepsegment on GitHub">Fork</a>

Designed with ASR outputs in mind, DeepSegment uses BiLSTM + CRF for automatic sentence boundary detection. It significantly outperforms the standard libraries (spacy, nltk, corenlp ..) on imperfect text and performs similarly for perfectly punctuated text.

For the completely unpunctuated test case, the absolute accuracy is 52.637 and the F1 score is 91.33 (precision: 93.242, recall: 89.506).

![](/images/deepsegment_accuracy.png)



<!-- DeepSegment (slightly modified version) performance on English and French tasks of FinSBD 2019 

![](/images/finnlp_eng.png) ![](/images/finnlp_fra.png) -->


# Installation
```
# Install tensorflow or tensorflow-gpu separately
# Tested with tf and tf-gpu version 1.3.0 to 1.10.0
pip install deepsegment
```

# Usage
```
# if you are using gpu for prediction, please see https://stackoverflow.com/questions/34199233/how-to-prevent-tensorflow-from-allocating-the-totality-of-a-gpu-memory for restricting memory usage

from deepsegment import DeepSegment
# the config file can be found at in the pre-trained model zip. Change the model paths in the config file before loading. 
# Since the complete glove embeddings are not needed for predictions, "glove_path" can be left empty in config file

segmenter = DeepSegment('path_to_config')
segmenter.segment('I am Batman i live in gotham')
['I am Batman', 'i live in gotham']
```

The pre-trained models are available [here.](https://github.com/bedapudi6788/DeepSegment-Models)

<p class="text-center">
{% include button.html link="https://github.com/bedapudi6788/deepsegment" text="Learn More" %}
</p>