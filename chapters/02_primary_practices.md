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


<!--
Documentation explains how a project works, the assumptions the project makes,
and how to actually use the included artifacts (data, code, figures, etc.). 
-->

> Writing is a primary mechanism for *doing* research, not just for reporting
> it.
>
> – paraphrased from [Simon Peyton Jones][peyton-jones], computer scientist

[peyton-jones]: https://simon.peytonjones.org/


## Start with the Scope

At the beginning of a project, write a **scoping document** or research proposal describing your research question and the goals. The process of writing this document is an excellent way to
clarify what you're trying to achieve, ensure alignment among your collaborators, and identify potential problems or gaps early when they can be more easily addressed. Depending on your specific funding mechanism and discipline, a scoping document may also be required before you begin collecting data. Later, once you have your data, this document can help you and your
collaborators explain the history of the project and the original reasoning for how you collected the data, your overall research design, and specific project goals.

Your scoping document can also be a powerful project management tool, helping you stay focused and organized as you work. It's a good idea to establish a timeline in your document that includes the milestones you'd like to
accomplish. The milestones should be specific, measurable, and concrete, so that you
can easily tell when you've completed one. Be generous with yourself and your
collaborators; it can be hard to predict the directions research will take you,
and tasks that seem short (especially programming tasks) can end up taking
longer than expected. It's almost always better to finish a deliverable earlier rather than having to pivot to accommodate delays.

For projects that involve data analysis, incorporate into your scoping process necessary time to investigate your planned data sources.
Sometimes a data set that seems promising can lack the exact features you need, have
too few observations, have too much missing data, or otherwise be untenable for your planned research. If you are collecting the data
yourself, make a plan for how you will collect the data. Describe what data sets will be available at the analysis stage, and how they will be recorded and need to be structured for analysis. Failure to do this may result in the need for extensive data restructuring or, in the worst case, unusable data.

During the process of writing your scoping document, consider whether there are any biases, ethical concerns, privacy concerns, licensing fees, or other issues that may influence your research. Include these, and how you will address them, in your research plan.

If you are submitting your scoping document as a grant or other formal research
proposal, the organization you submit to may have specific structure
requirements. If they don't, or if you aren't submitting your research proposal
anywhere, consider the following as a potential outline for a scoping document:

- **Collaborators:** Who is working on the project? Include where
  they work and how to get in touch with them. Typically this will include their email address.
- **Background Information:** What does someone need to know to understand the goals
  of the project?
- **Project Duration:** How long will the project take? 
- **Data:** What data sources will be used in the project? If there are ethical
  or privacy concerns about the data, outline them here and describe mitigation
  strategies. If you will be collecting data, what data will you collect and 
  how?
- **Statement of Work and Milestones:** Who will do what by when? This is a good 
  place to describe key deliverables and associated milestones you expect to accomplish, with
  approximately when they will be achieved.
- **Collaborator Responsibilities:** Additional responsibilities outside the 
  statement of work can go here, like who will complete periodic stakeholder updates and funder reports, or who brings the donuts to the team meetings. :) 
- **Project Deliverables:** What is the final product of the project? This could
  be a publication, website, piece of software, infographic, or something else
  entirely.
- **Ownership and Licensing of Work Products:** Many universities, publishers,
  and funders have requirements as to who owns research and how its products
  should be licensed. For more information about licensing at UC Davis, check
  out the [Open Source Program Office resources][ospo-licensing].  
- **Funding Sources and Pay Schedule:** If money is changing hands, it is a good
  idea to lay out the specifics of how that will happen.

Not every project will require every section. However, including more
information early on in a project will make your life easier down the line. In
general, reproducibility requires you to know what you did and when. While a
project proposal or scoping document will inevitably differ from what actually
happens, having a starting point will make reconstructing your research process
much easier. Additionally, don't hesitate to update your project prosposal as
things change. Updating your plan as you figure out what works and what doesn't
isn't a failing -- it's good research practice. And your project proposal can help
you keep track of those changes as you make them.
 

:::{tip}
When deciding how you will structure your data, it's helpful to review "tidy data" principles, especially if you are recording your data in spreadsheet software like Microsoft Excel or Google Sheets. Check out DataLab's [Excelling with Excel workshop
reader][datalab-excel] to learn how to keep your data neat and tidy.

