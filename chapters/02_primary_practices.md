Primary Practices
=================

This chapter covers primary practices for reproducibility. At DataLab, we adopt
these practices for every project, and we recommend that you do too.  They'll
ensure that you can work on projects efficiently, without being slowed down by
trying to remember what you did last week, find that one file with the code
that actually works, or reorganizing your project so that it isn't embarrassing
to share with a collaborator.

Of the five reproducibility principles introduced in {numref}`Chapter %s
<introduction>`, only four appear here: documentation, artifact preservation,
project organization, and workflow automation. The first three of these are the
most critical principles. Neglecting them can make your projects impenetrable
to other people---and in some cases, even to future you. The subsequent
chapters will address the remaining principle: environment management.

For all of the practices listed in this chapter, the benefits far outweigh the
costs. Most of them are practices you can adopt immediately, with minimal
training. Eventually, they become good habits that you don't even have to think
about. There are two practices listed here---version control
({numref}`use-version-control`) and computing with code
({numref}`use-a-programming-language`)---that do require substantial effort to
learn and use. However, they provide benefits for reproducibility,
collaboration, and distribution that we consider well worth the cost.


Documentation
-------------

<!--
Documentation explains how a project works, the assumptions the project makes,
and how to actually use the included artifacts (data, code, figures, etc.). 
-->

> Writing is a primary mechanism for *doing* research, not just for reporting
> it.
>
> – paraphrased from [Simon Peyton Jones][peyton-jones], computer scientist

[peyton-jones]: https://simon.peytonjones.org/


### Start with the Scope

At the beginning of a project, write a **scope document** or research proposal
to lay out the research question and goals. The funding mechanisms in your
discipline may require this, but even if they don't, it's a excellent way to
clarify what you're trying to achieve and can help you identify potential
problems or gaps in reasoning early. The scope document will help you stay
focused and organized as you work. Later on, it can help you and your
collaborators understand the history of the project.

This is also a good time to establish a timeline with milestones you'd like to
reach. The milestones should be specific, measurable, and concrete, so that you
can easily tell when you've completed one. Be generous with yourself and your
collaborators: it can be hard to predict the directions research will take you,
and tasks that seem short (especially programming tasks) can end up taking
longer than expected. It's almost always better to finish things earlier than
planned rather than later.

For projects which involve data analysis, investigate potential data sources.
Sometimes a data set can sound promising, but lack the features you need, have
too few observations, or have too much missing data. If you'll collect the data
yourself, make a plan for data collection. You should have a clear picture of
which data sets will be available at the analysis stage and how they will be
structured. Pay particular attention to whether there are any biases, ethical
concerns, privacy concerns, licensing fees, or other issues.

:::{tip}
If you use spreadsheet software like Microsoft Excel or Google Sheets to
collect or analyze data, check out DataLab's [Excelling with Excel workshop
reader][datalab-excel] to learn how to keep your data neat and tidy.

To level-up your reproducibility, consider using a programming language like R
or Python to analyze data instead. Analyses you carry out in a spreadsheet can
be difficult for others to reproduce unless you meticulously document every
step. When you write code, anyone you share that code with can repeat your
steps.

If you need to store a lot of data, especially many different closely related
tables, consider using a {ref}`database<databases>` to store the data.
:::

[datalab-excel]: https://ucdavisdatalab.github.io/workshop_keeping_data_tidy/


(keep-running-notes)=
### Keep Running Notes

Set up one or more running notes documents when you set up your project. Use
the notes to keep track of things you've tried, things you want to try,
relevant references, and more. If you're working alone, these notes are just
for you---think of them as an external hard drive for your brain. Organize the
notes in whatever way works best for you. One thing that can be helpful is to
include the date whenever you add to the notes.


Whether you take notes on paper or digitally, the important thing is that you
take notes. Paper notes are convenient for diagramming and doodling, and can be
digitized after the fact to share with the team. Digital notes are convenient
for collaborating with team members who aren't physically present, and can be
shared as they are being written. When you start a notes document, make sure to
consider whether you'll need to include figures, code, or other media, and
choose an appropriate format. At DataLab, we frequently use paper notes, Google
Docs, and [Markdown][].

[Markdown]: https://commonmark.org/


#### For Collaborations

If you have collaborators, take notes about your meetings. Record anything
there's a chance you'll want to remember later: results (positive or negative),
new ideas, new leads, decisions, changes of plan, action items, and scheduling
details.

Consider what note-taking method works best for everyone. Some people like to
take notes during meetings, while others prefer to take summary notes
immediately after, so that they can be fully engaged. Collaborating on notes or
rotating who takes notes in each meeting can help lessen the burden, but having
a designated note-taker can help ensure consistency.

