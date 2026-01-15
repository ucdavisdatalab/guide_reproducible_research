Secondary Practices
===================

This chapter covers secondary practices for reproducibility. These are
practices which don't apply to every project, but are beneficial or even
essential when they do apply. For instance, projects that will never be
distributed do not necessarily need a license, so choosing a license is listed
here. DataLab adopts these practices for all projects for which they are
relevant, and we recommend you do too.


Documentation
-------------

(document-every-experiment)=
### Document Every Experiment

:::{note}
An "experiment" doesn't necessarily have to be an experiment done in a lab.
Doing an experiment could mean running a simulation, testing a model, or
something else.
:::

Keep a record of every experiment that you do. Document parameters, the
results, and anything else you think is relevant for:

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
Spreadsheets are often a good format for this kind of documentation, since
they're convenient for data entry.
:::


(choose-a-license)=
### Choose a License

A **license** is a legal document that grants others permission to do, use, or
possess something. If you plan to make your project widely or publicly
available, it's a good idea to select a license so that you can retain some
control over how it's used and protect yourself against certain kinds of legal
claims.

Different kinds of licenses are appropriate for different kinds of content.
There are licenses designed specifically for software and code, as well as
licenses for other media.

An **open-source** license is one that mandates access to or distribution of
original sources for any derivative products. For software, this means that the
original source code must be accessible. Open-source licenses ensure that
software can continue to be maintained and extended even if the original
developers cease development. They also benefit transparency and collaboration,
since anyone with the software can inspect and modify the code.

DataLab uses open-source licenses for a majority of our projects, whether they
consist of software or other materials (like this reader).

:::{seealso}
For licensing software, see [choosealicense.com][gh-cal] (maintained by GitHub)
or the Open Source Initiative's [FAQ answer about which license to
choose][osi-cal].

For licensing data, writing, art, or other materials, see Creative Commons'
[Choose a License page][cc-cal].
:::

[gh-cal]: https://choosealicense.com/
[osi-cal]: https://opensource.org/faq/#which-license
[cc-cal]: https://creativecommons.org/choose/


Artifact Preservation
---------------------

### Use Configuration Files

A **configuration file** is a file that stores accessory parameters for a
computation. Configuration files are distinct from data sets in that the data
they contain is usually under your control and not of primary interest. For
example, a configuration file for code that trains a statistical model might
specify where to find training data, where to find test data, which features to
include in the model, and where to save predictions. All of these could be
embedded in the code, but using a configuration file makes the code more
flexible.

Configuration files also have another benefit: they serve as a record of your
parameter settings. When parameter settings are embedded in code, then you have
to edit the code each time you want to run it with different settings. Unless
you're meticulous about version control, it may be difficult to determine which
settings you used for past computations. Configuration files eliminate this
problem: when you want to use a new settings, create a new configuration file
(possibly by copying one you already have). Then you can easily find the
settings for any computation in its respective configuration file.

<!-- also hard to share with collaborators and may introduce bugs -->

:::{tip}
If you also {ref}`document-every-experiment`, include the name of the
configuration file(s) for each experiment in your documentation.
:::

Plain-text formats are a good choice for configuration files because they can
be edited by anyone with a text editor. At DataLab, we particularly like to use
[TOML][] and [YAML][] formats for configuration files because they're
widely-used, human-readable, and there are well-supported functions for reading
them in R, Python, and Julia.

[TOML]: https://toml.io/
[YAML]: https://yaml.org/


### Release the Data

Publish or share your research data, so that other researchers can use it to
reproduce your work and possibly even do new work. In 2016, [Wilkinson et
al][wilkinson] suggested researchers should make their data **FAIR**:

* Findable: uniquely identifiable and citable, such as with a DOI
* Accessible: freely and publicly available
* Interoperable: saved in open, non-proprietary formats
* Reusable: well-documented and with a clear license

[wilkinson]: https://doi.org/10.1038/sdata.2016.18

The FAIR standards are now widely recommended as best practices.

You can satisfy the "F" and "A" standards by publishing your data to an
[open-access repository][oar]. For example, UC Davis is a partner of the
[Dryad][] open-access repository, and all UC Davis researchers can use Dryad
for free to publish their data.

