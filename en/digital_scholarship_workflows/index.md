---

title: Digital scholarship workflows
slug: workflows
author: Tomislav Medak
date: 2019-07-16 19:52:05 UTC
description: Overview of digital tools and workflows I use in my scholarly work, ranging from digitisation and referencing of text, plaintext authorship, storage and backup, to presentation and web presence. It covers tools - ScanTailor, OCR, Zotero, Diigo, Hypothesis, Markdown, Atom, Pandoc, Gitlab, Reveal.js and Nikola.

...

<script type="application/json" class="js-hypothesis-config">

{"showHighlights": false}

</script>

<script src="https://hypothes.is/embed.js" async></script>

This page covers digital tools and workflows that I use in my scholarly work. Practices described here are shaped by shadow libriarianship, plain text authorship and autonomy from platforms. When I started my PhD in early 2018, I decided to re-organise and consolidate the processes how I digitise, read, annotate and reference texts of other peple - and how I was write, revise and publish texts of my own. There were three reasons that motivated me to do so. First, given that I was now living between two countries and that I have a disability limiting my capacity to move around the heavy load of books and print-outs, I have fully shifted to reading text exclusively on screen. Second, I have decided to systematise my reading and writing to be technologically maintainable and replicable over years and decades. Third, I have desired to create a workflow that would allow me to easily publish my writing in a variety of formats required by the exigencies of academia and to give it a presence in one place on my own website.