It's usually a good idea to share the notes with everyone who attended the
meeting, so that misunderstandings can be corrected quickly. You can do this by
having a shared notes document or by sending out the notes after each meeting.
If you use a shared notes document, make sure it's in a format everyone can
access and edit; some collaborators may not be comfortable working with
Markdown or other plain-text formats.

### Citation Managers
You will likely find a great deal of literature (journal articles, reports, etc.)
that you will need to keep organized. Citation managers (like Zotero, EndNote,
Lean Library, and many others) can help with this. Modern citation managers have
browser extensions that can pull articles right from your web browser into your citation manager
in a single click. They also offer a variety of oraganizational techniques ranging from
collection folders to tagging systems. Most also integrate with Microsoft Word, Google Docs, 
or LibreOffice to help manage your bibliography while writing. They aren't perfect and 
you need to check their work but they can save you a lot of time. They also assist with 
collaborations because you can have a shared library with collaborators
that you can all add papers too.

You can learn more about the citation managers available at UCD [here][citation_managers]. They all have pros and cons.
 And if you need support choosing or working with one you can [consult with a librarian][research_consultation] anytime!

```{tip}
While there are several free options listed on the Library guide, note that Zotero is an open source tool.
That means that Zotero will travel with you if/when you leave UC Davis. Also see the <INSERT LINK TO OPEN SOURCE SECTION> for
more information about why open source tools are preferred for reproducibility.
```

[citation_managers]: https://library.ucdavis.edu/citations/citation-management-tools/
[research_consultation]: https://library.ucdavis.edu/schedule-a-research-consultation/ 



(write-readmes)=
### Write READMEs

:::{margin}
```{note}
A **directory** or folder is a container for files (and other directories) on a
computer's file system. It can be helpful to think of directories like folders
in a filing cabinet.
```
:::

A **README** is a document that introduces and explains a project or directory
within a project. READMEs should generally be plain-text (`.txt`) or Markdown
(`.md`) files, because these are non-proprietary formats accessible to anyone
with a text editor. READMEs help people---including future you---find and use
your project.

```{tip}
Each time you start a new project, create a new directory for the project. Use
this **project directory** to store all files related to the project. This
directory is sometimes also called the **top-level** directory for the project,
since all files for the project exist beneath it.

{numref}`establish-directory-structure` elaborates on this idea.
```

A project should always have a README in the top-level directory to serve as an
introduction. The top-level README will often be the first thing someone new to
the project sees. At a minimum, the top-level README should contain:

* The project title
* A brief description of the project
* A list of the contributors and their affiliations
* A primary contact (typically a name and email address)
* A list of links to other project resources, including data sets and papers,
  which are stored separately
* A {ref}`manifest that describes the files and directories<file-manifests>`

For projects with data or code, the top-level README should also contain
instructions for installation and use (more about this in {numref}`workflows`).

:::{margin}
```{note}
A directory structure is **shallow** if there are not many sub-directories.
```
:::

A top-level README is usually sufficient documentation for projects with a
shallow directory structure and where methodology is published elsewhere (such
as journal articles or technical reports). For projects with a deep directory
structure, additional READMEs in important directories can be helpful for
understanding where files are. For projects with technical details that are not
explained elsewhere, it's a good idea to provide additional documentation in
the form of READMEs or other files.

:::{seealso}
See DataLab's [README, Write Me! workshop reader][datalab-readme] for more
about how to write READMEs.
:::

[datalab-readme]: https://ucdavisdatalab.github.io/workshop_how-to-data-documentation/

(file-manifests)=
#### File Manifests

A **file manifest** is a description of the files and directories in a project.
For intuition, think of a shipping manifest on a box sent to you in the mail. A
file manifest serves two important purposes:

1. It describes which files and directories are supposed to be included with
   the project. If you, a collaborator, or an outside researcher thinks they
   might be missing a file, consulting the file manifest is one way they can
   check.
2. It documents the purpose of each directory (and often, each file).

A good file manifest lists files and directories in alphabetical order, with
the exception that sometimes listing all of the directories first is clearer.
A manifest should also show the directory hierarchy through indentation,
symbols, or both. Here's an example of a manifest from a DataLab project:

```
data/           Models and images
docs/           Notes on the project as well as environment setup
log/            Slurm log files
src/            Image preprocessing, model training, and analysis
STEGO/          Code for creating STEGO models
tests/          Scripts for testing workflows, examining outputs, etc.
toy_data/       Very (very!) small pieces of data for dev testing
```

If a directory contains many files or subdirectories, consider whether it's
clearer to write a separate manifest specifically for that directory.


(workflows)=
## Document the Workflows & Code

> Suppose you're working on a study of passenger rail systems in the United
> States. You use 3 scripts to produce plots that summarize how often trains
> are late and how late they are for various cities. The scripts must be run in
> a specific order and with specific arguments. A new student is about to join
> the project, and you need to make sure they're able to run the scripts and
> make the plots.

