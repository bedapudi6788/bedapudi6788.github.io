---
name: txt2txt
tools: [Keras, seq2seq, Python, Attention]
image: /images/txt2txt.png
description: An extremely easy to use and very configurable seq2seq implementation with Attention for text to text use cases.
---

# txt2txt

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
<a class="github-button" href="https://github.com/bedapudi6788/txt2txt" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star bedapudi6788/txt2txt on GitHub">Star</a>
<a class="github-button" href="https://github.com/bedapudi6788/txt2txt/fork" data-icon="octicon-repo-forked" data-size="large" data-show-count="true" aria-label="Fork bedapudi6788/txt2txt on GitHub">Fork</a>

<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">


An extremely easy to use and very configurable seq2seq implementation with Attention for text to text use cases.

Working with seq2seq tasks in NLP, I realised there aren't any easy to use, simple to understand and good performing libraries available for this. Though libraries like FairSeq or transformer are available they are in general either too complex for a newbie to understand or most probably overkill (and are very tough to train) for simple projects.

This module provides pre-built seq2seq model with Attention that performs excellently on most of the "simple" NLP taks. (Tested with Punctuation correction, transliteration and spell correction).

# Examples
1. [Adding two numbers](https://colab.research.google.com/drive/11lVvfa2EGYQ0y3O5gA--01iR0J6IRMCk)
2. [More Complex Math and fit_generator](https://colab.research.google.com/drive/1JqBxRiTZ0D1rB3bsw46FaA1McTqrDGCe)


![](/images/txt2txt.png)



# Installation
```
# Install tensorflow or tensorflow-gpu separately
pip install txt2txt
```

# Usage
```
# Training a model
from txt2txt import build_params, build_model, convert_training_data

input_data = ['123', '213', '312', '321', '132', '231']
output_data = ['123', '123', '123', '123', '123', '123']

build_params(input_data = input_data, output_data = output_data, params_path = 'params', max_lenghts=(10, 10))
    
model, params = build_model(params_path='params')

input_data, output_data = convert_training_data(input_data, output_data, params)
    
checkpoint = ModelCheckpoint('checkpoint', monitor='val_acc', verbose=1, save_best_only=True, mode='max')
callbacks_list = [checkpoint]

model.fit(input_data, output_data, validation_data=(input_data, output_data), batch_size=2, epochs=20, callbacks=callbacks_list)

# Inference (Beam)
from txt2txt import build_model, infer
model, params = build_model(params_path='params')
model.load_weights('path_to_checkpoint_file')
infer(input_text, model, params)
```


<p class="text-center">
{% include button.html link="https://github.com/bedapudi6788/txt2txt" text="Learn More" %}
</p>