[oar]: https://en.wikipedia.org/wiki/Open-access_repository
[Dryad]: https://datadryad.org/stash

To satisfy the "I" standard, {ref}`use-file-formats-effectively`. To satisfy
the "R" standard, a good start is to {ref}`keep-running-notes` and
{ref}`write-readmes`.

<!-- FIXME: this used to refer to choose-a-license too -->

:::{seealso}
See UC Davis Library's [Publish, Share, and Preserve Your Data
guide][library-publish-data] to learn more about how to release your data.
:::

[library-publish-data]: https://library.ucdavis.edu/data-analysis-and-management/publish-share-and-preserve-your-data/



Project Organization
--------------------

### Save Clean Data

Treat data cleaning and data analysis as distinct and equally important steps
in the research process. Write code to clean the data, and document *why* each
cleaning step was taken, so that cleaning is reproducible. Save a copy of the
clean data to use in analyses. This way:

* Cleaning is consistent across all analyses.
* You only need to run the cleaning step once. For some data sets, cleaning is
  a time-consuming and expensive computation.
* Cleaning and analysis concerns are kept separate, which makes it easier to
  write simple code with clear goals.
* You can use different languages or software for the cleaning step and the
  analyses.

What it means for data to be "clean" will depend on your project's specific
data sources and analysis goals. Nevertheless, here are some things you should
almost always do:

* Check that the structure of the data is appropriate. For instance, many tools
  for analyzing tabular data require **tidy data**, where each row is an
  observation and each column is a feature.
* Check that the types of the data are appropriate. In other words, make sure
  the language or software you plan to use recognizes data for what they are.
  For instance, dates often need to be explicitly converted to a date type.
* Investigate missing data. It's crucial to have a thorough understanding of
  what's missing before moving to analysis. If you decide to remove or fill in
  missing data, do so cautiously; it's not always necessary and can bias
  analyses.
* Investigate extreme data and erroneous data. As with missing data, it's
  important to understand the outliers in your data.

:::{seealso}
See DataLab's [Intermediate R: Cleaning & Reshaping Data workshop
reader][datalab-r-clean] to learn how to clean data in R.
:::

[datalab-r-clean]: https://ucdavisdatalab.github.io/workshop_intermediate_r/string-date-processing.html

(use-file-formats-effectively)=
### Use File Formats Effectively

For any dataset, there are many different ways to store that data. For tabular
data (rows and columns) alone, there are at least seven different file formats.
So how do you choose?

It is best to store data sets in file formats that:

* Are accessible to you, your collaborators, and other researchers across a
  variety of software

* Preserve the data set's structure and types (including categories, dates, and
  times)

* Can be read and written efficiently

Plain-text formats---such as comma-separated values (CSV)---satisfy the
accessibility requirement, and also have the advantage of being human-readable,
but usually fail on preservation and efficiency. Binary formats usually fare
better for preserving data set structure and types, as well as for fast read
and write times.

For tabular data sets, both [Apache Arrow][arrow] (also known as [Feather][])
and [Apache Parquet][parquet] satisfy all three requirements. Arrow and Parquet
are binary formats, so they aren't human-readable, but they are open standards,
so support for them can be implemented in any software. R, Python, and Julia
all already support both through various packages. The Arrow standard is
simpler but changes more frequently than the Parquet standard. As a result,
Arrow is faster to read and write and a good choice for short-term storage.
Parquet is a better choice for long-term storage because the standard is more
stable.



[arrow]: https://arrow.apache.org/
[feather]: https://arrow.apache.org/docs/python/feather.html
[parquet]: https://parquet.apache.org/

(prefer-open-standard-file-formats)=
#### Prefer Open Standard File Formats

For any file format, there is a defined standard for how any file of that format
should be structured on a computer. Open standard file formats have these
standards openly published and updated when they changed. They can be 
implementented by anyone in any application or software without paying licensing
fees. Additionally, they are not encumbered by copyrights, patents
or other legal restrictions to their use.

Standards for proprietary file formats are not publicly available and can be
changed unilaterally by the file format owner at any time. They may require
expensive software to read or write files of those formats, and if the company
stops maintaining the software, data in a proprietary file format may become
completely inaccessible.

Using open file formats means your data will be accessible to the largest
number of people, for the longest period of time. The following are a list of 
open standard file formats by data type. It is not exhaustive but is a place to
start. 