A **workflow** is a way of using your project. Often this will be a series of
commands you can run to produce a specific output. Remembering the order in
which to run commands and the settings for each one might seem easy while your
project only has a few workflows and you use them frequently. If your project
grows or you spend time away from it, you may find it much harder to remember
what to do. Moreover, your collaborators may have a hard time remembering how
to run a workflow you set up, and vice-versa. Thus it's important to document
your project's workflows.

There's one workflow that's essential to almost every project: downloading the
files and installing the necessary software. It's a good idea to provide
step-by-step installation instructions in your project's top-level README, even
if you're the only one working on the project. Installation instructions are
invaluable if you ever have to switch to a different computer or reactivate a
project you haven't worked on for a few months.

:::{note}
As an example, see the [installation instructions for fd][fd-install], a
popular command-line tool for finding files.
:::

[fd-install]: https://github.com/sharkdp/fd#installation

Besides installation, you should also document workflows for using your
project. Explain the different ways to use your project, the settings
available, and common patterns of use. If your project contains mostly data
rather than code, explain how the data were collected, how they can be used,
built-in assumptions, and limitations.

:::{note}
As an example, see the [user guide for ripgrep][rg-user-guide], a popular
command-line tool for searching within files.
:::

[rg-user-guide]: https://github.com/BurntSushi/ripgrep/blob/master/GUIDE.md

Documenting workflows is important for reproducibility because it enables you
and other people to repeat commands you used to get a particular output.
Workflow automation practices (see {ref}`FIXME`) take this a step further by
bundling all of the commands in a workflow into a single command.


### Make Workflow Diagrams

Workflows with multiple interdependent tasks can be confusing, especially for
people new to a project. Diagrams that lay out the sequence of and
relationships between inputs, tasks, and outputs (as a graph, network, or flow
chart) make understanding and using these workflows easier and faster. For
instance, if you can't remember what the inputs are for a particular task, you
can simply glance at the diagram.

It's usually a good idea to make more than one workflow diagram. Use separate
diagrams for independent workflows, and make multiple diagrams at different
levels of abstraction. Diagrams at different levels are especially helpful for
explaining workflows where some of the steps are relatively complex in their
own right.

There many different ways to make workflow diagrams, including:

* Sketching the diagram freehand. This is a fast, easy way to make a diagram
  that doesn't require learning new tools. Depending on your sketching skills,
  the resulting diagrams might look rough or be difficult to read. You might
  sketch:
    * On paper or a whiteboard (and take photos), which is wonderfully easy,
      but can make editing later difficult.
    * On a tablet (or with a mouse), which requires drawing software, but makes
      it possible to collaborate from different locations and makes editing
      later easier.
* Designing the diagram in vector graphics software (such as [Lucidchart][] and
  [Inkscape][]). This works well for editing and collaborating and can produce
  presentation-quality diagrams. The drawbacks are that it requires everyone to
  have a license for and learn the software, and is generally more
  time-consuming than sketching.
    * Presentation software (such as [Google Slides][slides] and [LibreOffice
      Impress][impress]) are widely known and usually provide some support for
      designing diagrams.
* Describing the diagram in a graph language (such as [Mermaid][] and
  [Graphviz][]). This works well for editing and collaborating and can produce
  presentation-quality diagrams. It's more time-consuming than sketching but
  can be less time-consuming than vector graphics software. GitHub and other
  Git hosts often have built-in support for Mermaid. The drawbacks are that you
  have to (learn and) use yet another language, and you have less control over
  how the diagram is drawn and laid out.

[Lucidchart]: https://www.lucidchart.com/
[Inkscape]: https://inkscape.org/
[slides]: https://workspace.google.com/products/slides/
[impress]: https://www.libreoffice.org/discover/impress/
[Mermaid]: https://mermaid.js.org/
[Graphviz]: https://graphviz.org/

DataLab uses a mix of sketching, Lucidchart, Inkscape, and Mermaid, depending
on the complexity of the diagram, who will see it, and other needs of the
project. In general, you should choose whatever diagramming method works best
for you (and your team)---making the diagrams is more important than how you
make them.

:::{seealso}
See DataLab's [README, Write Me! workshop reader][datalab-readme] for
suggestions about how to create workflow diagrams.
:::

### Make a Data Management Plan
Increasingly, funders are requiring Data Managment and Sharing Plans (DMSPs) as a condition 
of funding. Beyond being a necessity for grants, these are also an excellent reproducibility 
practice and should be implemented regardless of funder requirements. Ideally, you should make your plan as early in your research process as possible. 
If you haven't collected any data yet, you can create "dummy" or "hypothetical" data for your project to help you think through the data management process.
We often think of "data" as numbers in a spreadsheet, but you should take a broad view of "data". 
Field notebooks, conceptual sketches, interview transcripts, photographs, and many other items 
often can and should be considered "data" as well.