To level-up your reproducibility, consider using an open source programming language like R
or Python to analyze your data. Analyses you carry out in a spreadsheet or graphical user interface (GUI) based program that involes a lot of pointing and clicking to set options for the analysis can
be difficult for others to reproduce even when you meticulously document every
step. The advantage of programming is that anyone you share your analysis code with should be able to exactly repeat the steps of your analysis.

If you need to store a lot of data, consider using a {ref}`database<databases>`. This is especially helpful when your data is stored in many different closely related
tables, or your datasheet is really wide with numerous columns containing repeated information. You can learn more about databases and data storage technologies in DataLab's [Overview of Databases and Data Storage workshop reader][datalab-database], and how to work with databases using a Structured Query Language (SQL) in DataLab's [Introduction to SQL for Querying Databases workshop reader][datalab-sql].
:::

[datalab-excel]: https://ucdavisdatalab.github.io/workshop_keeping_data_tidy/
[datalab-database]: https://ucdavisdatalab.github.io/workshop_intro_to_databases/
[datalab-sql]:https://ucdavisdatalab.github.io/workshop_intro_to_sql/
[ospo-licensing]: https://ucospo.net/oss-resources/#understanding-licensing--compliance


(keep-running-notes)=
## Keep a Research Log

> You're part of a lab working on a research project that began three years
> ago. When you were introducing a new graduate student to the project this
> morning, they asked whether the lab considered investigating treatment Z,
> because they've seen lots of excitement about it in recent literature. You
> remember mentioning treatment Z to the principal investigator a few years ago
> and eventually deciding not to pursue it, but can't remember when or why you
> made that decision. Now you're wondering whether your decision was too hasty
> and reviewers will question why treatment Z wasn't considered. If only you
> had detailed notes to refresh your memory as to why treatment Z isn't
> relevant.

A **research log** is a collection of running notes about your progress on your
research project. You can set up one or more notes documents when you set up
your project. Use the notes to keep track of things you've tried, things you
want to try, decisions, relevant references, and more. If you have
collaborators, take notes about your meetings. Record anything there's a chance
you'll want to remember later: results (positive or negative), new ideas, new
leads, decisions, changes of plan, action items, and scheduling details.

<!--
Whether you take notes on paper or digitally, the important thing is that you
take notes.
-->

When you start a notes document, make sure to consider whether you'll need to
include figures, code, or other media, and choose an appropriate format. Paper
notes are convenient for diagramming and doodling, and can be digitized after
the fact to share with the team. Digital notes are convenient for collaborating
with team members who aren't physically present, and can be shared as they are
being written.

:::{admonition} For Collaboration
:class: important
Put some thought into what note-taking methods work best for everyone engaged
with the project. It's good to share notes with the entire team, so that
everyone can contribute and misunderstandings can be corrected quickly, unless
your research topic or data require restricting access.

Take notes during meetings. Some people like to take notes during meetings,
while others prefer to take summary notes immediately after, so that they can
be fully engaged. Collaborating on notes or rotating who takes notes in each
meeting can help lessen the burden, but having a designated note-taker can help
ensure consistency.
:::

One way to keep your notes digitally is to use **electronic lab notebook**
(ELN) software, which provide a searchable interface for entering notes. Most
ELNs automatically capture metadata about notes, such as the date and time they
were written, and can also store experimental data. Some also have other
features, such as file storage and sharing, version control, and publishing
tools. Depending on your discipline and research topic, you might be expected
or required to use a specific ELN system.

:::{seealso}
See the [Electronic Lab Notebooks][ELN] section of the UC Davis Library's
Research Data Management guide to learn more about ELNs.

[ELN]: https://guides.library.ucdavis.edu/data-management/electronic-lab-notebooks
:::

Another way to keep notes digitally is to use **issue tracking** software.
Issue tracking software were originally created to keep track of and help
organize work to be done, or "issues", in (large) software development
projects. However, most work equally well for keeping track of work in
computational research projects. Services such as [GitHub][], [GitLab][], and
[Tangled][] provide issue tracking.

[Tangled]: https://tangled.org/

:::{seealso}
See the [Working with GitHub][issues] section of DataLab's Git for Teams
workshop reader to learn more about issue tracking.

[issues]: https://ucdavisdatalab.github.io/workshop_reproducible_research/chapters/git-for-teams/02_working-with-github.html
:::


