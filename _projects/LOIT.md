---
name: LOIT
tools: [DataSet, Twitter, Telugu, Hindi]
image: /images/LOIT.png
description: Lot Of Indic Tweets dataset and corresponding pre-trained models.
---

# LOIT

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
<a class="github-button" href="https://github.com/bedapudi6788/LOIT" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star bedapudi6788/LOIT on GitHub">Star</a>
<a class="github-button" href="https://github.com/bedapudi6788/LOIT/fork" data-icon="octicon-repo-forked" data-size="large" data-show-count="true" aria-label="Fork bedapudi6788/LOIT on GitHub">Fork</a>

<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">


This dataset contains 79,45,718 (7.9 million) Telugu tweets and 1,76,54,722 (17.6 million) Hindi tweets.

Telugu: LOIT contains most (>85%) of the Telugu tweets made between 2010–01–01 and 2019–06–25. Of these, 73,78,582 are tweets with unique text.

Hindi: LOIT contains most of the Hindi tweets made between 2017–01–13 and 2018–12–31. Of these, 1,58,07,840 are tweets with unique text.

# Installation
```
# Install tensorflow or tensorflow-gpu separately
pip install loit
```

# Usage
```
import loit

# download data
# hindi and telugu are available as of now
loit.download('hindi', 'data')

# download fasttext cbow vectors and read them 
loit.load_vectors('hindi', 'cbow')

# download fasttext skipgram vectors and read them
loit.load_vectors('hindi', 'skipgram')

# read the jsons from data
#returns iterator that yields jsons
it = loit.read_data('telugu')

for tweet_json in it:
    print(tweet_json['tweet'])
    input()

```


<p class="text-center">
{% include button.html link="https://github.com/bedapudi6788/LOIT" text="Learn More" %}
</p>