:::{important}
Many projects (such as those with personal health data or other sensitive information) require 
extra consideration when developing your DMSP. You must consider things like deidentification of data, 
secure storage, and other privasy considerations. Learn more on the Library [Research Data Management Guide][rdmguide_privacy] 
or [consult with a librarian][rdm_email]!

[rdmguide_privacy]: https://guides.library.ucdavis.edu/data-management/confidentiality
:::

Some general considerations when starting a data management plan would be to ask yourself questions about the data:
* What sort of data will be generated?
	* Numbers in spreadsheets, images, recordings, etc.
* How much data will be generated?
	* A handful of spreadsheets? Hundreds of csv files? Millions of rows?
* How much space will the data take?
	* Megabytes? Gigabytes? Terrabytes?
* What is the cost/ability of replace lost data?
	* Can you rerun the experiment or reinterview a subject? Or is it a one time chance?
* What do people (or future you) need to understand about your data to work with it?
	* Units? Logical structure? Metadata and Documentation?
* Who will be responsible for the data?
	* Consider both in the short-term and the long-term.
 * How will you backup the data during the project?
    * Frequency? Responsible Party? Location? Risk Tolerance?
 * Will you need/want to share the data?
    * With who? Are there restrictions? How will it be found? 

:::{seealso}
See the [Research Data Managment Guide][libguide-dmp] for instructions
about how to make a data management plan or the Library .
Ask the Library's [Research Data Managment Team][rdm_email] for questions or conusltations.

You may also find these external guides useful:
* [Harvard DMSP Guide][harvard_guide]
* [National Library of Medicine DMSP Guide][nlm_rdm]
* [MIT Libraries Data Managment Guide][mit_dmp]
* [DMPTool Guidance][dmp_guide]
* [Digital Curation Centre DMSP Guide][dcc_guide]

