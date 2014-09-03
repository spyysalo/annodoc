---
layout: entry
title: Annodoc documentation and template
---

This is are an example of documentation created using the Annodoc
system. It serves a double purpose as *documentation* for the Annodoc
system and as a *template* that you can use as a starting point for
creating your own documentation using annodoc.

## Table of contents

* [What is Annodoc?](#what-is-annodoc)
* [How does it work?](#how-does-it-work)
* [Getting started](#getting-started)
* [Troubleshooting](#troubleshooting)

## What is Annodoc?

Annodoc is a documentation support system focusing in particular on
guidelines for text annotation. The system combines ease of editing
using a simple plain-text like format with support for the
visualization of complex, structured text annotation and close
integration with version control.

For example, consider the following fragment of documentation

<div class="documentation-example" markdown="1">
Mentions of person names are annotated as `PERSON`

~~~ ann
Barack Obama is the current president.
T1 PERSON 0 12 Barack Obama
~~~

<span style="float:right;font-size:75%;opacity:0.5">(Not seeing a visualization above? See <a href="#troubleshooting">troubleshooting</a>)</span>

</div>

this example is generated from the following input:

    Mentions of person names are annotated as `PERSON`

    ~~~ ann
    Barack Obama is the current president.
    T1 PERSON 0 12 Barack Obama
    ~~~

## How does it work?

The text content of Annodoc documents is in the simple [Markdown]
format (with the option to include HTML), and the data for the
visualizations is represented in any of a number of supported
annotation formats such as the [Stanford dependency], [CoNLL-X], or
[.ann standoff].

The final documents seen in the browser are a combination of (X)HTML
and [SVG] for the visualizations. The primary tools for generating the
final documents from the source are the [Jekyll] static web site
generator, which converts Markdown into (X)HTML, and the [brat]
annotation tool, which generates the SVG visualizations, with help
from some Annodoc-specific extensions.

The following figure shows the primary stages of processing.

<img style="width:100%" src="static/img/processing.png">

In addition to Markdown processing, Jekyll provides numerous other
features such as document collection management as well as templating
and simple scripting using the [Liquid] language, and Annodoc provides
various facilities for supporting guideline development such as
automatic linking of defined types.

Finally, to support the development and maintenance of complex sets of
documentation, Annodoc features close integration with the [Git]
distributed version control system through the [GitHub] web-based
hosting service, allowing automatic conversion and publication of the
most recent version of the online documentation each time the sources
are updated.

For more information on these technologies, please see the following:

* Jekyll: <http://jekyllrb.com/>
* brat: <http://brat.nlplab.org>
* Markdown: <http://daringfireball.net/projects/markdown/>
* Kramdown (Markdown superset): <http://kramdown.gettalong.org/>
* Liquid: <http://wiki.shopify.com/Liquid>
* Stanford Dependency format: <http://nlp.stanford.edu/software/stanford-dependencies.shtml>
* CoNLL-X format: <http://ilk.uvt.nl/conll/#dataformat>
* .ann standoff format: <http://brat.nlplab.org/standoff.html>
* Git: <http://git-scm.com/>
* GitHub: <http://github.com>

## Getting started

This is a dog.

## Collections

The following is a listing of pages in the "type" collection.  You can
find the source documents in the `_type` directory.

<ul>
{% for t in site.type %}
  <li><a href="{{ t.url | remove_first:'/' }}">{{ t.title }}</a>: {{ t.shortdef }}</li>
{% endfor %}
</ul>

## Troubleshooting

Are the annotation visualizations working? To check, see if the following
visualization and image look (broadly) similar.

Visualization:

~~~ ann
Barack Obama is the current president.
T1 PERSON 0 12 Barack Obama
~~~

Image:

<img src="static/img/visualization-example.png">

If yes, the basic visualization support is OK. If no (e.g.  if instead
of a visualization text such as `T1 PERSON 0 12 Barack Obama` is
shown), then try the following:

* Make sure you are using a supported browser. The visualizations
  require [SVG] support.  We recommend recent versions of Chrome or
  Safari. For IE, version 9 or newer is required.

* Check that JavaScript is enabled. The system requires JavaScript to
  generate the visualizations and will fail without it.

* Check the JavaScript console for errors. (The console is accessed in
  different ways depending on your browser.)

* Report the issue to the developers: email `sampo.pyysalo@gmail.com`

[Markdown]: http://daringfireball.net/projects/markdown/
[Stanford dependency]: http://nlp.stanford.edu/software/stanford-dependencies.shtml
[CoNLL-X]: http://ilk.uvt.nl/conll/#dataformat
[.ann standoff]: http://brat.nlplab.org/standoff.html
[SVG]: http://en.wikipedia.org/wiki/Scalable_Vector_Graphics
[Jekyll]: http://jekyllrb.com/
[brat]: http://brat.nlplab.org
[Liquid]: http://wiki.shopify.com/Liquid
[Git]: http://git-scm.com
[GitHub]: http://github.com
