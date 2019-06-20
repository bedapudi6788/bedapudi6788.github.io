---
name: NudeNet
tools: [Keras, Python]
image: /images/nudenet_example.png
description: An ensemble of Neural Nets for Nudity Detection and Censoring
---

# NudeNet

<!-- Place this tag where you want the button to render. -->
<!-- Place this tag in your head or just before your close body tag. -->
<script async defer src="https://buttons.github.io/buttons.js"></script>

<a class="github-button" href="https://github.com/bedapudi6788" data-size="large" data-show-count="true" aria-label="Follow @bedapudi6788 on GitHub">Follow @bedapudi6788</a>
<a class="github-button" href="https://github.com/bedapudi6788/nudenet" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star bedapudi6788/nudenet on GitHub">Star</a>
<a class="github-button" href="https://github.com/bedapudi6788/nudenet/fork" data-icon="octicon-repo-forked" data-size="large" data-show-count="true" aria-label="Fork bedapudi6788/nudenet on GitHub">Fork</a>

<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">

<style>
  #resultJSON:empty {display: none}

  #loader {
    border: 5px solid #f3f3f3;
    border-radius: 50%;
    border-top: 5px solid #1e93e0;
    width: 40px;
    height: 40px;
    position: absolute;
    top: 20%;
    left: 50%;
    -webkit-animation: spin 1s linear infinite;
    /* Safari */
    animation: spin 1s linear infinite;
  }

  /* Safari */

  @-webkit-keyframes spin {
    0% {
      -webkit-transform: rotate(0deg);
    }
    100% {
      -webkit-transform: rotate(360deg);
    }
  }

  @keyframes spin {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
</style>

<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
<script>
  function parseQuery(e) {
    query = $('#queryInput').val();
    $('#loader').show();

    let payload = {
      url: query
    };
    console.log(JSON.stringify(payload, undefined, 2))
    axios.post('http://ai.bpraneeth.com/nudenet_classifier_url', payload)
    .then((response) => {
      if (!response || !response.data) {
        console.error('Server Error! Please try again');
        $('#loader').hide();
        return;
      }
      $('#loader').hide();
      console.log(JSON.stringify(response.data, undefined, 2))
      processResponse(response.data);
    })
    .catch((err) => {
      $('#loader').hide();
      console.error(err);
    })
  }

function processResponse(data) {
    $('#resultJSON').html('<h4>Result:</h4><br>' + JSON.stringify(data, undefined, 2));
  }

$(document).ready(function() {
    console.log( "ready!" );
    $('#loader').hide();
});

</script>

<input type="text" class="form-control" id="queryInput" placeholder="Classification Demo: Enter image file direct URL">
<div id="loader"></div>

<button class="btn btn-primary" type="button" onclick="parseQuery()">Submit</button>
<div class="col-sm-12"> <pre id='resultJSON'></pre> </div>



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
