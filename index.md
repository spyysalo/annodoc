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
* [Visualizations](#visualizations)
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
one already, head over to the online [Annodoc repository] and
download, clone or fork the repository. The former two options
(download or clone) will give you a local copy of the system (see
[running locally](#running-locally) below), while cloning the
repository can allow you to work within the online version control
system (see [working online](#working-online)).

To **download** the system source, navigate to the [Annodoc
repository] and click on the `Download ZIP` link on the right-hand
toolbar. You should then unpack the downloaded `.zip` file in an
appropriate location and move to the directory with the source.  For
the next steps, see [running locally](#running-locally) below.

To **clone** the system, you will need the [Git] version control
system. After making sure that Git is available, navigate to the
[Annodoc repository] and copy the "clone URL" from the right-hand
toolbar. Then, run the command `git clone <URL>`, where `<URL>` is the
clone URL copied previously. Finally, move to the cloned directory and
see [running locally](#running-locally) below for the next steps.

To **fork** the system, you will need a GitHub account. Then, while
logged in to GitHub, navigate to the [Annodoc repository] and click on
the `Fork` button on the top right. This will give you a copy of the
repository that you can work on in GitHub. You can then download or
clone this copy, as above, to [run the system
locally](#running-locally), or [work online](#working-online) (see
below).

## Running locally

**Please note**: the Annodoc system has been developed and tested in a
linux environment and has so far not been specifically tested on
Windows.  We strongly recommend a Unix or workalike system (OSX or
linux) for running the system locally.

For running Annodoc locally, you will need to have a recent version of
[Jekyll]. In particular, version 2.0 or greater is required for
[collection](#collections) features.

After getting a local copy of the system (see [Getting
started](#getting-started) above), you can build the site from
sources and serve the resulting documents using the command

```
jekyll serve --watch
```

(here, the option `--watch` specifies that Jekyll should watch the
source documents for changes and rebuild the site when there are any.)

If the above command runs successfully, you should see something like
the following:

<pre><code>$ jekyll serve --watch
            Source: .
       Destination: ./_site
      Generating... done.
 Auto-regeneration: enabled
    Server address: http://0.0.0.0:4000/
  Server running... press ctrl-c to stop.</code></pre>

Here, the value `Server address` (commonly `http://0.0.0.0:4000/`) is
a URL where Jekyll is serving the site from. You should be able to see
the documentation by navigating to this address.

## Working online

For working online using GitHub, please refer to the documentation for
GitHub Pages at <https://pages.github.com/>.

## Editing

(start TODO)

If the `editurl` site variable is set in `_config.yml` (see
[Configuration](#configuration)), the header of each page will contain
an "edit page" link. If `editurl` is correctly set, this link leads to
the [GitHub] online editing page, shown in the following:

<img style="width:100%; border:1px solid lightgray" src="static/img/gh-edit.png">

To get started, the only relevant parts are the large black edit area
and the "Cancel" and "Commit changes" buttons at the bottom.

To give this a quick try, click on the following link: 
[edit sandbox document]({{ site.editurl }}/sandbox.md). 
This opens a "sandbox" document in a new tab. After testing
it out, feel free to either cancel without saving your changes, or
save them into the version control system using the "Commit changes"
button. You can see the resulting document here (reload to see
changes, and please note it may take some time for the changes to show
up.)

For experimenting with the system, we recommend using the sandbox
document instead of any "real" documents.

To edit the actual documentation, first find the page you're
interested in. Then,

* Click on the "edit page" link on the top
* Make your changes in the GitHub editor
* (Optional: add a message describing your changes in the "Commit changes" box)
* Click on "Commit changes"

Finally, wait a moment for your revisions to the documentation to be
compiled (normally no more than 10 seconds) and reload the
documentation page to make sure they look right.

(You may wish to ask your system administrator to set up this feature
for use by documentation authors.)

## Visualizations

As explained in the section [what is annodoc?](#what-is-annodoc),
visualizations are created using a simple syntax that identifies a
section of the document as being annotation in some particular format.
The system then replaces these sections with the corresponding
visualizations.

This section provides examples of various ways to create
visualizations.

### Simple visualization examples

A single tree in the Stanford Dependency format can be embedded using
the following syntax:

    ~~~ sdparse
    Dogs run
    nsubj(run, Dogs)
    ~~~

which results in this embedded visualization:

~~~ sdparse
Dogs run
nsubj(run, Dogs)
~~~

The CoNLL-X format is also supported. For example,

    ~~~ conllx
    1    Dogs   dog    _    NNS    _    2    nsubj
    2    run    run    _    VBP    _    0    ROOT
    ~~~

gives

~~~ conllx
1    Dogs   dog    _    NNS    _    2    nsubj
2    run    run    _    VBP    _    0    ROOT
~~~

Similarly, the [.ann standoff] format is supported:

    ~~~ ann
    Barack Obama is the current president.
    T1 PERSON 0 12 Barack Obama
    ~~~

gives

~~~ ann
Barack Obama is the current president.
T1 PERSON 0 12 Barack Obama
~~~

### Alternative visualization syntax

As an alternative to the `~~~` syntax, you can use the equivalent HTML
tag form:

    <div class="sdparse">
    Dogs run
    nsubj(run, Dogs)
    </div>

This form is more flexible in allowing e.g. additional attributes
to control aspects of the visualization. For example,

    <div class="sdparse" id="simple-example-parse" tabs="yes">
    Dogs run
    nsubj(run, Dogs)
    </div>

gives

<div class="sdparse" id="simple-example-parse" tabs="yes">
Dogs run
nsubj(run, Dogs)
</div>

### Ambiguous tokens (SD format)

If your example has several instances of the same token, you can use
their position to refer to the exact token. In the following example
`can-5` refers to the fifth token of the sentence, `can`.

    ~~~ sdparse
    I can can the can .
    nsubj(can-3, I)
    aux(can-3, can-2)
    det(can-5,the)
    dobj(can-3,can-5)
    punct(can-3,.)
    ~~~

will result in this visualization

~~~ sdparse
I can can the can .
nsubj(can-3, I)
aux(can-3, can-2)
det(can-5,the)
dobj(can-3,can-5)
punct(can-3,.)
~~~

### POS tags (SD format)

POS tags are optional and use the format "text/POS".

    ~~~ sdparse
    POS/NNP tags/NNS can/MD be/VB attached/VBN to/TO ( any part of ) the/DT sentence/NN text/NN ./.
    dep(tags-2, POS-1)
    nsubjpass(attached-5, tags-2)
    aux(attached-5, can-3)
    auxpass(attached-5, be-4)
    prep(attached-5, to-6)
    det(text-14, the-12)
    nn(text-14, sentence-13)
    pobj(to-6, text-14)
    det(part, any)
    prep(part, of)
    ~~~

~~~ sdparse
POS/NNP tags/NNS can/MD be/VB attached/VBN to/TO ( any part of ) the/DT sentence/NN text/NN ./.
dep(tags-2, POS-1)
nsubjpass(attached-5, tags-2)
aux(attached-5, can-3)
auxpass(attached-5, be-4)
prep(attached-5, to-6)
det(text-14, the-12)
nn(text-14, sentence-13)
pobj(to-6, text-14)
det(part, any)
prep(part, of)
~~~

Any literal slashes ("/") can be escaped using backslash.

     ~~~ sdparse
     \\/\\ escapes/VBZ :/: \\o\//\\o\/
     nsubj(escapes, \)
     ~~~

~~~ sdparse
\\/\\ escapes/VBZ :/: \\o\//\\o\/
nsubj(escapes, \)
~~~

### Multiple lines of text

The literal sequence `\n` in the SD input text is interpreted as a
newline. (This sequence should be separated by space from the rest of
the input.)

    ~~~ sdparse
    One line \n and another.
    ~~~

gives:

~~~ sdparse
One line \n and another.
~~~

### Editing controls

Controls for visualization editing and information is accessible in
elements with the attribute `tabs="yes"` (or any other non-empty
value):

    <div class="sdparse" id="simple-example-parse" tabs="yes">
    Dogs run
    nsubj(run, Dogs)
    </div>

This gives:

<div class="sdparse" id="simple-example-parse" tabs="yes">
Dogs run
nsubj(run, Dogs)
</div>

You can click on the tab on the top right to edit the visualization,
but note that the edits are not saved anywhere as there's no
server. This is mostly useful to build and debug examples.

### Unicode

Everything is unicode-compliant.

    ~~~ sdparse
    ロボットは 東大に  入れる か 。/。
    nsubj(入れる, ロボットは)
    nommod(入れる, 東大に)
    ~~~

~~~ sdparse
ロボットは 東大に  入れる か 。/。
nsubj(入れる, ロボットは)
nommod(入れる, 東大に)
~~~

## Adding documents

To add new documents into the system, simply create a new `.md`
document in the base directory of the system and add the following
front matter at the beginning of the document:

<pre><code>---
layout: entry
title: DOCUMENT-TITLE
---</code></pre>

(where `DOCUMENT-TITLE` is the title you wish to give to the
document.)

This [YAML] front matter is required for Jekyll to identify the
document as markdown.

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
[YAML]: http://yaml.org/