| Data Structure            | File Formats                                |
|---------------------------|---------------------------------------------|
|**Tabular Data**           | Plain-text (.csv, .tsv, .txt), Apache Arrow (.feather), Apache Parquet (.parquet), OpenOffice Calc (.ods)|
|**Nested/Tree Data**       | JSON, XML                                   |
|**Geospatial Data**        | GeoJSON (vector), GeoTIFF (raster), NetCDF (raster), Hierarchical Data Format (HDF, raster), OGC GeoPackge (both)|
|**Network or Graph**       | GraphML, Graph Exchange XML Format (GEXF), Graph Modeling Language (GML), Turtle/RDF|
|**Still Images**           | PNG (raster), TIFF (raster), SVG (vector)   |
|**Audio**                  | WAVE, AIFF, MP3, MXF                        |
|**Moving Images**          | MOV, MP4, AVI                               |
|**Databases**              | Postgres, SQLite, DuckDB, MongoDB, Neo4j, Apache CouchDB |


:::{admonition} A Word on Industry Standards  
:class: note
There are some fields that are so heavily dominated
by a particular proprietary software that the file format associated with that
software becomes the de facto file format for the entire field. In this case,
using the proprietary format will make data more accessible than using a niche
open standard format. However, you should back up your data in a non-proprietary
format in case you lose access to the proprietary software.
:::

:::{seealso}
For more information about file formats for long term data storage formats, see
the Library of Congress's [Recommended Formats Statement][rsf] and their webpage
on the [Sustainability of Digital Formats][sdf].
:::

[rsf]: https://www.loc.gov/preservation/resources/rfs/TOC.html
[sdf]: https://www.loc.gov/preservation/digital/formats/index.shtml


(databases)=
#### Databases

A **database** is an organized collection of data stored with specialized software that helps you
do things like query and update the data. Databases can:


* create a definitive version of your data that multiple people can access
without creating conflicts.

* provide quality control measures to reduce input errors and make sure typos don't get introduced into
your data.

* query millions of observations in seconds (which you can't do in Excel or Google Sheets!).

* store data more efficiently than regular files.

* control who has access to your data, and what they can do with it, on a very
granular level.

Databases are a specialized tool. They are optimized for querying and
transforming data. As such, they are generally faster at those tasks than R or
Python. However, they don't do everything. You can't create a data visualization
using a database, or run a statistical analysis. A database is a perfect data
source for those tasks to ensure that your results are reproducible across
collaborators and over time. Databases also make an excellent platform for
sharing or publishing your data. Their permissions functionality means you can
easily give the public read only access to your finalized data products, while
keeping the raw or unprocessed data only accessible to your collaborators.

Historically, databases were restricted to primarily tabular data (rows and
columns), in what are called **relational databases**. In recent years though, new
types of databases have come on the scene that can efficiently store all sorts
of different data, including nested or tree based data, graph data, and
unstructured text. The type of data you have will inform what kind of
database would be best for you, which you can find out more about in the
[Overview of Databases and Data Storage reader][datalab-db]

Many, if not most, database systems have graphical user interface software to
make it easier to interace with the database. But, to get the most out of a
database, it is helpful to the query langauge associated with your database of
choice. For relational databases this is SQL, which stands for Structured Query Language. To get get started with SQL, see
[Introduction to SQL for Querying Databases workshop reader][datalab-sql].
Non-relational (SQL-based) databases use a variety of langauges to write
queries. MongoDB, a document based database, uses MQL, which you can learn in
W3School's [MongoDB Tutorial][mongo]. Like other computer languages, query
languages like SQL and MQL make your data cleaning and transformation processes
reproducible. However, they are much easier to learn because the set of tasks
they are designed to do is much smaller. 


:::{seealso}
DataLab's [An Overview of Databases and Data Storage workshop
reader][datalab-db] provides an introduction to databases. DataLab's
[Introduction to SQL for Querying Databases workshop reader][datalab-sql]
teaches you how to query data in relational databases. W3School's [MongoDB
tutorial][mongo] shows you how to query data in a document or text based
database using MQL.
:::

