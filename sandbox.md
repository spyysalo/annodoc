---
layout: entry
title:  'Sandbox'
---

# Sandbox

This file is intended as a "sandbox" for trying out the editing
features. Feel free to make changes by clicking the "edit page" link
at the top. (You need to be logged in to GitHub and have write
permissions to this GitHub repository for this to work.)

----------

# Some markdown

* bulleted
* list

1. numbered
2. list

Link: [link text](http://www.example.com)

# header 1

## header 2

### header 3

*italics* and **bold**

`inline code`

----------

# Some visualizations

~~~ sdparse
Just some tokens
~~~

~~~ sdparse
Tokens/Noun with/Adpos POS/Noun
~~~

~~~ sdparse
A dependency
det(dependency, A)
~~~

<div class="sd-parse">
Alternative syntax
</div>

<div class="sd-parse" tabs="yes">
Dynamic visualization (click "edit!")
</div>

<div class="conllx-parse" tabs="yes">
1   CoNLL-X   CoNLL-X   NNP   _    _    2    NMOD    _    _
2   example   example   NN    _    _    0    ROOT    _    _
</div>

<div class="conllu-parse" tabs="yes">
1   CoNLL-U   CoNLL-U   NNP   _    _    2    nmod    _    _
2   example   example   NN    _    _    0    root    _    _
</div>

<div class="conllu-parse" tabs="yes">
# sentence-label S1
1   CoNLL-U   CoNLL-U   NNP   _    _    2    nmod    _    _
2   example   example   NN    _    _    0    root    _    _
</div>

<div class="ann-annotation" tabs="yes">
.ann annotation example
</div>

~~~ sdparse
Parse with errors
det(no-such, token)
~~~

Right-to-left text (Hebrew, SD format)

~~~ sdparse
דני/NOUN ראה/VERB סרט/NOUN
nsubj(ראה, דני)
dobj(ראה, סרט)
~~~

Same sentence in CoNLL-U:

~~~ conllu
1     דני       _        NOUN    _      _     2      nsubj _ _
2     ראה       _        VERB    _      _     0      root  _ _
3     סרט       _        NOUN    _      _     2      dobj  _ _
~~~

Arabic (CoNLL-U):

~~~ conllu
1     وَ       _        NOUN    _      _     2      nsubj _ _
2     لاحَظَ       _        VERB    _      _     0      root  _ _
3     التَقْرِيرُ       _        NOUN    _      _     2      dobj  _ _
~~~

----------
