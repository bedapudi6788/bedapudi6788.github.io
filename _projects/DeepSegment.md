---
name: DeepSegment
tools: [Tensorflow, LSTM, Python]
image: /images/deepsegment_accuracy.png
description: Designed with ASR outputs in mind, DeepSegment uses BiLSTM + CRF for automatic sentence boundary detection. It significantly outperforms the standard libraries (spacy, nltk, corenlp ..) on imperfect text and performs similarly for perfectly punctuated text.
---

# DeepSegment

<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-147985030-1"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-147985030-1');
</script>


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
pip install deepsegment
```

# Usage
```
from deepsegment import DeepSegment
# The default language is 'en'

# english (en), french (fr), italian (it) are supported as of now

segmenter = DeepSegment('en')

segmenter.segment('I am Batman i live in gotham')
# ['I am Batman', 'i live in gotham']
```

```
# Using with tfserving docker image
docker pull bedapudi6788/deepsegment_en:v2
docker run -d -p 8500:8500 bedapudi6788/deepsegment_en:v2

from deepsegment import DeepSegment

# The default language is 'en'

segmenter = DeepSegment('en', tf_serving=True)

segmenter.segment('I am Batman i live in gotham')
# ['I am Batman', 'i live in gotham']
```


<p class="text-center">
{% include button.html link="https://github.com/bedapudi6788/deepsegment" text="Learn More" %}
</p>