[datalab-db]: https://ucdavisdatalab.github.io/workshop_intro_to_databases/
[datalab-sql]: https://ucdavisdatalab.github.io/workshop_intro_to_sql/
[mongo]: https://www.w3schools.com/mongodb/index.php


Workflow Automation
-------------------

### Orchestrate with Shell Scripts

Even if you {ref}`organize-the-code` carefully, it's likely you'll end up with
workflows that consist of running several commands in a specific order and with
specific settings. It's also likely you'll need to re-run these workflows many
times as you incrementally improve, extend, and adapt the code. To make this
more convenient and ensure that you don't accidentally skip commands or use the
incorrect settings, it's a good idea to automate your most frequently used
workflows.

:::{note}
A **Unix shell** is a standardized way of interacting with a computer via text
commands---that is, via a command line. Unix shells are widely-used for
research computing. 

See the DataLab's [Introduction to the Command Line workshop reader][intro-cli]
to get started with the command line and Unix shells.

[intro-cli]: https://ucdavisdatalab.github.io/workshop_reproducible_research/chapters/command-line/01_interacting-with-computers.html
:::

If you run your workflows in a Unix shell, one way you can automate them is by
writing **shell scripts**. A shell script is a plain-text file with a sequence
of Unix shell commands (akin to scripts for other languages, such as R or
Python). You can create separate shell script for each workflow that you run
frequently. The technical effort is low, since this just amounts to writing
down the commands that you already run in a text file. Besides making it easier
to run specific workflows, you can also share shell scripts with your
collaborators or other researchers. This helps to ensure that they also run the
workflow correctly.

:::{seealso}
See DataLab's and DIB Lab's [Automating Your Analyses and Executing
Long-running Analyses on Remote Computers workshop
reader][datalab-shell-scripts] for the technical details of writing shell
scripts.
:::

[datalab-shell]: https://ucdavisdatalab.github.io/workshop_introduction_to_the_command_line/
[datalab-shell-scripts]: https://ngs-docs.github.io/2021-august-remote-computing/automating-your-analyses-and-executing-long-running-analyses-on-remote-computers.html


## Prefer Open-Source Software

> You're excited to start working on a project about how a particular virus
> spreads among domesticated poultry populations. The project seems promising,
> because your collaborator has been collecting data for over 10 years. When
> they send you the data, you notice that the first 3 years of data are
> anomalous compared to the rest. You ask your collaborator about it, and they
> mention that they used to calibrate the data with software from Big Money
> Corporation. After 3 years, they switched to an open-source calibration
> software, because Big Money Corp. went out of business. You'd like to confirm
> that the calibration software from Big Money Corp. used the same algorithm as
> the open-source calibration software, but the documentation is vague, the
> source code is not available, and no one online seems to know. You're glad
> your collaborator still has copies of the raw, uncalibrated data, but it
> looks like you'll have to spend a few days running all of it through the
> open-source calibration software.

Software is **open-source** if its source code is freely available. Most
commercial software is closed-source: only the developers have access to the
source code. Using open-source software makes your research more reproducible
in at least three ways:

* Transparency: When you use closed-source software, you have limited insight
  into how it actually works. The algorithms the software uses might not be the
  ones the distributor claims, and there might be bugs in their
  implementations. When you use open-source software, if you have these
  concerns, you can inspect the source code yourself to determine how the
  software works.

* Longevity: The lifespan of closed-source software is entirely up to its
  developers and distributor. In contrast, for open-source software, even if
  the original developers retire from or abandon development, someone else can
  step in and continue to develop the software. Many open-source software have
  continued to receive updates for 20-30 years or more, and run well on modern
  computers---an achievement few closed-source software can claim.

* Extensibility: Whether a new feature is added to closed-source software is up
  to the whims of its developers. With open-source software, you can add the
  feature yourself (or hire someone else to do it). 

We recommend using open-source software whenever possible because of these
benefits. That said, make sure to take into account the norms and expectations
of your collaborators and your discipline, and whether the available
open-source software meets your needs. In some disciplines, closed-source
software is widely-used, and using anything else can make it difficult to
collaborate or to convince peers of the soundness of your work. For specialized
tasks, closed-source software is sometimes the only software available. It's
wonderful if you want to be an open-source trailblazer (or even developer) in
your discipline, but make sure it's an informed decision. 

