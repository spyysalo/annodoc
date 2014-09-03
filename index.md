---
layout: entry
title: Annodoc documentation
---

This is are an example of documentation created using the Annodoc
system. It serves a double purpose as *documentation* for the Annodoc
system and as a *template* that you can use as a starting point for
creating your own documentation using annodoc.

## Table of contents

* [What is Annodoc?](#what-is-annodoc)
* [How does it work?](#how-does-it-work)
* [Getting started](#getting-started)
* [Running locally](#running-locally)
* [Editing](#editing)
* [Adding documents](#adding-documents)
* [Configuration](#basic-configuration)
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

First, you need to get a copy of the Annodoc system. If you don't have
one already, head over to the [Annodoc repository] and download, clone
or fork the repository. TODO

## Running locally

**Please note**: the Annodoc system has been developed and tested in a
linux environment and has so far not been specifically tested on
Windows.  We strongly recommend a Unix or workalike system (OSX or
linux) for running the system locally.

For running Annodoc locally, you will need to have a recent version of
[Jekyll]. In particular, version 2.0 or greater is required for
[collection](#collections) features.

## Editing

Please note that for the "edit page" link to work, you will need to
set the value of the `editurl` variable in `_config.yml` (see
[configuration](#configuration)).

## Adding documents



## Collections

The following is a listing of pages in the "type" collection.  You can
find the source documents in the `_type` directory.

<ul>
{% for t in site.type %}
  <li><a href="{{ t.url | remove_first:'/' }}">{{ t.title }}</a>: {{ t.shortdef }}</li>
{% endfor %}
</ul>

## Configuration

Different aspects of the way a set of documentation is presented are
controlled by various configuration files and settings. The following
are the most important.

* `_config.yml`

The Jekyll top-level configuration file `_config.yml` controls many
aspects of the conversion of the source documents into the final site
as well as how Jekyll serves the site. This file also configures the
[collections](#collections) that are defined for the documentation.
Full documentation for `_config.yml` is available from
<http://jekyllrb.com/docs/configuration/>.

* `_includes/header.html`, `_includes/footer.html`

These HTML files are automatically attached to every page on the site.
Edit the HTML content of these two files to customize the look of the
documentation, add navigation, etc. These files are standard HTML.

* `css/main.css`, `css/style-vis.css`

The [CSS] files found in the `css` subdirectory control the style
(look) of the main documentation (`main.css`) and the visualizations
(`style-vis.css`). It is not necessary to modify these in basic
usage. If changes to the style of the documentation pages or the
visualization are needed, please refer to e.g.
<http://www.w3.org/Style/CSS/Overview.en.html> for more information.

* `lib/local/config.js`

This JavaScript file holds the configuration for the [brat]
visualization component. The configuration specifies, for example, the
colors, labels, label abbreviations, and line styles to use for
visualizing various categories of annotation. For documentation on the
contents and syntax of this file, refer to
<http://brat.nlplab.org/configuration.html>.

## Troubleshooting

The following sections provide instructions for troubleshooting
various possible issues with the system.

### Troubleshooting: basic visualization

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

### Troubleshooting: local usage

If you are having trouble running the system locally, please check
the following:

* Check that you have a recent version of Jekyll by running `jekyll -v`.
  Version 2.0 or greater is recommended.

Some debian-based linux distributions are currently shipping a dated
version of Jekyll. If you are using such a system, you may wish to
consider using `gem` instead of `apt-get` to install Jekyll (see e.g.
<http://jekyllrb.com/docs/installation/#install-with-rubygems>).

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
[Annodoc repository]: https://github.com/spyysalo/annodoc
[CSS]: http://en.wikipedia.org/wiki/Cascading_Style_Sheets