[harvard_guide]:[https://datamanagement.hms.harvard.edu/plan-design/data-management-and-sharing-plan]
[nlm_rdm]:https://www.nnlm.gov/guides/data-glossary/data-management-plan
[mit_dmp]:https://libraries.mit.edu/data-management/plan/write/
[dmp_guide]: https://dmptool.org/general_guidance
[dcc_guide]:https://www.dcc.ac.uk/dmps

:::
[rdm_email]: dataservices@ucdavis.edu
[libguide-dmp]: https://guides.library.ucdavis.edu/data-management/planning

### Document the Code

Provide documentation for your project's code. Think about how people
(including you) will typically use the code. Will they:

* Run entire scripts?
* Call individual functions?
* Import your code as a package?
* Do something else?
* Do some combination of these?

The point of the documentation is to help other people reproduce the typical
workflows. Even if you {ref}`sec-use-a-task-runner`, documentation is important
to help people understand what each workflow does and how it works.

Use READMEs to summarize the code's purpose, intended use cases, and
organization across files. See {ref}`FIXME` for more about how to write
READMEs.

Most programming languages support comments as a way to intersperse
documentation with code. Use comments to explain, in natural language, what
your code is meant to do. This is especially important for parts of the code
that are terse, complicated, or potentially counter-intuitive. An excellent
programming strategy is to first write comments outlining the steps you want to
complete, and then fill in the code between the comments; this strategy is a
form of **[literate programming][lit]**.

[lit]: https://en.wikipedia.org/wiki/Literate_programming

Place comments at the beginning of each code file to explain the file's
purpose, inputs, assumptions, outputs, and any pitfalls. If the code is
organized into functions, do the same for each function. Some programming
languages have syntax or packages specifically for writing this kind of
documentation. These tools typically enforce some kind of organization and
remind you about important details to include. They can also make it easier for
others to find your documentation by making it available through the language's
built-in help system. Python's [docstrings][] and R's [roxygen2][] package are
examples of such tools. This kind of documentation is essential if you plan to
package your code and/or release it to a wider audience.

[docstrings]: https://peps.python.org/pep-0257/#what-is-a-docstring
[roxygen2]: https://roxygen2.r-lib.org/


Artifact Preservation
---------------------

### Make Backups

Hard drives can and do fail. Store at least one backup copy of each project on
a different computer, on an external hard drive, or in the cloud. This way, if
your hard drive stops working, you won't lose everything. Make a schedule for
when you'll update the backups, either daily or weekly, and stick to it.

:::{important}
For projects which involve data, it's especially important to keep backup
copies of the original or source data sets. This way you can experiment with
multiple approaches to data processing and can recover if you accidentally
corrupt or delete a data set.
:::

Cloud services such as [Google Drive][gdrive], [Dropbox][], [Box][], and
[OneDrive][] are convenient for backups because you can also easily share the
files with collaborators. If you {ref}`use-version-control`, then [GitHub][],
[BitBucket][], or [GitLab][] are similarly convenient. If your project has
specific privacy requirements, be careful to make sure they're satisfied when
choosing a cloud service.

:::{seealso}
See the UC Davis Library's [Research Data Management Guide][library-rdm-backups] section on backups for more comprehensive guidance on the topic.

[library-rdm-backups]: https://guides.library.ucdavis.edu/data-management/storage
:::

[gdrive]: https://drive.google.com/
[Dropbox]: https://www.dropbox.com/
[Box]: https://www.box.com/
[OneDrive]: https://onedrive.com/
[GitHub]: https://github.com/
[BitBucket]: https://bitbucket.org/
[GitLab]: https://about.gitlab.com/



(use-version-control)=
### Use Version Control

A **version control system** is a system for tracking changes to documents,
code, or other data. You may already use copies of files with different names
as a kind of ad-hoc version control: `essay.doc`, `essay_edited.doc`,
`essay_final.doc`, `essay_final_for_real.doc`, and so on. A more consistent and
less error-prone approach is to use software specifically designed for version
control. In computing contexts, when people say "version control," it's often
implied that they mean version control software. In addition to helping you
keep track of different versions of files, most modern version control software
can also help you share and collaborate on files with others.


#### For Documents

Cloud-based office suites such as Microsoft 365 and Google Office have version
control built-in. Consult the documentation for your preferred office suite to
learn more. A disadvantage of these services is that they typically save
documents in proprietary formats that may not be accessible to some people, and
they do not necessarily preserve version information when you download a
document from the cloud. For an open-source, desktop-based alternative,
consider using [LibreOffice][], which also has version control built-in.

[LibreOffice]: https://www.libreoffice.org/

[Markdown][] provides basic formatting options, is supported by a wide variety
of editors and platforms, and can be used to produce publication-quality
documents with open-source tools like [Pandoc][]. Because Markdown is a
plain-text format, anyone with a text editor can read a Markdown document, and
you can manage versions with the same version control systems available for
code. For a more richer markup language that produces publication-quality
documents out-of-the-box, but has many of the same advantages as Markdown,
consider [LaTeX][].

[Pandoc]: https://pandoc.org/
[LaTeX]: https://www.latex-project.org/

#### For Code

Version control systems for code first appeared in the 1960s and are now widely
considered an essential part of every programmer's toolkit. One reason for this
is that code is usually developed incrementally: you write code for a new
feature, run tests to make sure it works, make corrections, and repeat, until
you can move on to the next feature. Occasionally, you might start to develop a
feature and then realize that it just won't work or that it isn't worth the
effort. In that situation, it's important to be able to go back to the most
recent version of the code before you started working on the feature---which is
exactly what version control allows you to do. If you suspect that some changes
to your code introduced a bug, you can also use version control to isolate the
changes that caused the bug by testing earlier versions. These capabilities
also make version control well-suited to research, because you never know when
you'll need to re-run an old experiment or hit a dead end on a particular line
of investigation.

Many different version control systems exist, but a [recent StackOverflow
survey][so-vcs-survey] found that about 93% of developers use [Git][], an
open-source distributed version control system. "Distributed" means that Git is
flexible about where you store your code: there can be copies of the code on
your laptop, on a private server, on a hosting service like [GitHub][], and on
your collaborators' laptops, and Git will help you keep all of them in
sync---if that's what you want. DataLab uses Git for all of our projects, and
recommends that you do too.

[so-vcs-survey]: https://stackoverflow.blog/2023/01/09/beyond-git-the-other-version-control-systems-developers-use/
[Git]: https://git-scm.com/


:::{seealso}
See DataLab's [Introduction to Version Control workshop reader][intro-vcs] for
a technical introduction to version control with Git.

[intro-vcs]: https://ucdavisdatalab.github.io/workshop_reproducible_research/chapters/version-control/01_version-control-systems.html
:::


Project Organization
--------------------

### Use Naming Conventions

> There are only two hard things in Computer Science: cache invalidation and
> naming things.
>
> -- [Phil Karlton][phil-karlton], software engineer at Netscape

[phil-karlton]: https://www.karlton.org/

Names are the first thing you see when you skim through the files in a
directory or the expressions in a snippet of code. Well-chosen names serve as a
form of documentation, making it easier to guess the purpose of each file or
expression. With that in mind, naming things amounts to summarizing (often
complex) concepts in one or two words---so it's no surprise that it can be
challenging and easy to neglect.

Adopting a naming convention and following it consistently can ease some of the
burden of naming things by reducing the number of decisions you have to make.
Different contexts often benefit from different naming conventions. For
instance, it's usually a helpful to have separate naming conventions for files
and for code.


#### File and Directory Names

*Choose filenames that are human-readable, machine-readable, and have a meaningful order when sorted alphabetically.* 

The UC Davis Library [Research Data 
Managment Guide][rdm-guide-filenaming] provides an overview of these basic principles and how to apply them when naming your files and directories.

[rdm-guide-filenaming]: https://guides.library.ucdavis.edu/data-management/file-naming

For example, consider this project:
```{image} /images/AmandaUnorganizedProject.jpg
:alt: A diagram showing an unorganized directory structure for Amanda's Research Project.
:width: 600px
:align: center
```

```{dropdown} Text version of directory structure
* **Amanda's Research Project/**
    * **observations/**
        * 20121103_ra179.7dec12.1_g.fits
        * 20121103_ra179.7dec12.1_r.fits
        * 20121103_ra179.7dec12.1_spec.fits
        * 20121104_ra180.0dec12.1_g.fits
        * 20121104_ra180.0dec12.1_r.fits
        * 20121104_ra180.0dec12.1_spec.fits
        * galaxy1_g_crop.fits
        * galaxy1_r_crop.fits
        * galaxy1_spec_restframe.fits
        * galaxy2_g_crop.fits
        * galaxy2_r_crop.fits
        * galaxy2_spec_restframe.fits
    * 1303.7762.pdf
    * 2dfft.py
    * BHmass.py
    * E&M class notes
    * mass & pitch angle scatter.png
    * paper on mass estimates.pdf
    * redshift(z)histogram
    * results
    * spiral paper.pdf
```

This directory appears to have grown organically--there is no consistent file organization or naming convention. Because of that, it's not obvious what this project is about and what it contains. Many of the file names are unclear and would require additional context to understand their purpose (e.g., "spiral paper.pdf"). This makes it difficult for anyone interacting with the project to be able to find a file and know why and how to use it. The directory structure is shallow, meaning that files serving different purposes are interspersed together. Additionally, several file names include spaces and special characters, which can cause problems for those using the files with analysis and other software.


Here is a cleaned up version of this same project:
```{image} /images/AmandaCorrectedStructure.jpg
:alt: A diagram showing the directory structure for the BlackHoleMass project.
:width: 600px
:align: center
```

```{dropdown} Text version of directory structure
* **BlackHoleMass_SpiralGalaxy/**
  * **analysis/**
    * **plots/**
      * mass_pitchangle_scatter.png
      * redshift_histogram.png
    * 2dfft.py
    * BHmass.py
    * results.csv
    * README.txt
  * **data/**
    * **processed/**
      * galaxy1_g_crop.fits
      * galaxy1_r_crop.fits
      * galaxy1_spec_restframe.fits
      * galaxy2_g_crop.fits
      * galaxy2_r_crop.fits
      * galaxy2_spec_restframe.fits
      * README.txt
      * README_methods.txt
    * **raw/**
      * 20121103_ra179.7dec12.1_g.fits
      * 20121103_ra179.7dec12.1_r.fits
      * 20121103_ra179.7dec12.1_spec.fits
      * 20121104_ra180.0dec12.1_g.fits
      * 20121104_ra180.0dec12.1_r.fits
      * 20121104_ra180.0dec12.1_spec.fits
      * README.txt
  * **literature/**
    * BHmass_pitch.bib
    * KormandyHo2013.pdf
    * Lusso2010.pdf
    * Vertergaard2006.pdf
  * README.txt
```

We can see a number of changes and choices the project author made to the project to make it more human and machine readable. This new folder structure helps us better navigate and understand how files relate to one another. The the inclusion of README.txt files is also important, as they contain additional context regarding the contents, origin and purpose of the associated files. The author also changed the file names to be more machine readable ("mass & pitch angle scatter.png" to "mass_pitchangle_scatter.png") and added names that explain more about the contents of the file ("spiral paper.pdf" to "KormandyHo2013.pdf"). Even without a background in astronomical physics, it is much easier to understand the purpose of the files for the project.

Adapted from [Schilling, Amanda, et al. “Managing Research Files.” OSF, 7 Feb. 2025. Web.][ou-osf-files]

[ou-osf-files]: https://osf.io/ukq6b/overview

:::{tip}
Before starting your project, it's a good idea to check if there are any additional domain-specific file convenions. Data repositories often also require specific naming conventions, so if you know you will be depositing your data there it can save you time and headache to apply those conventions at the beginning of your project. Regardless, your file names should always be easy for you, your collaborators, and your computer to read.
:::

:::{seealso}
The rules in this section are based on Jenny Bryan's [How to Name Files
presentation][how-to-name-files].

