<!--
.. title: 'Digital scholarship workflows'
.. slug: workflows
.. author: Tomislav Medak
.. date: 2019-07-22 19:52:05 UTC
.. previewimage: /images/digital_scholarship.png
.. description: Overview of digital tools and workflows I use in my scholarly work, covering a range of actions from digitisation, annotation, referencing, plaintext authorship, storage and backup, to presentation and web presence. It includes workflows based on ScanTailor, OCR tools, Zotero, Diigo, Hypothesis, Markdown, Atom, Pandoc, Git, Reveal.js, reveal-md and Nikola.
-->

---
lead: This page covers digital tools and workflows that I use in my scholarly work, covering a range of actions from digitisation, annotation, referencing, plaintext authorship, storage and backup, to presentation and web presence. It includes workflows based on ScanTailor, OCR tools, Zotero, Diigo, Hypothesis, Markdown, Atom, Pandoc, Git, Reveal.js, reveal-md and Nikola. The approach builds on practices of shadow librarianship, plain text authorship and autonomy from platforms. While these workflows are particularly useful to scholars, they can be practical for anyone doing a lot of reading and writing.
---

<script type="application/json" class="js-hypothesis-config">

{"showHighlights": false}

</script>

<script src="https://hypothes.is/embed.js" async></script>

<!-- TOC -->