(document-every-experiment)=
### Document Every Experiment

:::{note}
An "experiment" doesn't necessarily have to be an experiment done in a lab.
Doing an experiment could mean running a simulation, testing a model, or
something else.
:::

In your notes, keep a record of every experiment that you do. Document
parameters, the results, and anything else you think is relevant for:

* Repeating experiments in the future. Research projects are often
  iterative---you may need to repeat an experiment to make adjustments to a few
  parameters or because you discovered a bug in your code.

* Comparing across experiments. Think of the documentation as a high-level
  overview of your project. Use it to get a sense of which experiments had
  promising results, which didn't, and which you might want to try next.

* Avoiding redundant work. By keeping track of what's already been done, you
  can avoid accidentally and unnecessarily repeating an experiment that you or
  your collaborators have already done.

Get in the habit of recording experiments as soon as you start to plan them,
and recording the results as soon as they finish. Assign a unique name or
number to each experiment so that you can reference specific experiments in
your other notes and files. If you have collaborators, make sure they can
access the documentation and understand how to use it.

:::{tip}
ELNs or spreadsheets are often a good format for this kind of documentation,
since they're convenient for data entry.
:::

## Citation Managers
You will likely find a great deal of literature (journal articles, reports, etc.)
that you will need to keep organized. Citation managers (like Zotero, EndNote,
Lean Library, and many others) can help with this. Modern citation managers have
browser extensions that can pull articles right from your web browser into your citation manager
in a single click. They also offer a variety of oraganizational techniques ranging from
collection folders to tagging systems. Most also integrate with Microsoft Word, Google Docs, 
or LibreOffice to help manage your bibliography while writing. They aren't perfect and 
you need to check their work but they can save you a lot of time. They also assist with 
collaborations because you can have a shared library with collaborators
that you can all add papers to.

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
## Write READMEs

:::{margin}
```{note}
A **directory** is a container for the files on your computer. It can be helpful to think of directories like the folders in a filing cabinet. Keeping your file system organized is important because it makes finding and accessing a specific file a lot easier, and enables you to more easily backup and share your work on a project. A directory can have multiple directories nested within it, which further helps keep the different files, such as your documents and datasets, organized. For example, your "research project" directory may contain "documentation", "data", and "code" directories that each contain the relative files for your project. For more tips about organizing your digital files, see the [UC Davis Library Research Data Management Guide on Directory Structures][libguide-directory]
```
:::

[libguide-directory]: https://guides.library.ucdavis.edu/data-management/directories

A **README** is one of the most important documents in your research project. The README introduces and explains a project, or the contents of a specific directory
within a project. READMEs should generally be plain-text (`.txt`) or Markdown
(`.md`) file format because these are non-proprietary formats meaning they are accessible to anyone
with a text editor regardless of their operating system and environment. READMEs help people---including future you---discover, understand, and use
your project. Thus READMEs are one of the most important documents you can write to make your work reproducible.

```{tip}
Each time you start a new project, create a new directory for the project. Use
this **project directory** to store all files related to the project. This
directory is sometimes also called the **top-level** directory for the project,
since all other directories and files for the project exist beneath it.

{numref}`establish-directory-structure` elaborates on this idea.
```

A project should always have a README in the top-level directory that serves as an
introduction to the entire research project. This top-level README will often be the first thing someone new to
the project sees. At a minimum, the top-level README should contain:

* The project title
* A brief description of the project
* A list of the project contributors and their affiliations
* A primary contact (typically a name and email address)
* A {ref}`manifest that describes the files and directories<file-manifests>`
* A list of links to any other project resources, including data sets and papers,
  that are stored or accessed separately

For projects with data or code, the top-level README should also contain
instructions for relevant software installation and code use. To learn more about this see {numref}`workflows`).

:::{margin}
```{note}
A directory structure is **shallow** if there are not many sub-directories. 
```
:::

A top-level README is usually sufficient documentation for projects with a
shallow directory structure, and where the methodology is published elsewhere (such
as in linkable journal articles or technical reports). For projects with a deep directory
structure, additional READMEs in important directories can be helpful for
navigating their contents. For projects with technical details that are not
explained elsewhere, it's a good idea to provide additional documentation in
the form of READMEs or other files, such as file manifests and data dictionaries (see below).