:::{seealso}
Many universities, including UC Davis, have an Open Source Program Office
(OSPO) to train and support contributors and maintainers of open-source
software. You can learn more about UC OSPOs at the [UC OSPO Network][ospo]
website.

[ospo]: https://ucospo.net/
:::


(use-a-programming-language)=
### Compute with Code

:::{note}
This practice is recommended for projects that involve computations. If your
project doesn't, or if all computations are handled by specialized software,
then you might not need a programming language.

Nevertheless, we've included writing code as a primary practice to emphasize
that it's uniquely important for reproducibility if your project does involve
computations.
:::

Code is an explicit, unambiguous record of every step in a computation. This is
a major benefit for reproducible research. You can share your code with someone
else, and if they run it with all of the same inputs, they'll get the same
outputs. The same is difficult or impossible to achieve using software that has
a graphical user interface.

Another benefit of programming is that code is reusable and often scalable. If
you write code to solve a general problem, you can then apply it to any number
of specific instances of that problem. The only constraints are time and the
computing resources available to you. Most popular programming languages have
supportive, active communities that create and distribute thousands of
user-contributed packages, so often it's not even necessary to solve a problem
yourself---you can reuse someone else's code.

::::{grid}
:::{grid-item}
```{image} /images/logo_r.png
:alt:
:width: 50%
:align: center
```
:::

:::{grid-item}
```{image} /images/logo_python_device.svg
:alt:
:width: 40%
:align: center
```
:::

:::{grid-item}
```{image} /images/logo_julia.svg
:alt:
:width: 50%
:align: center
```
:::
::::

:::{margin}
```{note}
A **high-level** programming language is one which uses abstractions to hide
most of the details of the hardware.
```
:::

Choosing a programming language doesn't just mean choosing a particular syntax,
it also means choosing a community and ecosystem. Different languages have
different strengths, weaknesses, community cultures, and packages. We recommend
choosing an open-source, high-level language designed for research computing
and data analysis, such as:

* [R][]: a "software environment for statistical computing and graphics," R is
  especially well-suited to cleaning and analyzing tabular data, training
  statistical models, and creating data visualizations. R has support for
  missing values built-in, a friendly and active community, and tens of
  thousands of user-contributed packages, mostly related to statistics and data
  science.

* [Python][]: a general-purpose programming language that "lets you work
  quickly and integrate systems more effectively." The Python community
  supports research computing through its user-contributed NumPy, SciPy, and
  Pandas packages, as well as others. Python's syntax encourages well-organized
  code, and its community is enormous and spans many different disciplines.
  It's also one of the primary languages for deep learning. Python's facilities
  for data analysis are not as mature as R's, with equivalent features and
  stability but some rough edges.

* [Julia][]: a relatively new programming language "appropriate for scientific
  and numerical computing, with performance comparable to [languages like C]."
  Julia is designed from the ground up for research computing and uses modern
  optimizations to run substantially faster than R or Python for many tasks.
  Julia's community is small but growing. Julia's facilities for data analysis
  are not as mature as R's or Python's, with many still in early development.
  Expect to occasionally have to develop things yourself when you wouldn't in
  more mature languages.

[R]: https://www.r-project.org/
[Python]: https://www.python.org/
[Julia]: https://julialang.org/

When choosing a language, always make sure to consider the specific needs of
your project. Projects with specific requirements for performance or other
features (for example, developing web applications) may benefit from using
other languages or a mix of languages.

:::{seealso}
If you want to learn R, see DataLab's [R Basics workshop reader][r-basics] and
consider joining the [Davis R Users Group][drug].

If you want to learn Python, see DataLab's [Python Basics workshop
reader][py-basics] and consider joining the [Davis Python Users Group][dpug].

If you want to learn Julia, see the [official Julia documentation][julia-docs]
and consider joining the [UC Julia Users Group][ucjug].
:::

[r-basics]: https://ucdavisdatalab.github.io/workshop_r_basics/
[drug]: https://d-rug.github.io/
[py-basics]: https://ucdavisdatalab.github.io/workshop_python_basics/
[dpug]: https://datalab.ucdavis.edu/davis-python-users-group/
[julia-docs]: https://docs.julialang.org/
[ucjug]: https://datalab.ucdavis.edu/julia-users-group/