Prefer an essay over a presentation? See Douglas MacDonald's [On Naming
Things][on-naming-things].
:::

[how-to-name-files]: https://github.com/jennybc/how-to-name-files
[on-naming-things]: https://www.douganddata.com/2022/07/on-naming-things/


#### Names in Code

Most programming languages have a **style guide** with standards for how to
format code, either officially or by community consensus. Following a style
guide helps make your code intelligible to other programmers. Style guides
usually include naming conventions, which tend to focus on how to capitalize
and delimit words in multi-word names. Three common formats for names are:

* `camelCase` delimits words by capitalizing the first letter of each word
* `snake_case` delimits words with underscores
* `kebab-case` delimits words with dashes

Some style guides use several different formats to distinguish between
different kinds of objects.

Among the languages widely used for data science:

* R doesn't have an official style guide, but the [Tidyverse style
  guide][tidy-style] is popular. It recommends `snake_case` for all names. In
  the past, `camelCase` and R's unique `dot.case` were also popular.
* Python has an [official style guide called PEP 8][pep-8]. It recommends
  `UpperCamelCase` for class names, `UPPER_SNAKE_CASE` for constants, and
  `snake_case` for all other names.
* Julia has an [official style guide][julia-style]. It recommends
  `UpperCamelCase` for module and type names, and `snake_case` for all other
  names.