:::{seealso}
See DataLab's [README, Write Me! workshop reader][datalab-readme] for more
about how to write READMEs.
:::

[datalab-readme]: https://ucdavisdatalab.github.io/workshop_how-to-data-documentation/


(file-manifests)=
### File Manifests

It's good practice to include a file manifest in your project README, and whenever you share files. A **file manifest** is a description of the files and directories in a project.
This list is analogous to the shipping manifest on a box your receive in the mail. Just as the shipping manifest lists all the items in the box, the file manifest lists all files in a project directory. A
file manifest serves two important purposes:

1. It describes which files and directories are supposed to be included with
   the project. If you, a collaborator, or an outside researcher thinks they
   might be missing a file, consulting the file manifest is one way they can
   verify this.
2. It documents the purpose of each directory (and often, each file).

A good file manifest will list the directories in alphabetical order, followed by all files in alphabetical order. A manifest should also show the directory hierarchy through indentation,
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

If a directory contains many files or subdirectories, you might consider writing a separate file manifest specifically for that directory.

## Document the Data

**Metadata**, or data that describes data, is critical to the research process.
It delineates how the data were collected, what assumptions were made, what
biases might be present, any ethical concerns, the overall structure, what each
observation means, what each feature means, and more. Good data
documentation guides researchers towards appropriate, responsible use of the
data for both the current and future studies.

Good metadata should answer the questions who, what, when, where, why, and
how about your data. How your metadata answers these questions will
depend on conventions in your field of research. If you are submitting your data
to a particular data repository, it will likely have a required metadata scheme
you will need to follow. Otherwise, pick a metadata scheme that aligns with
other researchers in your field. If you have to submit a Data Management Plan,
it will specifically ask how you will apply and adhere to field specific data
standards. For more information about Data Management Plans, see the UC Davis
Library's [Data Management Research Guide][lib-dmp] and the California 
Digital Library's [DMPTool][]

If you aren't sure what the standard is in your field, there are several online
repositories to help you out. The [Metadata Standards Catalog][msc] has a fairly
exhaustive list of metadata schemes, which you can browse [by
subject][msc-subject]. [Fairsharing.org][fairshare] also stores metadata and
other documentation standards. By using an existing community standard metadata
scheme, you make it possible for future researchers (including you!) to compare
your data to data from other, heterogeneous, sources.

```{note}
Many metadata resources include a **[controlled
vocabulary][c-vocab]**. This is a list of specific values, each with a
predefined meaning. It is designed to provide consistency and uniqueness across
data sources. One common example of a controlled vocabulary is a list of
geographic names, like the [Thesaurus of Geographic Names (TGN)][tgn]. There are
many ways you can refer to New York City (NYC, the Big Apple, Manhattan etc).
But if you want to be able to group together all data about New York City, it is
helpful if everyone calls it the same thing.
```

Even if you don't know where your data will end up, documenting your data when
you collect it will help ensure your documentation doesn't have any gaps. Timely
documentation also maximizes the likelihood that your research can be
reproduced, as well as reused by other researchers increasing your overall
research impact. If your project uses data collected earlier or by someone else,
it's a good practice to fill gaps in the existing documentation with your own.
Thorough documentation isn't just beneficial to other researchers, it's also
beneficial to future you. Small details you notice and document can be important
later in the project.

```{figure} /images/michener_information_entropy.png
---
name: information-entropy
figwidth: 550px
align: center
alt: 
---
Information Entropy (Figure 1) from ([Michener et al. 1997][michener]) &copy; 
1997 by the Ecological Society of America.
```

:::{note}
One of the simplest and most widely used metadata standards is the [Dublin
Core][dublin-core], a set of 15 metadata elements originally defined at a 1995
workshop in Dublin, Ohio. The exact definition of the Dublin Core elements can
be a bit technical, but the University College Dublin (Ireland) Library provides
simplified explanations and examples [here][dublin-ex]. 
:::

If all of this seems overwhelming, that's okay. The Consortium of European
Social Science Data Archives (CESSDA) has a great introductory
[video][cessda-video] for those who have never documented data before. CESSDA
also provides detailed explanations of what information to document at both
project and data level in their [Data Management Expert Guide][cessda-guide].
This includes detailed information about documenting quantitative and
qualitative data. Just make sure to expand all the collapsed sections.


