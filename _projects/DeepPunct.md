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
      text: query
    };
    console.log(JSON.stringify(payload, undefined, 2))
    axios.post('http://ai.bpraneeth.com/deep-segment_punct', payload)
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

window.onload = function() {
    console.log( "ready!" );
    $('#loader').hide();
};

</script>

<input type="text" class="form-control" id="queryInput" placeholder="DeepSegment + DeepPunct demo. Input limit: 600 characters.">
<div id="loader"></div>

<button class="btn btn-primary" type="button" onclick="parseQuery()">Submit</button>
<div class="col-sm-12"> <pre id='resultJSON'></pre> </div>




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