[pep-8]: https://peps.python.org/pep-0008/
[tidy-style]: https://style.tidyverse.org/
[julia-style]: https://docs.julialang.org/en/v1/manual/style-guide/

:::{seealso}
Wikipedia's [naming conventions page][wiki-naming] describes the styles and
naming conventions for a wide variety of programming languages.
:::

[wiki-naming]: https://en.wikipedia.org/wiki/Naming_convention_(programming)

Besides how to format names in code, another detail to consider is how long
names should be. Longer names allow for richer descriptions, but can also make
code harder to read. Here's one code organization expert's recommendation:

> The length of variable names should be proportional to their scope. Big
> scopes imply long names.
>
> The length of function and class names should be inversely proportional to
> their scope. Small scopes imply long names.
>
> -- [Robert "Uncle Bob" Martin][bob-martin], software engineer and author

[bob-martin]: https://en.wikipedia.org/wiki/Robert_C._Martin

In other words, the longer a variable is in use, the longer its name should be.
The rationale is that if a variable is in use for a long time, expressions that
use the variable may be far away from its definition, making it harder to infer
the meaning from context. So don't hesitate to name a variable `x` if it will
only be used in a couple of expressions and there's not an obviously better
name, but avoid naming a variable `x` if it's going to be used repeatedly
throughout all of your code; choose a longer, more descriptive name.

:::{tip}
Some other naming conventions include:

* Use `i`, `j`, and `k` for indexes in loops.
* Use verbs (action words) in function names, because functions do things. For
  example: `read_data`, `add_offset`, `run_simulation`.
* Use `get_` and `set_` as prefixes for functions that get and set components
  of a data structure.
* Use `is_` or `has_` as prefixes for functions that return a Boolean value.
:::

:::{seealso}
See [How Patterns in Variable Names Can Make Code Easier to Read][how-patterns]
for Felienne Hermans' perspective as a computer science education researcher.
:::

[how-patterns]: https://youtu.be/z7w2lKG8zWM


(establish-directory-structure)=
### Establish a Directory Structure

Create a separate, dedicated directory, often called a **repository**, for each
of your projects. Store everything related to the project there. This will make
it easier to find files and also to share specific projects with others. Use
directories within each repository to further organize your files. At a
minimum, we recommend these directories:

* `data/` for data sets
* `docs/` for documents
* `src/` for code in scripts (such as `.R` or `.py` files). The abbreviation
  `src` is short for "source code". R scripts conventionally belong in `R/`
  instead, because of how R's packaging mechanisms work
* `notebooks/` for code in notebooks (such as RMarkdown or Jupyter notebooks)
* `outputs/` for results (data, models, figures, etc.)

Of course, if your project doesn't include any code then the `src/` and
`notebooks/` directories aren't necessary. If your project has lots of
outputs, it can also be helpful to replace or supplement the `outputs/`
directory with more specific directories such as `figures/` and `models/`.

These recommendations are not necessarily appropriate for every project. When
choosing a directory structure, consider the specific needs of your project,
your collaborators, and your audience. Make sure to document whatever directory
structure you decide to use in your project's README (see
{numref}`file-manifests`).

If your research is more qualitative in nature than quantitive, the same basic 
principles of organization apply. However the overall goal may be to show iterative 
analysis, reflection, and ethical managment of sensitive materials rather than rigid
data pipeline processng. For instance, your directory structure might include:

