---
name: NudeNet
tools: [Keras, Python]
image: /images/nudenet_example.png
description: An ensemble of Neural Nets for Nudity Detection and Censoring
---

# DeepPunct

<!-- Place this tag where you want the button to render. -->
<!-- Place this tag in your head or just before your close body tag. -->
<script async defer src="https://buttons.github.io/buttons.js"></script>

<a class="github-button" href="https://github.com/bedapudi6788" data-size="large" data-show-count="true" aria-label="Follow @bedapudi6788 on GitHub">Follow @bedapudi6788</a>
<a class="github-button" href="https://github.com/bedapudi6788/nudenet" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star bedapudi6788/nudenet on GitHub">Star</a>
<a class="github-button" href="https://github.com/bedapudi6788/nudenet/fork" data-icon="octicon-repo-forked" data-size="large" data-show-count="true" aria-label="Fork bedapudi6788/nudenet on GitHub">Fork</a>

Pre-trained Classification and Detection models for nudity detection and censoring.

![](/images/nudenet_example.png)

![](/images/nudenet_scores.png)

Classification scores on the data available [here.](https://dataturks.com/projects/Mohan/NSFW(Nudity%20Detection)%20Image%20Moderation%20Datatset)




# Installation
```
# Install tensorflow or tensorflow-gpu separately
pip install nudenet
```

# Usage
```
# if you are using gpu for prediction, please see https://stackoverflow.com/questions/34199233/how-to-prevent-tensorflow-from-allocating-the-totality-of-a-gpu-memory for restricting memory usage

from nudenet import NudeClassifier
classifier = NudeClassifier('classifier_checkpoint_path')
classifier.classify('path_to_nude_image')
# {'path_to_nude_image': {'safe': 5.8822202e-08, 'nude': 1.0}}

from nudenet import NudeDetector
detector = NudeDetector('detector_checkpoint_path')

# Performing detection
detector.detect('path_to_nude_image')
# [{'box': [352, 688, 550, 858], 'score': 0.9603578, 'label': 'BELLY'}, {'box': [507, 896, 586, 1055], 'score': 0.94103414, 'label': 'F_GENITALIA'}, {'box': [221, 467, 552, 650], 'score': 0.8011624, 'label': 'F_BREAST'}, {'box': [359, 464, 543, 626], 'score': 0.6324697, 'label': 'F_BREAST'}]

# Censoring an image
detector.censor('path_to_nude_image', out_path='censored_image_path', visualize=False)
```

The pre-trained models are available [here.](https://github.com/bedapudi6788/nudenet-models)

<p class="text-center">
{% include button.html link="https://github.com/bedapudi6788/nudenet" text="Learn More" %}
</p>