- [1) Digitising](#1-digitising)
    - [Scanning and creating an OCR-ed PDF](#scanning-and-creating-an-ocr-ed-pdf)
    - [OCR-ing a non-OCR-ed PDF](#ocr-ing-a-non-ocr-ed-pdf)
- [2) Reference management and annotation](#2-reference-management-and-annotation)
    - [Zotero](#zotero)
    - [Diigo and Hypothesis](#diigo-and-hypothesis)
    - [Annotated bibliography](#annotated-bibliography)
- [3) Writing](#3-writing)
    - [Markdown](#markdown)
    - [Atom](#atom)
    - [Spell-checking, grammar and style](#spell-checking-grammar-and-style)
- [4) Formatting and publishing](#4-formatting-and-publishing)
    - [Pandoc](#pandoc)
    - [Citation style language files](#citation-style-language-files)
- [5) Revising](#5-revising)
- [6) Naming, storing and backing-up files](#6-naming-storing-and-backing-up-files)
    - [Git, Gitlab and SparkleShare](#git-gitlab-and-sparkleshare)
    - [Backing-up the Zotero library](#backing-up-the-zotero-library)
- [7) Presentations and website](#7-presentations-and-website)
    - [Reveal.js and reveal-md](#reveal-js-and-reveal-md)
    - [Nikola](#nikola)

<!-- /TOC -->

When I started my PhD in early 2018, I decided to re-organise how I digitise, read, annotate and reference other people's texts - and how I write, revise and publish my own. Three reasons motivated me to do so. First, living now between two countries with a disability that limits my capacity to move around heavy loads of books, I decided to shift entirely to reading text on the screen. Second, I wanted to systematise my reading and writing workflows around simple standards that would be technologically maintainable over years and decades. Third, I needed a workflow that would allow me to easily re-format my texts for publishing in a variety of academic venues and on my own website.

The workflows presented here cover digitisation of text, reference management, annotated bibliography, writing in plaintext, formating for publication, revising text, storage and backup, as well creating slide presentations and a static website. They build first and foremost on the impressive [PhD Starter Kit by Achintya Rao](https://raoofphysics.github.io/phd-starter-kit/). His detailed advice how to set up work around a PhD has helped me immensely - and makes parts of this document redundant. I have also learned a lot from the [Guide to Plain Text Social Science](https://kieranhealy.org/resources/) by Kieran Healy [-@healy_plain_2018] and the work of Dennis Yi Tenen and Grant Wythoff on [Sustainable Authorship in Plain Text](https://programminghistorian.org/en/lessons/sustainable-authorship-in-plain-text-using-pandoc-and-markdown). In fact, [Dennis](http://denten.plaintext.in/) has written a monograph on *Plain Text* [@tenen_plain_2017]. Bits and bobs gleaned from various corners of the Internet I have linked to in the text. While none of the tools and workflows I discuss requires much technological skill, they do require some very basic knowledge of command-line (a.k.a. console, terminal, prompt). Ubuntu provides [a short beginners guide](https://tutorials.ubuntu.com/tutorial/command-line-for-beginners). For discovery, experimentation and problem-solving, or anything more sophisticated, I rely on the technical prowess of my friend and collaborator [Marcell Mars](https://gist.github.com/marcellmars).

## 1) Digitising

Books and texts I read, I read predominantly in the digital form. Digital text benefits from the fact that it is easily storable, portable, searchable, annotable and re-usable. Digital text, however, has its shortcomings compared to the text in print, such as potential data rot or lack of physical navigation. However, these shortcomings are of lesser concern than the advantages offered by digital text.

Digital text comes in many formats, but in my scholarly work I operate primarily with books, journals and articles in dedicated e-book formats such as `.mobi` or `.epub` or more commonly as `.pdf`. A PDF can be either born-digital or created by scanning. It is the latter that is of interest here. You can scan a book or a journal with [a book scanner](http://diybookscanner.org/), a photocopier or a simple camera. A scanned PDF can be pushed through the optical character recognition (OCR), making the resulting file amenable to highlighting, annotation and citation that are central to scholarly reading and writing.

#### Scanning and creating an OCR-ed PDF

A detailed description of the workflow that I use to scan books and create PDFs can be found in my [Book Digitisation tutorial](https://knowledge-production.github.io/forge/tutorials/book-digitization.html). This tutorial I have written together with Dubravka Sekulić and Ann Mertens for the [Memory of the World](https://memoryoftheworld.org) shadow library. The workflow is mostly based on free software and should work with minor adaptations equally on Linux, OSX and Windows. In brief, to digitise a book, I use [a hacklab scanner](https://www.memoryoftheworld.org/blog/2012/10/28/our-beloved-bookscanner-2/) or a regular office flat-bed scanner to create full-colour, high-resolution images of the book. Then next I use [ScanTailor](https://github.com/scantailor/scantailor/wiki/User-Guide) to crop the images down to the content of the pages, correct distortions and reduce the full-colour to black and white. This results in much smaller, mostly b/w image files. Against these files first I do optical character recognition, and then collate them into an OCR-ed PDF using either the  [Tesseract](https://github.com/tesseract-ocr/tesseract/wiki) GUI frontend [Gscan2pdf](http://gscan2pdf.sourceforge.net/) or the proprietary [Abbyy Finereader](https://www.abbyy.com/en-eu/finereader/).

#### OCR-ing a non-OCR-ed PDF

To OCR a PDF that hasn't been OCR-ed previously, you either have to use proprietary applications such as Abbyy Finereader or Adobe Acrobat Pro, or unstitch the PDF into image files, improve and OCR them and stitch them together into a searchable PDF. The latter is particularly useful if you have a PDF consisting of two-page spreads or if it has a lot of dark shadings and specks. To unstitch a multipage PDF into image files, I find that the command-line converter `pdftoppm` produces best output results, allowing me to set the output resolution and formats (`.png`, `.jpg` or `.tiff`) while retaining the image quality:

```
pdftoppm -r 300 -png /path/to/<sourcefile>.pdf /path/to/destination/directory/

```

From there, you can use the digitisation workflow described in the previous section to OCR the output images and stitch them back into a PDF file.

## 2) Reference management and annotation

Central to scholarly work today is keeping abreast of a large amount of published research, scholarly writing and daily reporting relevant to one's work. Not only does one have to read and keep an overview over a vast body of literature, but also be able to excerpt and summarise texts, easily retrieve segments for citation, and manage bibliographic references. Therefore, there are many software tools that assist scholars in managing your literature, annotations and references such as [EndNote](https://endnote.com/), [Mandeley](https://www.mendeley.com/) or [RefWorks](https://refworks.proquest.com/). My preference is for [Zotero](https://www.zotero.org/) because it is a free software programme developed in a non-commercial ecosystem and supported by a number of universities.

While I use Zotero to organise my reading workflow, the reading itself I do mostly on an old trusty Android tablet using the fantastic [Moon+ Reader Pro](https://www.moondownload.com/). For reading and annotation of online texts, I use the social bookmarking service [Diigo](https://www.diigo.com/user/tomislavmedak) and the collective annotation service [Hypothes.is](https://web.hypothes.is/).

#### Zotero

How to use Zotero as reference management and research tool is well explained on the [project website](https://www.zotero.org/support/). In brief, after [installing Zotero and connector for your browser of choice](https://www.zotero.org/download/), you can add a variety of bibliographic items either manually or more commonly by scraping bibliographic metadata from [Worldcat](https://www.worldcat.org), [OpenLibrary](https://openlibrary.org/), [Google Books](https://books.google.com/), [Amazon.com](https://amazon.com), [Google Scholar](https://scholar.google.com), academic repositories or any online source that contains well organised metadata. To Zotero you can add books, academic articles, book chapters, reports, documents, newspaper articles, blog entries, videos and many other formats.

The browser connector retrieves bibliographic metadata - author, title, journal, volume publisher, pagination, ISBN, ISSN, DOI... - and adds them as a bibliographic item to your Zotero library. It is always advisable to manually double-check the scraped metadata, as the location of publisher, original year of publishing and similar details are frequently incomplete and inconsistent across those metadata repositories. To each item in the library, Zotero will attempt to add a PDF if available. Failing that, you can attach a digital file manually. Zotero also creates a snapshot of any webpages you add to the library.

The items added to the library can then be organised into collections and subcollections and tagged with keywords. This allows you to search and sort your references quickly, assemble the reading for your research projects, add more items as you read and write, and later return to your existing collections to find items to drag and drop into your future research project collections.

You can back up your Zotero library by syncing it to the account that you can create at Zotero.org. With a Zotero.org account, you can create group libraries, which you can share when doing teaching or writing with others.

Zotero has [LibreOffice, MS Word and Google Docs plugins](https://www.zotero.org/support/word_processor_integration) that integrate search and citation in your text processors. Zotero repository offers almost [10.000 citation styles](https://www.zotero.org/styles) that you can install in your Zotero. Zotero then automates the creation of bibliography from the citations you have used. If your bibliographic metadata is complete and you have the right citation style file, this will save you an immense amount of time that you would spend on doing citations and bibliography manually.

I use Zotero as an organiser and sandbox for all of my research. Typically I organise future research projects in thematic collections and subcollections, meticulously attaching the PDF files of books or articles to their respective bibliographic entries. As much as Zotero is central to my reading and writing workflow, the add-on [ZotFile](http://zotfile.com/) is central to my use of Zotero. ZotFile I use to send a PDF file (`right-click on the item -> Manage Attachments -> Send to Tablet`) to a cloud directory that I sync with my tablet for reading. I then read, highlight and annotate the file on my tablet, using the [Moon+ Reader Pro](https://www.moondownload.com/) (not a free software, but works excellent with a large number of digital formats, including `.pdf`, `.mobi`, `.epub` and `.md`, and is more than worth spending $5 on it). Once I have recorded the edited file in the synced cloud folder, I use ZotFile to retrieve it back into Zotero (`right-click on the item -> Manage Attachments -> Get from Tablet`). ZotFile automatically extracts all the annotations, which it stores in a note, and retains the highlights you have made in the attached PDF. This is a superb feature that allows me to quickly parse the highlights and quote the text at any point later. To set up ZotFile add-on, you need to define in ZotFile preferences the local path on your computer to the folder you sync with your cloud and tablet.

Another important add-on for my Zotero workflow is [Better BibTeX](https://retorque.re/zotero-better-bibtex/). Better BibTeX automatically generates `.bib` file(s) that contain reference-lists of items from the entire library or any (sub-)collection and assigns to each item a unique citation key. The citation keys I can then use to reference works when entering citations in the texts I write in Markdown (see the next section). When converting a Markdown text into a formatted text, I only need to specify the citation style, and that citation key will automatically be transformed into a properly formatted reference for that citation style. To set up Better BibTeX, you need to define the format of the citation key in the Better BibTeX tab of Zotero preferences. I use the following pattern:

~~~~

[auth:fold:lower:condense=_]_[Title:nopunct:skipwords:select,1,1:lower]_[year]

~~~~

For Dennis Yi Tenen's monograph on *Plain Text* this translates into `tenen_plain_2017`. Also, while you're in BibTex preferences tab, it is advisable to instruct Better BibTeX to do automatic export when idle as indexing large libraries whenever you make an edit in your library can slow down your Zotero.

Finally, some journals require that you include DOI links in the references. [Zotero DOI Manager](https://github.com/bwiernik/zotero-shortdoi/releases/tag/v1.3.8) add-on can verify if those exist and add them to your library items.

#### Diigo and Hypothesis

Zotero was created primarily with journal articles and books in mind. However, you can't easily annotate webpages in Zotero. While I still use Zotero to reference webpages, to annotate them, I use primarily social bookmarking service [Diigo](https://www.diigo.com). Diigo annotations I add manually as a note to their respective Zotero references. I use Diigo also to bookmark websites from my phone for later reading. Similar functionality is offered by [Pocket](https://getpocket.com/) and [Instapaper](https://www.instapaper.com/).

[Hypothesis](https://web.hypothes.is/) is a tool that can be used to a layer of collective annotation and public debate on top of any webpage, as well as on any online or local PDF. To see it in action, go to the retractable shelf in the upper right corner of this webpage. It will reveal annotations and notes related to this webpage made on Hypothesis. If you are logged in on Hypothesis, selecting a section of a webpage will bring up a tool menu allowing you to either annotate or highlight the section. You can also enter a URL of any webpage after https://hyothes.is to open a Hypothesis thread on that webpage. The tool is particularly useful for reading groups and collective learning processes. However, I find it less convenient than Diigo to extract annotations for storing in Zotero. With either you can read and annotate *online* texts both on your computer and your mobile devices.

#### Annotated bibliography

In order to have an overview of key arguments in a vast amount of texts you use in your research and their particular relevance for your research, it is advisable to maintain an annotated bibliography. An annotated bibliography typically consists of a list of sources with short description and evaluation for each source. Some universities may require students to keep an annotated bibliography and submit it for progress review panels, but it is generally a useful building block in creating a literature review. [University of New South Wales](https://student.unsw.edu.au/annotated-bibliography) provides a good overview of the purpose of an annotated bibliography and structure of annotations.

I follow [Emory University's helpful guide](https://student.unsw.edu.au/annotated-bibliography) on how to create annotated bibliographies in Zotero. It recommends to use either "abstract" or "extra" fields in a bibliographic item, and then generate an annotated bibliography with the adequate annotated bibliography citation styles downloaded from the Zotero repository.

## 3) Writing

When I started my PhD, I faced the challenge of how to organise writing, formatting and revising of my texts. Chapter drafts typically have to be revised over and over, creating versions upon versions, potentially creating a labyrinth of ever more complicated file names. Formatting, citations styles and front matter frequently have to be changed for each publication a text is submitted to. A text written for a publication should eventually appear on my own website, but then it involves a lot of formatting work. All these complications led me to adopt and adapt a writing workflow based on [Markdown](https://daringfireball.net/projects/markdown/) plain text syntax and [Pandoc](https://pandoc.org/) document converter. Using Pandoc, a plain text in Markdown can, with little or no tweaking, be matched with different citation styles and output into different file formats. A single text can thus be easily re-formatted and re-used for different publication venues, slide presentations or website pages. Markdown files are small, can be easily stored, and their revisions kept track of on software development repositories by means of [Git](https://git-scm.com/) version control system. Elements of this one-text-many-output-formats workflow are covered in the rest of this document.

#### Markdown

Markdown is a markup language with a syntax extending the old email formatting conventions. Single asterisks `*`spanning words`*` indicates *italics*, double asterisks `**` **bold**. Single hashtag `#` indicates heading 1, double hashtag `##` heading 2. Syntax in Markdown indicates semantic structure (italics is a single emphasis, bold is a double emphasis, heading 1 is a top-level heading, heading 2 is a level two subheading, etc.) that can be later rendered into a formatted text with any selection of style. Markdown was initially developed by [John Gruber](https://en.wikipedia.org/wiki/John_Gruber) in collaboration with [Aaron Swartz](https://en.wikipedia.org/wiki/Aaron_Swartz) with the intent of making the marked-up text due to its minimalist syntax readable to regular mortals who have little clue about computer languages. Here is a [helpful tutorial](https://www.markdowntutorial.com/) to get you started, here a [handy cheat sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images) with an overview of Markdown syntax.

#### Atom

While written in a markup syntax and with an `.md` extension, Markdown files are not nothing but plain text files and can be created using the simplest of text editors such as [nano](https://www.nano-editor.org/) on *nix systems, [TextEdit](https://support.apple.com/guide/textedit/welcome/mac) on OSX, or [NotePad](https://git-scm.com/) on Windows. However, advanced text editors such as [Emacs](https://www.gnu.org/software/emacs/) or [Vim](https://www.vim.org/) can add a lot of functionality. I use [Atom](https://atom.io/), a free software text editor developed by GitHub, and available for all major operating systems.

Atom with its packages provides a lot of support for Markdown writing and integrates well with Zotero.

To improve the usability of Atom as a writing tool, I use:

  - [TypeWriter](https://atom.io/packages/typewriter) for centred layout;
  - [Wordcount](https://atom.io/packages/wordcount) for displaying word and character count.

To improve Markdown writing experience, I use:

  - [Markdown Writer](https://atom.io/packages/markdown-writer) for syntax assistance;
  - [Markdown Preview Enhanced](https://atom.io/packages/markdown-preview-enhanced) for previewing the document rendered in Pandoc (make sure you have ticked 'Use Pandoc Parser' and set the path to Pandoc executable and command-line arguments such as `.bib` file location and `.csl` citation style file in its settings).

To integrate Atom with Zotero using a `.bib` file generated by BetterBibTex add-on in Zotero, I use:

  - [Autocomplete-bibtex](https://atom.io/packages/autocomplete-bibtex). To set up the Autocomplete-bibtex you need to enter in its settings a path to the `.bib` file of your Zotero library. Markdown already comes with a syntax for citation in the form `[@id]`. If you type in `@` followed by the first letters of an author's name or title, Autocomplete-bibtext will bring up a drop-down menu offering you to select items from your Zotero library matching those letters. By selecting an item, a citation key for that item will be inserted into the text, resulting in an entry such as `@tenen_plain_2017`. A similar way to integrate Atom and Zotero is provided by [Zotero-picker](https://atom.io/packages/zotero-picker) that emulates the search bar in the LibreOffice, MS Word and Google Docs plugins.

#### Spell-checking, grammar and style

As a native speaker of a minor language, my writing in English often has rough edges. To weed out spelling errors when writing in Atom, I use the [Linter-spell](https://atom.io/packages/linter-spell) package, which depends on hunspell or aspell for spell-checking. Linter-spell allows parallel spell-checking in multiple languages, which you need to specify in the settings in the Default languages field. In my case, those are: `en-GB, hr-HR`. Make sure you have those hunspell or aspell language files installed on your system.

For issues of English grammar and style, several online services provide assistance well beyond what the built-in spelling-checkers in text processors such as LibreOffice, MS Word and Google Docs, or Linter-spell in Atom can offer. My assistant of choice is [Grammarly](https://grammarly.com). Grammarly both integrates with browsers as an add-on and has a dedicated page to paste in a text for correction. Already as a free service, it offers many suggestions related to grammar and style, and as a subscription service plenty more. The jury is still out as to whether the subscription is worth its money.

## 4) Formatting and publishing

A text written in Markdown plain text can be converted into a variety of formats using Pandoc. I use Markdown and Pandoc to write my PhD chapters, a book project, submissions for academic journals, texts for media, slide presentations and pages for this website. All these various kinds of venues have different requirements on how the texts need to be formatted: different citation styles, different text layouts, different front matter, different file formats. Writing a semantically structured text in Markdown syntax and rendering it into formatted text with Pandoc gives me maximum flexibility and reusability for my texts.

#### Pandoc

[Pandoc](https://pandoc.org/), a free software tool developed by the philosopher of science [John MacFarlane](https://johnmacfarlane.net/), is a universal document converter that can translate between a large number of formats, including from Markdown plain text to fully formatted `.html`, `.docx` or `.pdf` documents - and back to Markdown. Pandoc can read syntax for front matter metadata, links, footnotes, tables, ordered lists, mathematical formulas and many other structural elements, and render them into beautifully styled documents. It also includes the [pandoc-citeproc library](http://hackage.haskell.org/package/pandoc-citeproc), which can automatically generate citations and a bibliography in Pandoc-rendered documents using the Citation Style Language (CSL) files.

[Pandoc manual](https://pandoc.org/MANUAL.html) provides a detailed guide on how to use Pandoc. My baseline Pandoc command for conversion from an `.md` file to `.docx` file has the following structure:

~~~~

pandoc <document>.md --metadata-file=metadata.yml --bibliography=/home/<user>/.pandoc/bibliography/zotero_library.bib --csl=/home/<user>/.pandoc/csl/harvard.csl --reference-doc=/home/<user>/.pandoc/custom-reference.docx -s -o <document>.docx

~~~~

This will convert the `document.md` file, using my metadata YAML file, my Zotero library `.bib`, Harvard referencing style file and `custom-reference.docx` template, into a `document.docx` file (make sure to replace placeholder paths to files and file names with your own). Flag -s (or --standalone) produces an output that includes an appropriate header and footer, but the header and footer is already automatically included for some formats (including `.pdf`, `.docx` and `.odt`) and not for others (including HTML, LaTeX or `.rtf`). Flag -o indicates the output file.

A separate YAML metadata file is a relatively recent feature and might not work in older versions of Pandoc. Instead, you can write a YAML metadata block at the top of your text Markdown file. In fact, this is what I tend to do. In a YAML block, you can define many items, such as the font family, `.csl` style file and `.bib` file that will be used with the document. I tend to include only the front matter and retain flexibility with format elements by specifying them only when outputting in Pandoc. A typical YAML block of my article has the following structure:

~~~~
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
~~~~

Pandoc Manual has a more detailed explanation of [metadata blocks](https://pandoc.org/MANUAL.html#metadata-blocks) and [YAML metadata block](https://pandoc.org/MANUAL.html#extension-yaml_metadata_block).

Custom-reference.docx template file generated by Pandoc has a number of predefined styles to render your metadata, text structure and references. I have combined examples and tweaks I found online to create a .docx template that suits my needs. You can download it from [here](/files/custom-reference.docx). If you want to add a style that is not already defined by Pandoc and the template file, you need to edit a text in that custom style in your template file and then use the HTML style span tag around the relevant segment of text in your .md file to match that style. For example, for a custom style for keywords, I had to span the keywords in my Markdown text in the following way:

~~~~

<span custom-style=“Keywords”>**Keywords:** postdigital, digital economy, technocapitalism, liberal capitalist hegemony, the far-right</span>

~~~~

Pandoc generates PDF files using LaTeX and depends on a PDF engine installed on your system. The default LaTeX template produces beautiful PDFs. Plain HTML output, however, will be bare-bones and will require CSS or HTML5 templates to define the layout of the webpage. For more complex documents and uses, a good starting point is a repository with [user-contributed Pandoc templates](https://github.com/jgm/pandoc/wiki/User-contributed-templates).

#### Citation style language files

Markdown syntax for citation is `[@citationkey]`. Pandoc-citeproc will use the specified `.bib` file and citation format file to output citations and a bibliography in the desired form. Almost 10.000 `.csl` files for various referencing standards and publications-specific styles can be downloaded from the [Zotero Style Repository](https://www.zotero.org/styles). If your book or journal editor doesn't have a `.csl` file, you can try to detect what style the publication uses at the [Citation Style Language project](https://editor.citationstyles.org/). If it only approximates a style, you can edit an existing style to build a `.csl` file that matches the publication's style.

## 5) Revising

The downside of Markdown plain text and Pandoc workflow is that tracking changes and comments among versions cannot be practically done in a document as it can be done in LibreOffice, MS Word or Google Docs files. If you receive suggestions and comments in a `.docx` format, you can use Pandoc to convert a `.docx` version of your document back into `.md`, using the following command:

~~~~

pandoc -s <commented-document>.docx --wrap=none --track-changes=all --atx-headers -o <commented-document>.md

~~~~

Option `--track-changes` can have three values: accept, reject and all. If we use 'all' to include all deletions, insertions and comments, thus replicating the 'show changes' function of a MS Word or LibreOffice, the results are underwhelming - there is so much noise from added inline code that it renders the Markdown document unreadable while also breaking a part of the syntax such as citation keys.

One course of action is to go through the suggested changes in the received `.docx` file and manually enter them into the original Markdown document. Another course of action is to run Pandoc conversion with the 'accept' option and then compare differences, merge them or edit the original with a tool such as [Meld](https://meldmerge.org/).

If your supervisors or editors want to see the changes you have made between two drafts, you can always output two versions of your `.md` file to a `.docx` or `.odt` and create a track-changes file with LibreOffice's ['compare document' function](https://help.libreoffice.org/Common/Comparing_Versions_of_a_Document). The same can be done for versions of PDFs - Timothée Poisot has an explanation of how to do that on [his blog](http://timotheepoisot.fr/2014/07/10/markdown-track-changes/).

## 6) Naming, storing and backing-up files

To organise my scholarship files, I divide my projects between the 'PhD' directory that includes not only the thesis but everything related to my PhD study, 'writing' directory that includes not only my writing but also my collaborative writing projects, 'web' directory that includes my static website, 'presentations' directory that includes my conference texts and slides, and 'technocapitalism' book project directory. Following useful advice of [Achintya Rao's PhD Starter Kit](https://raoofphysics.github.io/phd-starter-kit/#directory-structure), I have adopted a heterogenous yet consistent nomenclature for my directories and files. Directories and sub-directories are named differently, depending on what works best for my recall and for search, sorting and command-line operations: short memorable titles, priority sorting using numeral prefixes `01_`, `02_`, `03_`,..., and chronology sorting using [ISO Date Format](http://en.wikipedia.org/wiki/ISO_8601) prefix `YYYYMM_`.

Naming versions of a text as it undergoes revisions can be a cause for confusion and frustration. There are always small edits that happen between major drafts, and there are always small edits that happen after the final submission. Adding suffixes '`_v.1`, `_v.2`, `_v.3`...' or '`_draft_1,` `_draft_2`, `_draft_3`... `_final` can easily get out of hand. For this reason, I use Git to version, store and backup my writing.

#### Git, Gitlab and SparkleShare

[Git](https://git-scm.com/), a free software framework developed initially by Linus Torvalds, is a version control system for collaborative software development projects. Each of my five scholarship directories is a git directory that I keep synced with my online repository on [GitLab](https://gitlab.com/) ([GitHub](https://github.com) or [BitBucket](https://bitbucket.org/) should serve you equally). Extensive [Git documentation](https://git-scm.com/docs) is available from the Git project, a [handy quick overview of commands](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf) from the GitHub.

To initiate an existing project directory into a git directory, you have to execute the following sequence of commands:

~~~~
cd <localdir>
git init
git add .
git commit -m 'message'
git remote add origin <url>
git push -u origin master
~~~~

Before you do `git commit`, you should probably exclude all large and sensitive directories or files by creating a '.gitignore' file in the same directory, specifying in the file the path to documents you want to omit. The origin <url> you will obtain by creating a new project on GitLab (or GitHub if you use that).

Once you have created a remote repository, you will be syncing the changes you have made locally by executing the following sequence of commands:

``git add -all; git commit -m '<message for this revision>'; git push``

Changes in the remote repository that were made by your co-authors or collaborators you can sync to your local directory by doing:

``git pull``

The directory synced and backed up on your remote repository can always be copied to another computer locally by doing:

~~~~
mkdir <localdirectory>
git clone https://gitlab.com/USERNAME/PROJECT-NAME.git
~~~~

You can automate this process by using [SparkeShare](https://www.sparkleshare.org/), a git-based file-sharing application, that acts in a similar way to cloud storage applications like Dropbox or Google Drive, but uses a version repository of your choice for storage. After you have set up [SparkleShare](https://opensource.com/article/19/4/file-sharing-git), it runs as a daemon in your system tray keeping your .git directories synced locally and remotely. Note that version repositories are not good for storing large files and directories, but plain text and images that I use in my work are small enough.

### Backing-up the Zotero library

Zotero is central to my reading workflow, and the Zotero library directory contains annotated PDFs of almost everything I read. Its directory is both large and precious to me. Zotero.org account will back-up your references, but given the limited amount of storage offered by Zotero.org (300mb for free, up to 6GB under an inexpensive payment plan), I store a back-up of my Zotero library in the cloud using [rclone](https://rclone.org/), a command-line tool that lets you sync your local files and directories with a remote cloud destination. Although rclone has excellent documentation and assists in the setup through command line dialogues, there's also the [RcloneBrowser](https://martins.ninja/RcloneBrowser/) (a recent Ubuntu build can be found [here](https://www.ubuntuupdates.org/package/webupd8/bionic/main/base/rclone-browser)) that provides a graphical frontend for rclone.

## 7) Presentations and website

To create slide presentations with Markdown, I use [reveal-md](https://github.com/webpro/reveal-md) - a Markdown-oriented fork of [Reveal.js](https://github.com/hakimel/reveal.js/). Reveal.js is a highly capable framework for creating presentations in HTML, developed initially by [Hakim el Hattab](https://hakim.se/), and offering slick features such as nested slides, fragments, speaker notes and PDF export. To create my website with Markdown, I use [Nikola](https://getnikola.com/) static web generator, developed by Roberto Alsina.

#### Reveal-js and reveal-md

You can download and install Reveal.js from its [GitHub repository](https://github.com/hakimel/reveal.js/). Reveal.js slides can be written directly into the `index.html` file, either using HTML markup or Markdown. However, Reveal.js can load external Markdown files, a feature I find much more convenient for my workflow. It allows me to quickly transform the text of my talk that I have already written in Markdown into a slide show or conversely write my text as slide notes.

Reveal-md streamlines the integration of Reveal.js and external Markdown files. To install reveal-md follow the instructions on its [Github page](https://github.com/webpro/reveal-md). To create a presentation from my Markdown presentation document, I typically execute the following line from the folder where I hold my Markdown presentation file, the images it links to and my custom style-sheet files:

~~~~

reveal-md technologies_and_eclogical_transition.md --vertical-separator "\n--\n" --css black_custom.css

~~~~

By defining a vertical separator (in my case, two line breaks around two dashes), I enable nested slides. I also indicate a custom CSS file built from one of Reveal.js themes, but if you omit this option, it will use the default black theme - or you can use the option `--theme` to chose one of the other themes provided in the installation.

My presentation I have written in the `technologies_and_eclogical_transition.md` file. A typical slide segment has the following structure:

~~~~
---

# modeling the human needs within planetary boundaries

<img src="./raworth_embedding.png" height="400" />

<font size="4"> Kate Raworth, *Doughnut Economics: Seven Ways to Think Like a 21st-Century Economist*, 2017 </font>

Note: all economic processes are drawing on living matter, materials and energy from nature, transforming them from a more ordered state into a less ordered state, from a more usable condition to a less usable condition.

--
~~~~

Here `---` is the default separator for horizontal slides and `--` for vertical, i.e. nested slides that I have defined when executing my command. `#` defines the heading, `Note:` my slide note. Slide segments typically combine Markdown and HTML syntax, particularly when better control over the size of fonts and images is called for.

Reveal-md can also print slides to PDF:

~~~~

reveal-md technologies_and_eclogical_transition.md --vertical-separator "\n--\n" --css black_custom.css --print /tmp/test.pdf

~~~~

Reveal-md can be run from a Docker, generate a static website, and do a number of other things that are best explored on its [Github page](https://github.com/webpro/reveal-md).  

#### Nikola

[Nikola](https://getnikola.com/) (named after Nikola Tesla) is a static website generator comparable to [Jekyll](https://jekyllrb.com/) or [Hugo](https://gohugo.io/). Most of the online publishing frameworks such as Wordpress or Mediawiki use databases and web programming to generate the webpage for each visitor dynamically. Yet most of the content we publish on our websites is, in fact, meant to be static - every visitor is supposed to see the same content. Static website generators emerged in response to this mismatch and its consequences. With static websites, you generate the website locally and then upload it to the server. What goes in is Markdown, HTML and CSS, what goes on the server are only HTML files and the linked images and documents. This has substantial advantages: software updates by your online hosting service will not obsolete your website even if you stop updating it, websites are safer from attacks, they are far less resource hungry, they don't lock you in with a vendor. You can always move your HTML files to another server, no matter how big or small, no matter its setup. Static websites provide you with autonomy from platforms and lock-ins, while offering everything you might expect from a modern website: themes, blogs, tags, comments, RSS/Atom fees or social media integration.

[Nikola](https://getnikola.com/getting-started.html) is easy to install across all major operating systems. Once you've installed Nikola, you can initialise your website locally. A Nikola website can behave as primarily a blog or as a site. Nikola has an extensive [handbook](https://getnikola.com/handbook.html) providing you with all the ins and outs of installing Nikola, using the framework and defining the behaviour of your website.

I host my website on GitHub Pages, [using my domain](https://help.github.com/en/articles/using-a-custom-domain-with-github-pages), which costs me altogether the price of domain registration. This allows me to use Git to update the changes to my website. This is done with a single line of code run from my local Nikola website directory:

``nikola build; git add --all; git commit -m "`date`"; git push``

However, should GitHub ever terminate the service, I can always transfer the website elsewhere and use another protocol, as basic as FTP, to keep it online.

Essential for my purposes is that Nikola can use Pandoc to compile HTML. To use Pandoc as the compiler, go to the `conf.py` file located in the local Nikola website directory, uncomment the [following line in the list of compilers] (https://getnikola.com/listings/conf.py.html#listingsconfpy-305) and set the [PANDOC_OPTIONS](https://getnikola.com/listings/conf.py.html#listingsconfpy-1085). The options in my case read:

~~~~

PANDOC_OPTIONS = ['--toc', '--template=/home/<user>/.pandoc/templates/html_nikola.template', '-t', 'html5', '--filter', 'pandoc-citeproc', '--bibliography=/home/<user>/.pandoc/bibliography/zotero_library.bib', '--csl=/home/coyu3/.pandoc/csl/harvard-coventry-university.csl' ]

~~~~

Pandoc here uses a custom template created by my collaborator Marcell Mars to deal with some of my additional front matter. Nikola already offers a number of [metadata entries](https://getnikola.com/handbook.html#id18). By default, it uses reST comments, but you can [easily change that setting into YAML](https://getnikola.com/listings/conf.py.html#listingsconfpy-317) in the `conf.py` file. My template file adds to existing metadata affiliation for the authors, article abstract, and article lead. The file is available [here](/html_nikola.template).

On some of the pages on my website, including this one, I have Hypothesis installed. To add Hypothesis script to a page, you need to add the following code after your metadata entry:

~~~~

<script type="application/json" class="js-hypothesis-config">

{"showHighlights": false}

</script>

<script src="https://hypothes.is/embed.js" async></script>

~~~~

To improve how pages and posts are shared on Facebook or Twitter, it is necessary to include a preview image. This is done by placing an image of optimal size and use the 'previewimage' metadata element with the relative path to the image file (e.g `previewimage:/images/<filename>.jpg`). Before you share, it's best to go to Facebook's [Object Debugger](https://developers.facebook.com/tools/debug/og/object/) to test if the preview image works as expected.

To improve discoverability and ranking of your pages and posts on search engines, add in the 'description' metadata element of each Nikola page or blog post a short description of its content that best matches potential searches.

Finally, to add Google Analytics to your Nikola, you have to uncomment the [BODY_END line](https://getnikola.com/listings/conf.py.html#listingsconfpy-1204) in you `conf.py` file and enter the following code:

~~~~

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

~~~~

For more customisations and tweaks, [Nikola docmentation](https://getnikola.com/documentation.html) offers a plenitude of resources, but you can also find on the web examples of Nikola-powered website customisations such as this highly resourceful [Lois Tiao's blog post](http://louistiao.me/posts/how-i-customized-my-nikola-powered-site/).

**Further reading:**