* `data/` which includes `interviews/`, `fieldnotes/`, and `documents/`
* `coding/` which includes `themes/` and `memos/`
* `outputs/` which includes `analysis_summaries/` and `reports/`

:::{seealso}
For more examples of directory structures, see:

* DataLab's [Project Template][datalab-template]
* [Cookiecutter Data Science][cookiecutter]
* The Turing Way's [Creating Project Repositories guide][turing-repo]
:::

[datalab-template]: https://github.com/datalab-dev/template_project
[cookiecutter]: https://github.com/drivendata/cookiecutter-data-science
[turing-repo]: https://the-turing-way.netlify.app/project-design/project-repo/project-repo-advanced

(organize-the-code)=
### Organize the Code

```{figure} /images/xkcd_goto.png
---
name: xkcd-goto
alt:
---
"goto" from ["xkcd"][xkcd] by Randall Munroe ([license][xkcd-license]).
```

Whenever you're about to write code, take time to think about what its purpose
is and how it will be used in the future. Clarity on these points can make it
easier to decide where to put the code, break down the programming problem, and
choose appropriate programming abstractions.

Is your code for a one-shot exploration, a prototype, or something highly
visual? Then it's probably a good idea to write and save your code in a
notebook format, such as [RMarkdown][], [Jupyter][], or [Quarto][]. Notebooks
display writing and results inline with code, so that you can try snippets of
code out, get immediate feedback, and take notes. Notebooks can also display
images, so you can inspect plots and other figures without opening another
window or file.

[RMarkdown]: https://rmarkdown.rstudio.com/
[Jupyter]: https://jupyter.org/
[Quarto]: https://quarto.org/


::::{grid}
:::{grid-item}
```{image} /images/logo_rmarkdown.png
:alt:
:width: 50%
:align: center
```
:::

:::{grid-item}
```{image} /images/logo_jupyter.svg
:alt:
:width: 50%
:align: center
```
:::

:::{grid-item}
```{image} /images/logo_quarto.svg
:alt:
:width: 50%
:align: center
```
:::
::::

On the other hand, if your code is likely to be reused many times over the
course of the project---and possibly in other projects or by other
people---then it's usually preferable to write and save your code in a script
format. Script formats are usually plain-text files with an extension like
`.R`, `.py`, or `.jl` to indicate the kind of code.

A mix of notebooks and scripts can be an effective way to solve programming
problems and develop code. Don't feel locked in to one or the other, and
remember that generally notebooks can load functions and other code from
scripts.

#### Write Functions

To solve problems efficiently and better organize your code, try to break
programming tasks into small, manageable steps. Use writing (for instance, in
comments) to clarify and plan the steps. For each step, write the code to solve
a few small, simple cases. Once the code for a step seems to work correctly,
turn it into a function. Start by identifying the inputs and outputs. These
become the parameters and return value, respectively. Test the function still
works on the small, simple cases. Then scale up to larger, more complex cases.
Edit the function and add parameters as necessary to make it work correctly for
the new test cases, making sure that it also continues to work correctly for
the old ones. When you have functions for all of the small steps, combine them
(usually in sequence) to handle the larger task.

:::{important}
How small is a "small step"? Small steps and functions should generally be
longer than a single expression---because in that case you might as well just
write the expression---and generally be shorter than one screen in your
editor---so that you can reason about what they do easily. Be flexible and
judicious with these guidelines; there are exceptions.

When you write small steps, you can try to break them down into smaller
sub-steps as well. The sub-steps are usually individual expressions.
:::

:::{tip}
It may be helpful to think of writing code or functions like writing an essay.
Start with an outline (describe the steps in comments). Sometimes the outline
will have multiple levels (sub-steps). Once you've written the outline, start
filling in the details (the code). As you write, you may occasionally need to
stop and adjust the outline as you uncover gaps in your reasoning.
:::

#### Make It Modular

Create separate scripts for separate parts of your project. For example, you
might have a script to clean the data, a script to train a model, a script to
generate predictions from the trained model, and a script to generate figures
summarizing the results. Dividing up responsibilities across multiple scripts
is helpful for isolating bugs and staying focused while you're working. Using
multiple scripts will also make it easier for you and your collaborators to
find things, provided the scripts have descriptive, unambiguous names.

Structure your scripts so that they're **modules**: collections of functions
that can be imported and used by other code. Avoid writing code outside of
functions, with one exception: to define a constants (named values that do not
change, such as pi). Doing this ensures that importing a script won't cause
hard-to-predict side effects.

If you want to be able to run a script from the command line, include a
function that serves as the entry point---the code that runs first. For many
programming languages, it's required or recommended to call this function
`main`. Regardless of what name you choose, use it consistently for the entry
point functions across all of your scripts.


<!--
See https://speakerdeck.com/jennybc/zen-and-the-art-of-workflow-maintenance?slide=56
-->