:::{seealso} 
There are many resouces on documenting your data available. Here are a selection
of them:
- [Metadata Standards Catalog][msc]
- [Fairsharing.org][fairshare]
- [README, Write Me! DataLab workshop reader][datalab-readme]
- [UC Davis Research Data Management LibGuide][lib-metadata]
- [CESSDA's Data Management Expert Guide][cessda-guide]
- [The Turing Way on Documentation and Metadata][turing-metadata]
- [MIT Metadata Info][mit-metadata]
- [Harvard Biomedical Documentation and Metadata][harvard-metadata] 
- University College Dublin on [Metadata][dublin-ex] and [Documentation][ucd-doc]
:::


[lib-metadata]: https://guides.library.ucdavis.edu/data-management/documentation
[lib-dmp]: https://guides.library.ucdavis.edu/data-management/planning
[DMPTool]: https://dmptool.org/
[msc]: https://rdamsc.bath.ac.uk/
[msc-subject]: https://rdamsc.bath.ac.uk/subject-index
[fairshare]: https://fairsharing.org/
[michener]: https://esajournals.onlinelibrary.wiley.com/doi/10.1890/1051-0761%281997%29007%5B0330%3ANMFTES%5D2.0.CO%3B2
[mit-metadata]: https://libraries.mit.edu/data-management/store/documentation/
[dublin-core]: https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#section-3
[dublin-ex]: https://libguides.ucd.ie/data/metadata
[cessda-video]: https://www.youtube.com/watch?v=cjGz-I0GgKk
[cessda-guide]: https://dmeg.cessda.eu/Data-Management-Expert-Guide/2.-Organise-Document/Documentation-and-metadata
[tgn]: https://www.getty.edu/research/tools/vocabularies/tgn/index.html
[turing-metadata]: https://book.the-turing-way.org/reproducible-research/rdm/rdm-metadata/
[harvard-metadata]: https://datamanagement.hms.harvard.edu/collect-analyze/documentation-metadata
[c-vocab]: https://rdf-vocabulary.ddialliance.org/
[ucd-doc]: https://libguides.ucd.ie/data/documentation

(create-data-dictionary)=
### Create a Data Dictionary

A **data dictionary**, part of your metadata, is a document that explains what
every field or element in your dataset means as well as any restrictions on
their values. This includes things like the data type (ex. number, date, text,
boolean), and whether that field can be missing. The more information you
include, the more helpful it will be down the line (see [Captain
Obvious][captain_o]). Data dictionaries are the most efficient way to
communicate the structure and content of your data to other collaborators,
including future you! A very basic one could look like this:

|Field Name |Field Description                         |Data Type   |Notes     |
|-----------|------------------------------------------|------------|----------|
|person_id  |autogenerated by database                 |integer     |          |
|name       |legal full name (family name, given name) |string      |          |
|occupation |A person's job or vocation                |string      |Must come from the Bureau of Labor Statistics Occupation List |
|...        |...                                       |...         |...       |



If you aren't sure where to start with creating a data dictionary, DataLab has a
[template][datalab_dd_template] you can use as a jumping off point. If you
prefer step by step instructions, Kristin Briney's [Create a Data Dictionary
exercise][create_dd] might be for you. [Open Science Framework (OSF)][osf_dd] has
resources on what details to add to your data dictionary, and the
[USGS][usgs_dd] provides many examples of data dictionaries and how they are
used in different contexts. If you are working with multiple data sets, make
sure to clarify which data dictionary to use with each data set.

If your dataset looks less like a series of rows and columns, and more like a
long list of files, consider creating a **data inventory** instead. A data
inventory should include the author or source, title, publication year and DOI
(if published), and file name for each file, and can include more file metadata
as necessary. For example, a data inventory for works of fiction in the public
domain could look something like this.

|Author              |Title               |Year |Filename                                  |
|--------------------|--------------------|-----|------------------------------------------|
|Bronte,Charlotte    |JaneEyre            |1847 |EN_1847_BronteCharlotte_JaneEyre.txt      |
|Austen,Jane         |SenseandSensibility |1811 |EN_1811_AustenJane_SenseandSensibility.txt|
|Wollstonecraft,Mary |Maria               |1798 |EN_1798_WollstonecraftMary_Maria.txt      |
|...                 |...                 |...  |...                                       |


If you also need to keep track of things like the provenance or license
associated with each file or data set, DataLab's 
[data inventory template][datalab_di_template] provides a comprehensive
starting point. 