The tools and workflows presented here cover digitisation of text, reference management, digital reading, writing and revising in plaintext, storage and backup, and publishing to various formats ranging form .docx and .pdf to .html presentations and static websites. The workflows here build first and foremost on the impressive [PhD Starter Kit by Achintya Rao](https://raoofphysics.github.io/phd-starter-kit/). His detailed tutorial on how to set up PhD work, has helped me immensely and makes much of this document redundant. This document, however, covers a different scope. I also draw a lot from the [Guide to Plain Text Social Science by Kieran Healy](https://kieranhealy.org/resources/) and the work of Dennis Yi Tenen on [Sustainable Authorship in Plain Text](https://programminghistorian.org/en/lessons/sustainable-authorship-in-plain-text-using-pandoc-and-markdown). Bits and bobs gleened from various corners of the Internet are linked to in the following paragraphs. While none of the tools and workflows I discuss require much technological skill, for the discovery, experimentation and problem-solving I rely on the technical prowess of my closest collaborator [Marcell Mars](https://gist.github.com/marcellmars).


## Digitising

All books and texts I read, I read in the digital form. Digital text benefits from the fact that it is easily storable, portable, searchable, annotable and re-usable. It has its downsides compared to print, such as potential data rot or lack of physical navigation, but these considerations are of lesser priority to me compared to the advantages offered by digital text.

Digital text comes in many formats, but in my scholarly work I mostly encounter books, journals and articles in e-book formats such as .mobi or .epub, webpages or most commonly .pdf. A .pdf is either generated from a layout or from a scan. You can scan a book or a journal with a [book scanner](http://diybookscanner.org/), a copier or a simple camera. A scanned .pdf can be pushed through the Optical Character Recognition (OCR) process to become searchable, making it amenable to operations such as highlighting, annotation and citation that are standard fare of scholarly writing.

### Digitisation workflow

Detailed description of the workflow I have perfected and documented together with Dubravka Sekulić and Ann Mertens for the [Memory of the World](https://memoryoftheworld.org) shadow library can be found in the [Book Digitisation tutorial](https://knowledge-production.github.io/forge/tutorials/book-digitization.html). The workflow is mostly based on free softare and should work with minor adaptations equally on Linux, OS X and Windows. In brief, to digitise a book I use a hacklab scanner or flat-bed to create full-color, high-resoltion images of the book. In [ScanTailor](https://github.com/scantailor/scantailor/wiki/User-Guide) I crop out everything but the content of the pages, correct distortions and reduce the full-color of text sections to black and white, thus generating smaller image files. These files I OCR with and output to a .pdf file using either  [Tesseract](https://github.com/tesseract-ocr/tesseract/wiki) frontend [Gscan2pdf](http://gscan2pdf.sourceforge.net/) or [Abbyy Finereader](https://www.abbyy.com/en-eu/finereader/).

### OCR-ing a non-OCR .pdf file

To OCR a .pdf file that isn't OCR-ed previously, you either have to use proprietary software such as Abbyy Finereader or Adobe Acrobat Pro, or unstitch the .pdf into image files, OCR them with a tool such as Tesseract, and stitch them together into a searchable .pdf. To unstich a multipage .pdf into image files, I find that the command-line converter pdftoppm produces best output results, allowing me to set the output resolution and formats (.png, .jpg or .tiff) while retaining the quality of images:

~~~

pdftoppm -r 300 -png /path/to/sourcefile.pdf /path/to/destination/folder/

~~~

From there you can use the digitising workflow to OCR the output images and stitch them back into a .pdf file. This process can also help you improve scans that consist of two-page spreads or scans that have a lot of dark shadings and specks.

## Reference management, annotation and reading

Central to scholarly work today is keeping abreast of a large amount of published research, scholarly writing and daily reporting relevant to one's work. Not only does one have to read and keep an overview over a vast body of literature, but also be able to excerpt and summarise texts, easily retrieve segments for citation and manage bibliographic references. That are many software tools out there that assist you in managing your reading, annotation and referencing such as [EndNote](https://endnote.com/), [Mandeley](https://www.mendeley.com/) or [RefWorks](https://refworks.proquest.com/), but I prefer [Zotero](https://www.zotero.org/) as it is developed in a non-commercial ecosystem of free software and supported by universities.

While I use Zotero to organise my reading workflow, the reading I do mostly on an old trusty Adroid tablet using the fantastic [Moon+ Reader Pr](https://www.moondownload.com/). For reading and annotation of online texts I use social bookmarking tool [Diigo](https://www.diigo.com/user/tomislavmedak) and collective annotator [Hypothes.is](https://web.hypothes.is/).

### Zotero

How to use Zotero as a reference management and research tool is well explained on the [project website](https://www.zotero.org/support/). In brief, after [installing Zotero and connector for your browser of choice](https://www.zotero.org/download/), you can add a variety of bibliographic items either manually or more commonly by scraping bibliographic metadata from [Worldcat](https://www.worldcat.org), [OpenLibrary](https://openlibrary.org/), [Google Books](https://books.google.com/), [Amazon.com](https://amazon.com), [Google Scholar](https://scholar.google.com), academic repositories and websites that have well organised metadata. You can add books, articles, chapters, reports, documents, newspaper articles, blog entries, videos and a number of other formats.

Connector retrieves author, title, journal, volume publisher, pagination, ISBN, ISSN, DOI and similar data, and adds them to as a bibliografphic item in your local Zotero library. It is advisable to manually double-check the scraped metadata. Location of publisher, original year of publishing and similar details are frequently incomplete and incosistent across those metadata repositories. To each item in the library Zotero will attempt to add a .pdf if available, failing that you can attach a digital file. Zotero also creates a snapshot of any webpages you add to the library.

The items added to the library can then be organised into collections and subcollections, and tagged with keywords. This allows you to easily search and sort your references, assemble the reading for your research projects, add more items as you read and write, and later come back to find and add items that are useful for your other research projects.

You can back up your Zotero library by syncing it to the account you can open on Zotero.org. With a Zotero.org you benefit from creating group libraries, which you can share when doing teaching or writing with others.

Zotero has [LibreOffice, MS Word and Google Docs plugins](https://www.zotero.org/support/word_processor_integration) that integrate search and citation in your word processors. Zotero repository offers almost [10.000 citation styles](https://www.zotero.org/styles) that you can install in your Zotero. Zotero then automates the creation of biobliography from the citations you have used.

In my workflow, I use Zotero as an organiser and sandbox for my research. Typically I organise my future research projects in a thematic collection and subcollections, meticulously adding the .pdf files of texts to bibliographic items. As much as Zotero is central to my reading and writing workflow, so is the the add-on [ZotFile](http://zotfile.com/) central to my use of Zotero. Zotfile I use to send a .pdf file to a cloud folder that I sync with my tablet for reading. I read, highlight and annotate the file on my tablet, using the [Moon+ Reader Pro](https://www.moondownload.com/) (no free software, but works excellent with a large number of digital formats, including .pdf, .mobi and .epub, and is more than worth its US$5). Once I have recorded the edited file in the synced cloud folder, I use the ZotFile to retrieve it back into Zotero. ZotFile automatically extracts all the annotations which ZotFile stores in a note and retains the highlights them in the attached .pdf. This is a superb feature that allows me to easily parse the highlights and quote the text at any point later. To set up ZotFile add-on, in its preferences you need to define the local path on your computer to the folder you sync with your cloud and tablet.

Another important add-on for my Zotero workflow is [Better BibTeX](https://retorque.re/zotero-better-bibtex/). Better BibTeX automatically generates .bib file(s) that contain reference-lists from the entire library or a (sub-)collections and assigns to each item a unique citation key. The citation keys I use to reference works when entering citations in the texts I write in Markdown (see the next section on writing). When converting a Markdown text into a formated text, I can specify the citation style and that citation key will be transformed into a properly formated reference for that citation style. To set up Better BibTeX, one needs to define the format of the citation key in the Better BibTeX tab of Zotero preferences. In my case, it's [auth:fold:lower:condense=_]_[Title:nopunct:skipwords:select,1,1:lower]_[year]. For Achintya Rao's PhD Starter Kit this translates into rao_phd_2016. As indexing a large library takes time, it is advisable to instruct Better BibTeX to do automatic export when idle.

Finally, some journals require that you include DOI links in the references. [Zotero DOI Manager](https://github.com/bwiernik/zotero-shortdoi/releases/tag/v1.3.8) add-on can verify if those exist and add them to your library items.

### Diigo & Hypothesis

Zotero was created primarily with journal articles and books in mind. However, there is no easy way to annotate webpages. While I still use Zotero to reference webpages, to annotate them I use primarily social bookmarking service [Diigo](https://www.diigo.com). Diigo annotations I add manually as a note to their respective Zotero references.

[Hypothesis](https://web.hypothes.is/) is a tool that adds a layer of collective annotation and public debate on top of any webpage or online and local .pdf files. To see it in action, go to the retractable shelf in the upper left corner of this webpage. It will reveal annotations and notes related to this webpage made on Hyopthesis. If you are logged in on Hypothesis, selecting a section of a webpage will bring up tool selectors allowing you to either annotate or highlight the section. You can also enter a URL of any webpage after https://hyothes.is to open a discussion on that webpage. The tool is particularly useful for reading groups and collective learning processes, however I find it less useful than Diigo for extracting annotations for storing in Zotero.

### Annotated bibliography

To maintain a good overview of key points in texts you use in your research and their relevance for your research, it is advisable to keep an annotated bibliography. An annotated bibliography typically consists of a list of sources with short description and evaluation of each source. Some universities may require students to keep an annotated bibliography and submit them for progress review panels, but it is a useful building block in creating a literature review. [University of New South Wales](https://student.unsw.edu.au/annotated-bibliography) provides a good overview of the purpose of an annotated bibliography and structure of annotations.

I follow Emory University's [helpful guide](https://student.unsw.edu.au/annotated-bibliography) to creating annotated bibliographies in Zotero by using either abstract or extra fields and annotated bibliography citation styles.

## Writing

When starting my PhD I decided to change the workflow how I am writing, formatting and revising my texts. Chapter drafts have to be revised over and over creating versions upon versions with ever more complicated file names. Formatting, citations styles and front matter have to be changed for each publication a text is submitted to. A text written for a publication should eventually appear on my personal website. So, all these exigencies led me to adopt and adapt a writing workflow based on [Markdown](https://daringfireball.net/projects/markdown/) plain text and [Pandoc](https://pandoc.org/) document converter. Using Pandoc a Markdown plain text can, with little or no changes, be output with different citation styles into different file formats, equally for publication submissions, slide presentations or website pages. Markdown files are small and I can easily store them on software development repositories using [Git](https://git-scm.com/) version control system. Elements of this workflow are covered in the rest of this document.

### Markdown

Markdown is a markup language with a syntax based on formatting conventions of email. Single `*asterisks around words*` stands for *italics*, double `**asterisks**` for **bold**. Single `# hastag` stands for heading 1, double `# hastag` stands for heading 2. Principally, syntax indicates semantic structure - italics is a single emphasis, bold is a double emphasis - that can be later rendered into a formatted text. Markdown was initially developed by [John Gruber](https://en.wikipedia.org/wiki/John_Gruber) and [Aaron Swartz](https://en.wikipedia.org/wiki/Aaron_Swartz) with the intent of making the marked-up text readable to regular mortals who have little clue about computer languages. Here is a [helpful tutorial](https://www.markdowntutorial.com/) to get you started, here a [handy cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) with Markdown syntax.

### Atom

While written in a markup syntax and with an .md extension, Markdown files are plain text files and can be created using the simplest of text editors such as [nano](https://www.nano-editor.org/) on *nix systems, [TextEdit](https://support.apple.com/guide/textedit/welcome/mac) on OS X, r [NotePad](https://git-scm.com/) on Windows. However, advanced text editors such as [Emacs](https://www.gnu.org/software/emacs/) or [Vim](https://www.vim.org/) can add a lot of functionality. I use [Atom](https://atom.io/), a free software text editor, developed by GitHab, and available for all major operating systems.

Atom with its packages provides a lot of support for Markdown writing and integrates well with Zotero. To improve usability of Atom as a writing tool, I use [TypeWriter](https://atom.io/packages/typewriter) for centered layout and [Wordcount](https://atom.io/packages/wordcount) for displaying word and character count. To improve Markdown experience, I use [Markdown Writer](https://atom.io/packages/markdown-writer) for syntax assistance and [Markdown Preview Enhanced](https://atom.io/packages/markdown-preview-enhanced) for previewing the document rendered in Pandoc (make sure you have ticked 'Use Pandoc Parser' and set the path to Pandoc executable and commandline arguments such as ).

To integrate Atom with Zotero using .bib file generated by BetterBibTex add-on in Zotero, install the [Autocomplete-bibtex](https://atom.io/packages/autocomplete-bibtex) package and enter in the settings path to the .bib file of your Zotero library. Markdown already comes with a syntax for citation in the form [@id]. If you type in '@' followed by the first letters of an author's name or title, Autocomplete-bibtext will bring up a drop-down menu offering you to select items from your Zotero library matching those letters. By selecting an item, a citation key for that item will be inserted into the text, resulting in an entry such as @tenen_plain_2017. A similar way to integrate Atom and Zotero is provided by [Zoter-picker](https://atom.io/packages/zotero-picker) that emulates the search bar in the LibreOffice and MS Word plugins.

### Spell-checking, grammar and style

As a native speaker of a minor language, my writing in English comes with rough edges. To weed out spelling errors when writing in Atom, I use [Linter-spell](https://atom.io/packages/linter-spell), which depends on hunspell or aspell for spell-checking. Linter-spell allows parallel spell-checking in multiple languages, which need to specified in the settings in Default languages field. In my case those are en-GB and hr-HR.

For issues of English grammar and style, there's a number of online services that provide assistance well beyond what built-in spelling checkers in word processors such as LibreOffice, MS Word or Linter-spell in Atom can do. My assistant of choice is [Grammarly](https://grammarly.com). Grammarly both integrates with browsers as an add-on and has a dedicated page to paste in a text for correction. Already as a free service it offers a lot of suggestions related to grammar and style, and much more as a subscription service. The jury is still out as to whether the subscription is worth its money.

## Formating & publishing

A text written in Markdown plain text can be converted into a variety of formats using Pandoc. I use Markdown and Pandoc to write my PhD chapters, my book project, submissions for academic journals, texts for media, slide presentations and posts for this website. All these have different requirements of how the texts are formatted and published: different citation styles, different text layouts, different front matters, different file formats. Writing semantically structured text in Markdown in Markdown syntax and rendering it into formatted text with Pandoc gives me maximum flexibility and reusability of text.

### Pandoc

[Pandoc](https://pandoc.org/), a free software developed by the philosopher of science [John MacFarlane](https://johnmacfarlane.net/), is a universal document converter that can translate between a large number of formats, including from Markdown plain text to fully formatted .html, .docx or .pdf documents. Pandoc can read syntax for front matter metadata, links, footnotes, tables, ordered lists, mathematical formulas and many other structural elements and render them into beautifully styled documents. It also includes [pandoc-citeproc library](http://hackage.haskell.org/package/pandoc-citeproc), which can automatically generate citations and a bibliography in pandoc documents using the Citation Style Language (CSL) files.

[Pandoc manual](https://pandoc.org/MANUAL.html) provides a detailed guide to using Pandoc. My baseline Pandoc command for conversion from .md to .docx has the following structure:

~~~

pandoc document.md --metadata-file=metadata.yml --bibliography=/home/<user>/.pandoc/bibliography/zotero_library.bib --csl=/home/<user>/.pandoc/csl/harvard.csl --reference-doc=/home/coyu3/.pandoc/custom-reference.docx -s -o document.docx

~~~

This will output the document.md file, using my metadata YAML file, my Zotero library .bib, Harvard referencing style and custom-reference.docx template, into a document.docx file (make sure to replace placeholder paths to files and file names with your own). Flag -s (or --standalone) produces an output with an appropriate header and footer, but the header and footer automatically included for some formats (including .pdf, .docx and .odt) and not for others (including HTML, LaTeX or .rtf). Flag -o indicates the output file.

A separate YAML metadata file is a relatively recent feature and might not work in older Pandoc versions. Instead you can write a YAML metadata block at the top of your text Markdown file. In fact this is what I mostly do myself. In a YAML block you can include a number of items, such as the fontfamily, csl style and .bib file that will be used with the document. I tend to include only the front matter and retain flexibility with format elements by specifying them only when outputting in Pandoc. A typical YAML block of my article has the following structure:

~~~

---
title: 'The Postdigital Condition and the Accelerated Technocapitalism'
subtitle: 'Accelerated Instrumental Rationality and the Three Responses of the Far-Right'

author:
  - Tomislav Medak
  - Coventry University
  - ORCID 0000-0003-3844-0434
  - medakt@coventry.ac.uk

date: June 26th, 2019

abstract: |
  **Abstract**: The article argues that the postdigital condition can be understood from the changing global economic and political context that was conducive to digital network technologies becoming ubiquitous...

...

~~~

Custom-reference.docx generated by pandoc has a number of predefined styles. I have combined examples and tweaks I found online to create a .docx template that suits my needs. You can download it from [here](/files/custom-reference.docx). If you want to add another style, you need to create a custom style in your .docx template file and then use the HTML style span tag around the relevant segment of text in your .md file to match that style. For example, for a custom style for keywords, I had to span the keywords in my .md in the following way:

~~~

<span custom-style=“Keywords”>**Keywords:** postdigital, digital economy, technocapitalism, liberal capitalist hegemony, the far-right</span>

~~~

Pandoc generates .pdf files using LaTeX and depends on a .pdf engine installed on your system. The default LaTeX template produces beautiful .pdf files. Plain HTML output, however, will be bare-bones and will require CSS or HTML5 templates to define the layout of the webpage. For more complex documents and uses, a good starting point is a repository with [user-contributed templates](https://github.com/jgm/pandoc/wiki/User-contributed-templates).

### Citation Style Language files

Markdown syntax for citation is [@citationkey]. Pandoc-citeproc will use the specified .bib file and citation format file to output citations and a bibliography in desired form. Almost 10.000 .csl files for various referencing standards and publications-specific styles can be downloaded from the [Zotero Style Repository](https://www.zotero.org/styles). If your editor doesn't have a .csl file, you can try to detect what style they use at the [Citation Style Language project](https://editor.citationstyles.org/). If it only approximates a style, there you can edit an existing style to build a .csl file for their style.

## Revising

The downside of Markdown plain text and Pandoc workflow is that tracking changes and comments among versions cannot be practically done in a document as with .docx or .odt files. If you receive the suggestions and comments in a .docx, you can use Pandoc to convert a .docx version of your document back into .md, using the following command:

~~~

pandoc -s commented-document.docx --wrap=none --track-changes=all --atx-headers -o commented-document.md

~~~

Option --track-changes can have three values: accept, reject and all. If we use 'all' to include all delitions, insertions and comments, thus replicting the 'show changes' function of word processors, the results are underwhelming - there is so much noise from added inline code that it renders the Markdown document unreadable while also breaking a part of the syntax such as citation keys.

One course of action is to go through the suggested changes in the receieved .docx file and manually enter them into the original Markdown document. Another course of action is to run pandoc conversion with the 'accept' option and then compare differences, merge them or edit the original with a tool such as [Meld](https://meldmerge.org/).

If your supervisors or editors want to see the changes you have made between two drafts, you can always output two versions of your .md file to a .docx or .odt and create a track-changes file with LibreOffice's ['compare document' function](https://help.libreoffice.org/Common/Comparing_Versions_of_a_Document). The same can be done for .pdf versions - Timothée Poisot has instructions how to do that on [his blog](http://timotheepoisot.fr/2014/07/10/markdown-track-changes/).

## Naming, storing & backing-up files

To organise my scholarship files, I divide my projects between the 'PhD' folder that includes not only the thesis but everything related to my PhD study, 'writing' folder that includes not only my writing but all collaborative writing projects, 'web' folder that includes my static website, 'presentations' folder that includes my conference texts and slides, and 'technocapitalism' book project folder. Following useful advices of [Achintya Rao's PhD Starter Kit](https://raoofphysics.github.io/phd-starter-kit/#directory-structure), I have adopted a heterogenous yet consistent nomenclature for my directories and files. Folders and sub-folders are named differently, depending what works best for retrieval and manipulation: short memorables titles, priority sorting using numeral prefixes 01, 02, 03,..., or chronology sorting using [ISO Date Format](http://en.wikipedia.org/wiki/ISO_8601) prefix YYYYMM.

Naming versions of a text as it undergoes revisions can be a cause for confusion. There is always small edits that happen between major drafts and there is always small edits that happen after the final submission. Adding suffixes 'v.1, v.2, v.3...' or 'draft_1, draft_2, draft_3... final' can easily get out of hand. For this reason I use Git to version, store and backup my scholarship.

### Git, Gitlab and SparkleShare

[Git](https://git-scm.com/), a free software developed initially by Linus Torvalds, is a version control system for collaborative software development projects. Each of my five scholarship directories is a git folder that I keep synced with my online repository on [GitLab](https://gitlab.com/) ([GitHub](https://github.com) or [BitBucket](https://bitbucket.org/) should serve you equally). Extensive [Git documentation](https://git-scm.com/docs) is available from the Git project, a [handy quick overview of commands](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf) from the GitHub.

To initiate an existing project folder into a git folder, you have to execute the follow sequence of commands:

~~~
cd <localdir>
git init
git add .
git commit -m 'message'
git remote add origin <url>
git push -u origin master
~~~

Before you do 'git commit', you should probably exclude all large folders or files by creating a .gitignore file in the same folder, specifying in the file the path do documents you want to ommit. <url> you will obtain by creating a new project on GitLab (or GitHub if you use that).

Once you have created a remote repository, you will be syncing the changes you made locally by executing the line:

~~~

git add -all; git commit -m 'message for this revision'; git push

~~~

Changes to remote repository made by your co-authors or collaborators you wil be syncing to your local folder by doing:

~~~
git pull
~~~

The folder synced and backed up on your remote repository can always be copied to another computer locally by doing:

~~~
mkdir <localfolder>
git clone https://gitlab.com/USERNAME/PROJECT-NAME.git
~~~

You can automate this process by using [SparkeShare](https://www.sparkleshare.org/), a git-based file-sharing application, that acts in similar ways as cloud storage applications such as Dropbox or Google Drive. After you have set up [SparkleShare](https://opensource.com/article/19/4/file-sharing-git), it run as a daemon in your system tray keeping your .git folders synced locally and remotely.

## Presentations & website

To create slide presentations with Markdown, I use the [Reveal.js](https://github.com/hakimel/reveal.js/) - a highly capable framework for creating presentations in HTML, developed initially by [Hakim el Hattab](https://hakim.se/), with slick features such as nested slides, fragments, speaker notes and PDF export. To create my website with Markdown, I use [Nikola](https://getnikola.com/) static web generator, developed by Roberto Alsina.

### Reveal.js

Reveal.js slides can be written directly into the index.html file, both as in the HTML markup and Markdown. Importantly, however, Reveal.js can load external Markdown. This allows me to easily transform the text of my talk that I have already written in Markdown into a slide show or converseley write my text as slide notes.

To create a presentation, first in the index.html file I enter metadata such as author and title, paths to stylesheets that will be used to render the presentation (Reveal.js comes with a number of beautiful themes), most importantly name of the Markdown file and separators that I will use for horizontal and vertical slides:

~~~

<div class="slides">
  <!-- Use external markdown resource, separate slides by three newlines; vertical slides by two newlines -->
  <section data-markdown="technologies_and_ecological_transition.md"
           data-separator="!---!"
           data-separator-vertical="!--!"
           data-notes="Note:">
  </section>
</div>

~~~

Now I can write my presentation in technologies_and_eclogical_transition.md file. A typical slide segment has the following structure:

~~~
!---!

# modeling the human needs within planetary boundaries

<img src="./raworth_embedding.png" height="400" />

<font size="4"> Kate Raworth, *Doughnut Economics: Seven Ways to Think Like a 21st-Century Economist*, 2017 </font>

Note: all economic processes are drawing on living matter, materials and energy from nature, transforming them from a more ordered state into a less ordered state, from a more usable condition to a less usable condition.

!--!
~~~

As can be seen from the example, slide segments typically combine Markdown and HTML syntax, at least to link to images, which I place into the presentation folder.

I also tend to tweak the existing behavior and themes to suit my preferences, for instance by setting in the index.html file an absolute position for heading 1.

### Nikola

[Nikola](https://getnikola.com/) (named after Nikola Tesla) is a static website generator comparable to [Jekyll](https://jekyllrb.com/) or [Hugo](https://gohugo.io/). Most of the online publishing frameworks such as Wordpress or Mediawiki use databases and web programming to dynamically generate a webpage for each visitor. Yet most of the content we publish on our websites is, in fact, meant to be static - every visitor is supposed to see the same content. Static website generators are response to this mismatch and its consequences. With static websites, you generated the website locally and then upload it to the server. What goes in is Markdown, HTML and CSS, what goes on the server is just HTML files and the linked images and documents. This has substantial advantages: software updates by your online hosting service will not obsolete your website if you stop updating, websites are safer, they are far less resources hungry, they don't lock you in with a vendor. You can always host your HTML files on another server, no matter how big or small. They provide you autonomy from platforms and lock-ins, while offering everything you might expect from a modern website: themes, blogs, tags, comments, RSS/Atom or social media integration.

[Nikola](https://getnikola.com/getting-started.html) is easy to install across major operating systems. Once you've installed Nikola, you can initialise you website locally. A Nikola website can behave as primarily a blog or as a site. Nikola has an extensive [handbook](https://getnikola.com/handbook.html) providing you with all the ins and the outs of installing and using the framework.

I host my website on GitHub Pages, [using my own domain](https://getnikola.com/handbook.html), which costs me the price of domain registration. This allows me to use Git to update the changes to the website. This is done with a single line of code run from my local Nikola website folder:

~~~

nikola build; git add --all; git commit -m "`date`"; git push

~~~

However, should GitHub ever terminate the service, I can always transfer the website eslewhere and use another protocol, as basic as FTP, to maintain my website.

Important for my purposes, Nikola can use Pandoc to compile HTML. For this purpose, you need to uncomment [a line in the list of compiles] (https://getnikola.com/listings/conf.py.html#listingsconfpy-305) and set [PANDOC_OPTIONS](https://getnikola.com/listings/conf.py.html#listingsconfpy-1085) in the con.py file located in the local Nikola website folder. The options in my case read:

~~~

PANDOC_OPTIONS = ['--toc', '--template=/home/<user>/.pandoc/templates/html_nikola.template', '-t', 'html5', '--filter', 'pandoc-citeproc', '--bibliography=/home/<user>/.pandoc/bibliography/zotero_library.bib', '--csl=/home/coyu3/.pandoc/csl/harvard-coventry-university.csl' ]

~~~

Obviously, Pandoc here uses a custom template created by my collaborator Marcell Mars to deal with some of my additional front matter. Nikola already offers a number of [metadata entries](https://getnikola.com/handbook.html#id18). Nikola uses by default reST comments wrapped in a comment, but you can [easily change that into YAML](https://getnikola.com/listings/conf.py.html#listingsconfpy-317) in the conf.py. My template file adds to existing metadata, affiliation for the authors, article abstract, and article lead. The file is available [here](/files/html_nikola.template).

On some pages on my website, including this one, I have Hypothesis installed. To add Hypothesis script to a page, you need to add the following code after your metadata entry:

~~~

<script type="application/json" class="js-hypothesis-config">

{"showHighlights": false}

</script>

<script src="https://hypothes.is/embed.js" async></script>

~~~

To improve how pages and posts are shared on Facebook or Twitter, it is necessary to include a preview image. This is done by placing an image of optimal size (for Facebook, it's 1200x635 pixels) and use the 'previewimage' metadata element with the relative path to the image file (e.g previewimage:/images/<filename>.jpg). Before you share, it's best to go to Facebook's [Object Debugger](https://developers.facebook.com/tools/debug/og/object/) to test if the preview image works as expected.

To improve discoverability and ranking of your pages and posts on search engines, add in the 'description' metadata element of each page or post a description of its content that best relates to potential searches. Finally, to add Google Analytics to your Nikola, you have to uncomment [the BODY_END line](https://getnikola.com/listings/conf.py.html#listingsconfpy-1204) in you conf.py and enter the following code:

~~~

BODY_END = """
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-131829443-1"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-131829443-1');
</script>
"""

~~~

For more customisation and tweaks, [Nikola docmentation](https://getnikola.com/documentation.html) offer a plenitude of resources, but you can find also find on the web examples of Nikola-powered website customisations such as the highly resourceful [Lois Tiao's blog post](http://louistiao.me/posts/how-i-customized-my-nikola-powered-site/).

Further sources:

[@healy_plain_2018]
[@poisot_tracking_2014]
[@rao_phd_2016]
[@tenen_sustainable_2014]
[@tenen_plain_2017]
