---
title       : Leveraging Open Source Software and Tools for Research
subtitle    : Write Once, Publish Everywhere
author      : Adam Van Iwaarden
job         : NCME April 15, 2015
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Introduction

The internet is the Gutenberg Press of the 21st Century.

>1.  Free (at least some places, like Github)
>2.  Open
>3.  Collaborative
>4.  Customizable - as simple or complex as you want.

Version control and open environment lend itself to collaboration, replication and elaboration.

--- .class #id 

## Grim Reality ...

Much of the world is still stuck in the dark ages of printed media.  There is still a demand for more traditional document formats.

>- PDF
>- Word Documents
>- Printable electronic media

---

## Grim Reality ...

Might have to make choices about what types of document formats we use based on the demands (skills) of others rather than what is ideal or desired.

---

## A way to have it all?

Like the Gutenberg Press, what we need is a universal template that allows us to write once, but publish our documents everywhere we want.  Add the ability to do it the formats we want.

My experiments with templating:

>1. Markdown Document: using markdown text files with Jekyll template(s)
>  - Can produce static web pages hosted on Github
>  - Free to use, but the process is kind of tedious.
>  - Only one "real" output format (HTML web page).  Printing to PDF painful.

>2. SGPreports:  using markdown text files with pandoc templates
>  - Attempt to produce a series of templates that convert a single text file into multiple formats.
>  - Default `pandoc` templates allow you to do this to some extent, but lacks consistency and many features of one document type are not available in others.


---

## The Jekyll Workflow

My typical workflow for going from data and script file to a reproducible report that can be hosted on Github:

`R` / `knitr` **/ R markdown   ->   markdown  ->  YAML / Jekyll / Liquid -> static HTML**

---

## The pandoc Workflow

My typical workflow for going from data and script file to a reproducible report that can be hosted on Github:

`R` / `knitr` **/ R markdown /** `SGPreports`  **->  YAML  ->   markdown  / pandoc -> standalone HTML**

>**->  markdown  / pandoc -> DOCX draft**

>**->  markdown  / pandoc -> (LaTeX) PDF**

>**->  markdown  / pandoc -> EPUB e-reader**

---

##  The Simple Workflow, markdown  ->  standalone HTML

At the heart of creating documents using the `SGPreports` package is producing a markdown file with properly *formatted* and populated YAML list.

>-  Markdown is a language and formatting syntax that can be read by humans and easily converted to HTML.

>-  For more information about markdown, see the [project website](http://daringfireball.net/projects/markdown/) and wikipedia (http://en.wikipedia.org/wiki/Markdown).

---

## YAML Front Matter

YAML is a basic markUP language that takes the form of a well structured list of elements.  YAML is used here to:
>-  Describe the document (title, author(s), abstracts, etc.) 
>-  Provide information to `R` and `pandoc` about how to convert and format the markdown text file.


>-  YAML front matter is located at the very top of this file.  It is composed of several variables sandwiched between triple dashes (`---`). These variables define how your `SGPreport` document will appear and will require some customization for each document you produce.

[Read this](http://en.wikipedia.org/wiki/YAML) for a general information and [this for help with YAML syntax](http://www.yaml.org/start.html).

---

## Add in Complexity as Desired

Complexity can be added to the workflow in multiple areas.

>1.  Using `R`, R markdown and the `knitr` package to process `R` code and include results in an output markdown file that can be converted to HTML.
>2.  Inline and in text HTML.
>3.  Using css, javascript, Bootstrap frameworks and other tools to create more stylized pages and complex (navigable) websites.  These are elements included in the gh-pages directory along with the markdown file.

---

##  Markdown_Document and SGPreports Projects

I wanted to create something that would allow me to easily turn a markdown file into an attractive document with an academic feel to it.  I wanted to be able to include features such as the inclusion of a section numbering, interactive (D3) visualizations, and mathematical equations.  Using css, Liquid templating (for Jekyll), and a few other tools, I created the "Markdown_Document" project two years ago.

>-  This is a simple, static site that displays an example of the documents that it can produce, which also serves as a manual for its use.  The example page can be viewed [here](http://adamvi.github.io/Markdown_Document/), and the Github repository can be viewed/forked/downloaded [here.](https://github.com/adamvi/Markdown_Document)

>-  See my [presentation from the 2014 NCME Training Session](http://centerforassessment.github.io/NCME_2015_Presentations/Adam/Markdown_Document.html) for more details and an example of how to set up a Markdown_Document repository

---

##  Markdown_Document and SGPreports Projects

SGPreports is a brand new project that has grown out of my work on the Markdown_Document project.  I wanted an easier solution that was completely integrated into `R`. 

>- Simplify my workflow - fewer moving pieces
>- Make it easier for others to replicate my workflow

---

##  Uses of Markdown_Document and SGPreports

>1.  Reports for state-level work with Student Growth Percentiles
>2.  White papers and research reports
>3.  Dissertation work

---

##  SGPreports

I've created a package for the R statistical environment called `SGPreports` and this can be installed through Github.  The package is still in its infancy, so it is not available on [CRAN](http://cran.r-project.org/web/packages/available_packages_by_name.html) yet.  

```
install.packages('knitr', dependencies = TRUE)
devtools::install_github('rstudio/rmarkdown')
devtools::install_github('adamvi/SGPreports')
```

---

##  SGPreports Vignettes

As part of the package I've created an *unconventional* vignette for the package.  This contains two markdown files that run through a demonstration of how to create brief reports.  

>-  One is simple.  This file (Vignette_Simple.Rmd) can be used to render a markdown text file into all four available output formats.

>-  The second file (Vignette_Complex_HTML.Rmd) contains more complex use cases, such as the ability to include interactive charts and plots.  Given the complexity of many of these features, this example report can only be rendered in HTML.

>-  Loading the SGPreports package and running this script will produce a file directory in your current working directory, change your working directory to it, and prints out a message with some instructions.

```
require('SGPreports')
getVignette()
```

>-  You can find out what directory is your working directory with the command `getwd()`