If your data uses numbers, acronyms, or abbreviations to store information, you
should include a [**codebook**][codebook] in your metadata. Like a data
dictionary, a codebook lists all of the variables in a data set. However, a
codebook also lists the meaning of each value (or code) for each variable. For
example, it is very common to store biological sex as a binary variable where
the values are either 0 or 1. The codebook for such a data set would tell you
that 0=male and 1=female for the sex variable.

[osf_dd]: https://help.osf.io/article/217-how-to-make-a-data-dictionary
[usgs_dd]: https://www.usgs.gov/data-management/data-dictionaries
[captain_o]: https://dataedo.com/blog/captain-obivous-guide-to-column-descriptions-data-dictionary-best-practices
[datalab_dd_template]: https://docs.google.com/spreadsheets/d/12N0hKyeT0ndZnt7rVZsz7LTW--BHhbb6TOegXEKQoxE/edit?usp=sharing
[datalab_di_template]: https://docs.google.com/spreadsheets/d/1nUb-eu82Q7VplDpk0np5rYuaN52mYHLdql18pRD0i4Y/edit?usp=sharing
[create_dd]: https://caltechlibrary.github.io/RDMworkbook/documentation.html#data-dictionary
[codebook]: https://www.icpsr.umich.edu/sites/icpsr/posts/shared/what-is-a-codebook-2

:::{seealso}
See [OSF][osf_dd] and the [Research Data Management Workbook][create_dd] for how
to create a data dictionary, UC Davis DataLab for [data
dictionary][datalab_dd_template] and [data inventory][datalab_di_template]
templates, and [USGS][usgs_dd] for examples.
:::


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
Workflow automation practices (see {ref}`sec-use-a-task-runner`) take this a
step further by bundling all of the commands in a workflow into a single
command.


## Make Workflow Diagrams

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

## Make a Data Management Plan
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
	* Megabytes? Gigabytes? Terabytes?
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

## Document the Code

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
organization across files. See {ref}`write-readmes` for more about how to write
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


## Make Backups

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
## Use Version Control

**Version control** is the act of tracking changes to your files. By capturing and timestamping all changes to the project files, version control allows for a complete audit and reconstruction of the project and is thus a cornerstone of reproducibility practices. Projects that use version control allow you to follow the exact course of the research from original data to analysis, interpretation, and final product as well as identify exactly when and why a specific file or result changed. There are a few common **version control systems** that you can use to track changes to your research files, including your documentation, code, and data. 

### Manual Version Control

You may already be saving copies of files with different names
as a kind of ad-hoc version control system. This could look like using a standardized file name convention that includes a keyword denoting the topic of the file combined with a date or project milestone indicating when the file was last modified. For example, the names of the copies could look like `essay_2025_12_01.doc` and `essay_2025_12_31.doc` if using calendar dates to denote changes, or `essay_edited.doc`, `essay_final.doc`, `essay_final_for_real.doc`, and so on if using project milestones. However, making multiple copies of a file and applying standardized naming conventions to track changes is error prone and can make it challenging to identify what exactly is different across the copies. It also requires more space as you are saving multiple full copies every file you modify. Thus, using cloud-based tools with or software that automate version control for your files is preferred whenever possible.

### Cloud-Based Version Control

Cloud-based office suites such as Microsoft 365 OneDrive, Google Office and Box include built-in version history features that allow you to revert to older versions of a file. This version control system can work effectively, assuming you have access to the platform and are able to store all your work there. It also requires you, and anyone else working on the file, to have reliable internet access. A disadvantage of these services is that they typically save
documents in proprietary formats that may not be accessible to some people, and
they do not necessarily preserve version information when you download a
document from the cloud to work with it locally on your machine. These cloud services also facilitate collaboration, assuming all members of the team have access to the tools. For an open-source, desktop-based alternative,
consider using [LibreOffice][], which also has version control built-in.

[LibreOffice]: https://www.libreoffice.org/

### Version Control Software

The most consistent and precise approach is to use software specifically designed for version control. In computing contexts, when people say "version control," it's often
implied that they mean a version control system that uses software designed for that purpose. In addition to helping you keep track of different versions of files, most modern version control software
can also help you share and collaborate on files with others. The most common version control software and cloud sharing platform are Git and GitHub.

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
flexible about where you store your code; there can be copies of the code on
your laptop, on a private server, on a hosting service like [GitHub][], and on
your collaborators' laptops, and Git will help you keep all of them in
sync---if that's what you want. DataLab uses Git for all of our projects, and
recommends that you do too.

