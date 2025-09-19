---
layout: post
title:  "Convert LaTex to docx"
date:   2025-09-19 15:50:15 +0200
categories: academic stuff
---

# How to convert a LaTex document into an Office document (docx)

Here is what I learned from a frustrating situation with a paper that I submitted to a journal, where the author instructions allowed a LaTex submission but the editorial reality was different. This can work quite well and it is a **much** better solution than loading a PDF into your favorite word processor or Acrobat Pro, but expect to do some manual formatting after the conversion.

- have pandoc and citeproc installed on your system
- convert vector figures into PNG files
- become familiar with how styles work in your word processor (I am using Libre Office)
- get a csl file (citation style language) of the journal, or one that is close enough
- forcefully insert a section called "References" in your LaTex document because otherwise it will not be there in the docx file
- if you use math symbols, expect them to be some special type of object in the office document (example: `$\dagger$`)
- use the commands below to convert
- check for more complicated in-text citations like (some fact; Author 1999) and correct them if necessary
- check if there are problems with the author name disambiguation (author first names popping up in in-text citations) and correct by hand if necessary


There are approaches:
1) conversion without a reference document
2) conversion with a reference document

## Without a reference document

```
pandoc -f latex -t  docx  --bibliography=your_bibfile.bib --citeproc --csl=journalname.csl -o name_of_office_document.docx name_of_tex_file.tex 
```

This is the simplest method. You simply change the weird default style to your needs in the word processor. However, if you find that you might have to change something in the LaTex code, you may have to repeat many manual steps.


## With a reference document

```
pandoc -f latex -t  docx  --bibliography=your_bibfile.bib --citeproc --csl=journalname.csl --reference-doc=style_reference_document.docx -o name_of_office_document.docx name_of_tex_file.tex 
```

This approach has the benefit of being able to make changes in the LaTex file without having to repeat the formatting steps in the word processor. The downside is that your reference document might break certain things like reference formatting, if it is not how `pandoc` expects it to be.

If things are breaking, copy from the converted version without the reference document and inspect the style names. This might be especially important for tables.

Important: the bibliography style should be named "Bibliography" (not "Bibliography 1" as Libre Office names it).

If tables don't render, check if they render in the converted version without the reference document.
