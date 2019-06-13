---
name: DeepPunct
tools: [Keras, LSTM, Python, Attention]
image: /images/deeppunct_example.png
description: Designed with ASR outputs in mind, DeepPunct uses LSTM encoder and decoders with Luong attention for automatic punctuation restoration.
---

# DeepPunct

<!-- Place this tag where you want the button to render. -->
<!-- Place this tag in your head or just before your close body tag. -->
<script async defer src="https://buttons.github.io/buttons.js"></script>

<a class="github-button" href="https://github.com/bedapudi6788" data-size="large" data-show-count="true" aria-label="Follow @bedapudi6788 on GitHub">Follow @bedapudi6788</a>
<a class="github-button" href="https://github.com/bedapudi6788/deepcorrect" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star bedapudi6788/deepcorrect on GitHub">Star</a>
<a class="github-button" href="https://github.com/bedapudi6788/deepcorrect/fork" data-icon="octicon-repo-forked" data-size="large" data-show-count="true" aria-label="Fork bedapudi6788/deepcorrect on GitHub">Fork</a>

Designed with ASR outputs in mind, DeepPunct uses LSTM encoder and decoders with Luong attention for automatic punctuation restoration.

![](/images/deeppunct_example.png)



# Installation
```
# Install tensorflow or tensorflow-gpu separately
pip install deepcorrect
```

# Usage
```
# if you are using gpu for prediction, please see https://stackoverflow.com/questions/34199233/how-to-prevent-tensorflow-from-allocating-the-totality-of-a-gpu-memory for restricting memory usage

from deepcorrect import DeepCorrect
corrector = DeepCorrect('params_path', 'checkpoint_path')
corrector.correct('how are you')
# How are you?
```

The pre-trained models are available [here.](https://drive.google.com/open?id=1Yd8cJaqfQkrJMbRVWIWtuyo4obTDYu-e)

<p class="text-center">
{% include button.html link="https://github.com/bedapudi6788/deepcorrect" text="Learn More" %}
</p>