[so-vcs-survey]: https://stackoverflow.blog/2023/01/09/beyond-git-the-other-version-control-systems-developers-use/
[Git]: https://git-scm.com/

:::{note}
Git and other version control software can manage versions of all file types. While this software also facilitates direct comparisons across different versions of your documentation and code files so you can quickly and reliably identify exactly what changed, it generally does not track specific changes within spreadsheet, image, and video files.
:::

:::{seealso}
See the UC Davis Library's [Research Data Management Guide][rdm-version-control] for an overview of  version control systems, and DataLab's [Introduction to Version Control workshop reader][intro-vcs] for
a technical introduction to version control with Git.

[rdm-version-control]: https://guides.library.ucdavis.edu/data-management/version-control
[intro-vcs]: https://ucdavisdatalab.github.io/workshop_reproducible_research/chapters/version-control/01_version-control-systems.html
:::

:::{note}
[Markdown][] is a lightweight markup language that provides basic formatting options, is supported by a wide variety
of editors and platforms, and can be used to produce publication-quality
documents with open-source tools like [Pandoc][]. Because Markdown is a
plain-text format, anyone with a text editor can read a Markdown document, and
you can manage versions with the same version control systems available for
code. For a more richer markup language that produces publication-quality
documents out-of-the-box, but has many of the same advantages as Markdown,
consider [LaTeX][].

[Pandoc]: https://pandoc.org/
[LaTeX]: https://www.latex-project.org/
:::


## Use Naming Conventions

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


### File and Directory Names

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


### Names in Code

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
## Establish a Directory Structure

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
## Organize the Code

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

### Write Functions

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

### Make It Modular

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

(sec-open-access)=
## Open Access 

Not having access to a piece of research or its underlying data and materials can be the main roadblock to reproducibility. Open access not only allows anyone to access and read the papers, but it also permits reproducibility, replicability, and the opportunity to build on or reuse all or part of your work in a future project to advance science and knowledge. Many grant providers and institutions may also require your work to be published open access.

:::{important}
**Open Licenses**

Applying an open license to your materials is key to making them openly available. Open licenses allow anyone to view, share, and reuse materials. See more in the {ref}`open-licenses` section below.
:::

#### Publish Open Data

Study data are often stored privately, but sharing your data is an integral part of reproducibility. Research simply cannot be reproduced without access to the data underlying the results, figures, tables, and conclusions.

**Open data** refers to data shared publicly and licensed under an open license so that it can be freely accessed, reused, and shared by anyone. Many grant providers, institutions, and publishers now require underlying data to be shared openly.

You can deposit your data in open data repositories to make them freely available. Whether you want a generalist or specialist repository, look for a reliable repository that meets the following requirements:
* Uses open licenses
* Assigns Persistent Identifiers (PID), such as digital object identifiers (DOI), to the dataset(s)
* Plans for long-term maintenance, continued access, and preservation of the datasets.
* Financially stable
* No burdensome access requirements for readers, such as registration fees, membership requirements, etc.
* Contact information, documentation, and staff or representatives are available to address issues and offer user support.

Learn more about trustworthy data repository requirements from [CoreTrustSeal][cts-repositories-requirements].

[cts-repositories-requirements]: https://www.coretrustseal.org/why-certification/requirements/

:::{note}
Some data may be personal or sensitive. Do not share your data openly if they are protected, nationally or commercially sensitive, contain identifying information, or you have not obtained proper consent. You can learn more about considerations for these types of data…(maybe Turing Way?)
:::

You should also ensure your data follow FAIR principles using the following practices:

**Findable:**
* Publish or deposit in an open access repository.
* Assign a persistent identifier to your dataset, such as a Digital Object Identifier (DOI). (This can usually be done by depositing in a repository.)
* Properly cite the data in any related published materials.

**Accessible:**
* Publish or deposit in an open access repository.
* Include proper metadata describing access, authentication, and authorization.

**Interoperable:**
* Publish data and metadata in standard, non-proprietary formats.
* {ref}`use-file-formats-effectively`

**Reusable:**
* Provide metadata and adequate documentation for reuse.
* **Other links to other sections???**
* Publish under an open license.
* Properly cite your source data.

:::{seealso}
See UC Davis Library's [Research Data Management Guide][RDM-guide-data-sharing] to learn more about how to share your data openly.

Review the {ref}`open-licenses` section below to learn more about publishing your data under an open license.
:::

[RDM-guide-data-sharing]: https://guides.library.ucdavis.edu/data-management/data-sharing

### Publish Open Access Articles

Publishing an open access article reduces barriers for readers and researchers by making it freely accessible.

Publishing your work in an open access journal or as an open access monograph is known as Gold Open Access. It generally goes through the same review process that any submission would, but is then published openly, usually through an open license, so that anyone can read it without having to pay a subscription or access fee.

Learn more about open access publishing, including finding reputable journals and avoiding predatory publishers, and open access funding support at UC Davis on our [Open Access Publishing Library Guide][open-access-guide].

#### Pre-Prints and Post-Prints

Publishing research Open Access can be expensive and therefore may not always be feasible. University of California authors may have [Open Access fee assistance][open-access-guide] available to them. However, authors with no fee assistance have other options for making their work openly available and, therefore, reproducible.

Authors can make their work openly available by self-archiving it somewhere accessible, such as an institutional repository or preprint server. This is also known as Green Open Access. Note that the archived version may be different than a peer-reviewed and formally published version.

**Preprints** are publicly available papers that have not (yet) been peer reviewed. Usually, authors will post a paper to a preprint server under an [open license](#open-licenses) after the paper has been written and before submitting to a journal for peer review and publication. Some preprints are never submitted or accepted to a journal for formal publication.

:::{important}
Articles are often revised, sometimes significantly, during the peer-review process. A published version of an article in a journal may differ greatly from a preprint version.
:::

**Post-prints,** or author-accepted manuscripts, have been peer-reviewed and accepted for publication, then made publicly available somewhere accessible, such as an institutional repository. These versions are usually the same as or very similar to the published versions.

:::{important}
Different publishers have different policies about sharing author-accepted manuscripts, including potential embargo periods. Refer to your publisher’s policies or [Jisc’s Open Policy Finder][open-policy-finder] to understand your sharing permissions.
:::


:::{seealso}
To learn more about Open Access options, the [Open Access Network][open-access-network] is a great educational resource that discusses Diamond, Gold, and Green Open Access.
:::

[open-policy-finder]: https://openpolicyfinder.jisc.ac.uk/
[open-licenses]: {ref}`open-licenses`
[open-access-guide]: https://guides.library.ucdavis.edu/open-access-publishing
[open-access-network]: https://open-access.network/en/information/open-access-primers/green-and-gold

(open-licenses)=
### Open Licenses

A **license** grants others permission to possess, copy, and/or use a piece of work in a variety of ways. An **open license** makes a work freely available for others to read, copy, distribute, and use without obtaining permission from the author or creator. Open licenses also provide free, immediate, and perpetual access to the content. 

For code, an open-source license ensures that software can continue to be maintained and extended even if the original developers cease development. They also promote transparency and collaboration, since anyone with the software can inspect and modify the code.

When an open license is applied to a work, the author or creator retains the rights to/ownership of the original work, and most open licenses require that proper credit be given to the creator.

[Creative Commons][creative-commons] licenses are the most common open licenses for articles and datasets. MIT licenses are common for open code, but many more are available, as discussed by the [Open Source Initiative][open-source-licenses].

Many open licenses allow for any type of use and reuse, including modifications, distribution, etc., but authors have options for open licenses with certain restrictions such as no commercial use or no derivatives, or a requirement that any copies or adaptations be licensed under a similar open license.

[creative-commons]: https://creativecommons.org/
[open-source-licenses]: https://opensource.org/licenses

:::{seealso}
For licensing data, writing, art, or other materials, see Creative Commons' [Choose a License page][cc-cal] for help deciding on a Creative Commons license.

For licensing software, see [choosealicense.com][gh-cal] to help you choose an open license (maintained by GitHub) or the Open Source Initiative's [FAQ answer about which license to choose][osi-cal].
:::

[gh-cal]: https://choosealicense.com/
[osi-cal]: https://opensource.org/faq/#which-license
[cc-cal]: https://creativecommons.org/choose/
