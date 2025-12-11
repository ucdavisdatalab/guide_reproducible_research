Case-by-case Practices
======================

:::{attention}
This chapter is still a work-in-progress. Check back when you've got some
experience with research computing and are ready to learn more.
:::

This chapter covers case-by-case practices for reproducibility. Many of these
practices require substantial effort to adopt or require specific technical
knowledge. They can be important and even essential for certain kinds of
projects, but we feel they aren't broadly applicable in the ways that primary
and secondary practices are. DataLab occasionally adopts these practices. Read
this chapter when you feel like you've mastered the practices in the previous
chapters and want to learn even more.



Documentation
-------------

### Use Issue Tracking


### Make a Data Management Plan

:::{seealso}
See DataLab's [Data Management Plan toolkit][datalab-dmp] for instructions
about how to make a data management plan.
:::

[datalab-dmp]: https://datalab.ucdavis.edu/data-management-plans/


Artifact Preservation
---------------------

### Log Output

:::{seealso}
If you're using R, see DataLab's [Intermediate R: Outputs, Errors, and Bugs
workshop reader][datalab-r-output] for a brief overview of a how to manage log
files in R.

If you're using Python, see DataLab's [Intermediate Python: Squashing Bugs with
Python's Debugging Tools workshop reader][datalab-py-output] for a brief
overview of how to manage log files in Python.
:::

[datalab-r-output]: https://ucdavisdatalab.github.io/workshop_intermediate_r/output-errors-and-bugs.html#logging-output
[datalab-py-output]: https://ucdavisdatalab.github.io/workshop_intermediate_python/chapters/04_debugging.html#logging


### Use Version Control for Data




Workflow Automation
-------------------

```{figure} /images/xkcd_is_it_worth_the_time.png
---
name: xkcd-worth
alt:
---
"Is It Worth the Time?" from ["xkcd"][xkcd] by Randall Munroe
([license][xkcd-license]).
```

[xkcd]: https://xkcd.com/
[xkcd-license]: https://xkcd.com/license.html



### Use a Task Runner

> You're working on a project where you receive a new dataset every few weeks.
> Before you analyzing a dataset, you must process it with the `moo_calibrate`
> command line software. You don't use `moo_calibrate` outside of this project,
> so every time you have to run it, you struggle to remember the parameters.
> Last time you ran `moo_calibrate`, you wrote down the parameters, but it
> would be nice if you could automate the workflow so that you don't have to
> type as much and you can't accidentally run the command twice.

A **task runner** is a piece of software to organize and run tasks that use
other (command line) software. With a task runner, you can create named tasks
and specify the commands to run to complete each task. Later, you can run a
task by simply referring to it by name. Using a task runner makes your results
easier to reproduce, because by doing so, you encode the exact commands (in
order) to carry out tasks related to your project. Others can run a task with
no risk of accidentally skipping a command, passing the wrong arguments to a
command, or running a command out of order.

Some task runners, called **build systems**, can also keep track of dependence
between tasks. To illustrate the idea, suppose you have a task `download` that
downloads data and another task `analyze` that runs your analysis on the data.
You can't analyze data you don't have, so the `analyze` task depends on the
`download` task. If you use a build system to run the `analyze` task, it will
first make sure that the `download` task is complete (by running it, if
necessary). Using a build system makes results from projects with
interdependent tasks easier to reproduce.

Task runners usually have other features that are also helpful, such as:

* The ability to run tasks only when necessary (saving time)
* The ability to run tasks in parallel
* Language-specific features (many, but not all, build systems are designed to
  work best with a specific programming language)


DataLab recommends [Pixi][] as a task runner for most projects, since it's
relatively easy-to-use and also has other features related to reproducibility
(see {numref}`FIXME`). For projects with many interdependent tasks, DataLab
recommends [Snakemake][] as a build system. Many other task runners and build
systems also exist.

[Pixi]: https://pixi.sh/
[Snakemake]: https://snakemake.github.io/

:::{seealso}
See DataLab's [Installing Software with Pixi workshop reader][datalab-pixi] for
an introduction to Pixi.

[datalab-pixi]: https://ucdavisdatalab.github.io/workshop_research_computing/chapters/installing-software/

See DataLab's and DIB Lab's [Automating Your Analyses with the Snakemake
Workflow System workshop reader][datalab-snakemake] for an introduction to
Snakemake.

[datalab-snakemake]: https://ngs-docs.github.io/2021-august-remote-computing/automating-your-analyses-with-the-snakemake-workflow-system.html
:::



### Use Continuous Integration

#### Lint the Code

#### GitHub Actions


## Document the Computing Environment

> A few years ago, you developed an R script to read an obscure file format,
> MOO, for one of your research projects. The script was a huge help at the
> time, but you moved on and haven't used it in a while. You just started an
> exciting new project, and your collaborator sent you some data in a MOO file.
> You find your script and try running it, but alas, it crashes with an error
> message. In the years since you wrote the script, you updated your R packages
> and even uninstalled a few. You're confident the script would work if only
> you could go back to the packages and versions you had when you wrote it.

What your computer can do depends on its hardware and software. For instance, a
computer with Windows 11 installed will not necessarily be able to run software
developed for the much older Windows 95. Nor will it be able to run most
software developed (exclusively) for macOS. The computer's central processing
unit (CPU), memory, and other hardware components also limit the kinds of
software it can run. Together, your computer's hardware and software make up a
**computing environment** with specific capabilities and limitations.

When you use computers in the course of your research, it's important to
document the computing environment(s), so that people who want to reproduce
your work will know what hardware and software they need. Without this
documentation, an attempt to reproduce your work might yield errors or even
incorrect results, and thus raise questions about whether your process and
findings are valid. Good documentation on computing environments also makes it
easier to:

* Bring new collaborators into a project
* Switch between or replace computers
* Revisit old projects, whether to reexamine results or to repurpose methods
* Reach a wide audience (especially if you want others to use your software)

Modern operating systems are designed to ensure that software runs correctly
across a wide variety of hardware, so they provide abstraction layers that hide
hardware differences. As a result, for making research reproducible, software
is usually the primary concern (with the exception of projects that rely on
rare or specialized hardware). So at a minimum, for each computer you use in
your research, you should document the name and version of:

* The computer operating system
* All other software you use to arrive at your results, including application
  software (such as Microsoft Excel), programming languages, and packages for
  programming languages

If you decide to document the hardware, also include the manufacturer and model
of:

* Core components:
    * Central processing unit
    * Graphical processing unit (if not integrated in the CPU)
    * Memory
* All other hardware critical or relevant to your results

There are many strategies and tools you can use to make documenting and
reproducing computing environments more convenient and reliable. In the
following sections, we describe three: environment managers, containerization,
and cloud computing.

<!--
Computer hardware is expensive, so changing it isn't easy: the hardware you
have is the hardware you use. The good news is that modern operating systems
(like Windows and macOS) and programming languages abstract away many of the
idiosyncrasies of hardware. As a result, a computer's capabilities and limits
due to hardware depend more on performance characteristics like CPU speed,
memory, and storage space than on make and model. That said, for the sake of
transparency, it's good to make a habit of recording the exact specifications
of any hardware you use for a research project.

Software is much more mutable than hardware. Major operating systems receive
updates weekly, and some software applications and libraries receive updates
monthly. Most software builds on other software, so while updates typically fix
bugs and add new features, they can also introduce incompatibilities.

In high-level programming languages like R and Python, details of the hardware
are mostly hidden away. That is, hardware has little to no impact on how you
write code, with only a few exceptions. Hardware may affect how quickly your
code runs, but usually not the final result. As a consequence, for many
research computing projects, the hardware environment is of less concern than
the software environment.

One of the major advantages of the open-source and open-science ecosystem is
the trove of packages and other software developed and published by members of
the community. As these are updated, projects that rely on older versions may
cease to work correctly unless they are also updated. So for most projects,
keeping track of the software environment means keeping track of the specific
versions of packages and other software with which the project was carried out.

A **virtual environment** is a self-contained collection of software with
specific versions. A key characteristic of virtual environments is that they
can coexist with other virtual environments.

that can coexist alongside other virtual environments, which may contain
different software or the same software with different versions. An
**environment manager** is a software tool that can create virtual
environments. Environment managers can usually also install, update, and remove
software.
-->

### Environment Managers

An **environment manager** is a software tool to create, keep track of and
switch between collections of software. These collections of software are
called **virtual environments**. When you create a virtual environment, it's
empty, with minimal or no software installed. As you install software into it,
the environment manager records the names and versions of the software (and
sometimes other details). Most environment managers can also save this metadata
to a file that fully describes the virtual environment. You can then use the
file and the environment manager to reproduce the virtual environment on other
computers. In short, using an environment manager directly addresses the need
to document the software in your computing environment by doing the most
tedious parts for you.

Besides making your computing environment easier to reproduce, using an
environment manager also provides several other benefits:

* Most environment managers can download, install, update, and uninstall
  software, so that you don't have to track down links and work through
  multi-step installation instructions.
* New collaborators can quickly set up a virtual environment with the exact
  same software as you. Similarly, you can quickly get set up on other
  computers.
* You can work on multiple projects with incompatible software requirements
  simultaneously by using a separate virtual environment for each project.
  Virtual environments are generally independent and self-contained. For
  example, you might create one virtual environment with R version 4.5 and
  another with R version 3.2, even though these are incompatible.
* When you revisit an old project, you can easily "time travel" back to the
  virtual environment and software you had when you were working on it.

Many different open-source environment managers exist. For most research
computing projects, we recommend and use [Pixi][]. Pixi can:

[Pixi]: https://pixi.sh/

* Install general-purpose software packages (such as Git, R, and Python)
* Install Python packages from PyPI or Conda-Forge
* Install R packages
* Determine dependencies for a given collection of packages you want to use
* Automatically download and install packages
* Create and manage virtual environments on a per-project basis
* Keep track of which packages you installed (and their versions)
* Reproduce an environment from a description


:::{note}
Pixi downloads packages from [conda-forge][], a community-maintained repository
of open-source software. The conda-forge repository was originally created to
support [Conda][], the first environment manager designed specifically for
research computing projects. Thanks to the hard work of its maintainers,
conda-forge contains more than 25,000 packages.

[Conda]: https://docs.conda.io/
[conda-forge]: https://conda-forge.org/

We recommend Pixi rather than Conda because Pixi is faster, provides better
cross-platform support, and provides exact reproductions of virtual
environments (until recently, Conda did not support exact version matching).
Pixi also provides several other features that make it pleasant to use.
:::

```{figure} /images/xkcd_python_environment.png
---
name: xkcd-python
alt:
---
"Python Environment" from ["xkcd"][xkcd] by Randall Munroe
([license][xkcd-license]).
```

We recommend that you create a new virtual environment for each project and
switch between them as needed. Make sure to save the description of the virtual
environment with each project (Pixi does this automatically). If you're also
using a version control system, we recommend using it to track changes to the
environment description file.

:::{seealso}
See DataLab's [Setting Up Software][datalab-pixi] workshop reader for a
detailed introduction to Pixi.

If you exclusively use R and prefer to use an environment manager developed
specifically for R, check out the [renv][] package.

If you prefer to use the original conda, instead see DataLab's [Making Python
Projects & Environments Reproducible][datalab-conda] workshop reader.

[datalab-pixi]: https://ucdavisdatalab.github.io/workshop_reproducible_research/chapters/installing-software/01_environment-managers.html
[renv]: https://rstudio.github.io/renv/
[datalab-conda]: https://ucdavisdatalab.github.io/workshop_intermediate_python/chapters/retired/reproducible.html
:::


### Containerization

While environment managers provide a way to reproduce most of the software (or
at least the open-source software) in your computing environment, they usually
don't account for your computer's operating system. They also don't account for
differences in hardware. One strategy that addresses both of these points is
hardware **virtualization**: make your computer simulate another computer,
complete with its own hardware and operating system, and then do all of your
computing in this virtual computer. A drawback of this approach is that
simulating a computer requires CPU time and memory, so there's less available
for the things you actually want to compute. Nevertheless, virtualization
provides strong guarantees for reproducibility, since everyone who interacts
with your project can use the exact same computing environment you used.

Operating system virtualization, or **containerization**, takes the same
approach as hardware virtualization, but only simulates the operating system,
not the computer hardware. This takes less computing resources away from the
things you want to compute, while still providing most of the reproducibility
guarantees. Containerization began to become popular in the 2010s with the
releases of [Docker][] and [Kubernetes][]. It is now widely-used in industry
and considered a software engineering best practice for ensuring
business-critical software works correctly.

[Docker]: https://www.docker.com/
[Kubernetes]: https://kubernetes.io/

For most projects, we recommend using an environment manager rather than
containerization. Containerization is most useful if your research project
needs to be reproduced by many people and uses software that isn't
well-supported by environment managers, or if containerization is already
widely-used and accepted in your discipline.


### Cloud Computing

Cloud computing services such as [Google Cloud][gcloud], [Amazon Web
Services][aws] (AWS), and [Microsoft Azure][azure] provide hardware and
software on demand. UC Davis provides its own cloud computing service in the
form of [Open OnDemand][ucd-cloud] and (at UC Davis Health) the Advanced
Compute Environment (ACE). Cloud computing's primary benefit is flexibility in
choosing and changing hardware. Most commercial cloud computing services rely
on containerization to manage software, while Open OnDemand and ACE mostly
leave software management to you.

[gcloud]: https://cloud.google.com/
[aws]: https://aws.amazon.com/
[azure]: https://azure.microsoft.com/
[ucd-cloud]: https://docs.hpc.ucdavis.edu/software/ondemand/

From a reproducibility perspective, cloud computing can be beneficial in the
short term, because (especially with commercial services) other researchers can
easily set up and use the exact same hardware and software you used originally
to reproduce your results. However, in the long term, the hardware you used may
stop being available, because cloud computing services periodically update or
change the hardware they offer.

If you decide to use cloud computing, we recommend documenting the details of
the hardware by hand, and using an environment manager or containerization to
manage the software for your project.


## Publish Your Code

> Ten years ago, your lab devised a new method to preprocess and calibrate data
> from an ovisometer, a scientific instrument for non-invasive collection of
> data about sheep. You published a paper with an explanation of the method and
> case studies demonstrating its performance characteristics. To carry out the
> case studies, your co-author implemented the method in the R programming
> language, and ran the code on data you collected. Your co-author did not want
> to publish the code with the paper, insisting that the method is what's
> important, not the implementation.
>
> Today you received an email from someone trying to reproduce your case
> studies. They got vastly different results for the third case study, and
> asked if you'd be willing to share the code from the implementation you used
> in the paper. You don't have a copy of the code, and when you contact your
> co-author, they say they lost track of their copy over the years.

When you develop software as part of a research project, your research is not
completely reproducible unless you make the source code for the software
available along with the other research results. Sharing the code provides
transparency about exactly what you did and allows peers to verify that it
matches what you said you did, which includes examining it for extra steps,
unstated assumptions, and bugs. It also ensures that others can run the code
themselves, reproducing your results.

There are several things to think about when publishing code, which we discuss
in the following sections.


### Document the Code

Provide documentation with your code, so that others will know how to use it
(see {ref}`FIXME`). For code you plan to share, it's especially important to
include set up or installation instructions, instructions for how to run the
code, and an overview of what's included with the code.


### Choose an Open-Source License

A **license** is a legal document that grants others permission to do, use, or
possess something. If you plan to make your code or other research materials
widely/publicly available, it's a good idea to select a license so that you can
retain some control over how they're used and ensure you receive proper credit.

An **open-source** license is one which guarantees that people can freely
access, distribute, and create derivatives of a project and its source
materials. For software, the source material is code. By making the code
available, open-source licenses provide complete transparency about how the
software works. They also encourage people to collaborate on the development
and maintenance of the project. With an open-source license, a project can
remain vibrant and continue to grow even if the original authors stop
participating. For all of these reasons, choosing an open-source license is a
best practice for reproducible research.

DataLab uses open-source licenses for a majority of our projects, whether they
consist of software or other content (like this reader).

Different kinds of licenses are appropriate for different kinds of content.
There are licenses designed specifically for software and code, as well as
licenses for other media. Different licenses also put different conditions on
use and redistribution. For instance, some licenses restrict commercial use and
redistribution.

Choosing a license might seem daunting because so many different licenses
exist, but there are lots of resources available to help. A good starting point
is [choosealicense.com][gh-cal] (maintained by GitHub). Popular licenses tend
to be a good choice because they've withstood the test of time and are familiar
to many people. For software, the GNU Public License (GPL) and MIT License are
particularly popular. For data, writing, art, and other content, [Creative
Commons licenses][cc-cal] are popular; section {ref}`FIXME` provides more
details about licensing non-software content.

[gh-cal]: https://choosealicense.com/
[cc-cal]: https://creativecommons.org/choose/

:::{seealso}
See also the Open Source Initiative's [FAQ answer about which license to
choose][osi-cal] for even more about licensing software.

[osi-cal]: https://opensource.org/faq/#which-license
:::


#### Package the Code

Many programming languages provide standards and tools for creating libraries
or packages of code that can be shared with others. For example, R and Python
both have well-documented package formats and tools to install packages from
centralized repositories such as CRAN and PyPI. Packaging your code makes it
easier for others to obtain, install, and run, and thus makes it easier to
reproduce your results. If you have collaborators, packaging the code early can
also make it easier to share changes and ensure everyone is working with the
same version.

If your research uses a single programming language, look into the best way to
package code for that language. If it uses multiple languages, packaging the
code separately for each language is often a good choice. If you're not sure
what kind of packaging to use, the Conda format might be a good choice, since
it's language-agnostic, and the conda-forge maintainers provide [documentation
about how to create a package][conda-forge-docs].

[conda-forge-docs]: https://conda-forge.org/docs/maintainer/adding_pkgs/


:::{seealso}
To learn more about creating an R package, see the book [R Packages][r-pkg] by
Wickham & Bryan.

To learn more about creating a Python package, see pyOpenSci's [Python Package
Guide][py-pkg] or the [Python Packaging User Guide][pypa].

[r-pkg]: https://r-pkgs.org/
[py-pkg]: https://www.pyopensci.org/python-package-guide/
[pypa]: https://packaging.python.org/
:::


#### Create Automated Tests for the Code

If you develop reusable software as part of your research, it's a good idea to
create automated tests that verify the software works as intended. Automated
tests are specifically helpful for making sure that changes to the code don't
accidentally introduce bugs or remove existing features. This is important from
a reproducible research perspective because bugs introduced over time can make
it difficult or impossible for others to reproduce your results. Tests can also
serve as concrete goals to guide development of the software: write a test that
checks for what the software should be able to do, then write the code to pass
the test.

Automated tests are especially important for software that have many developers
or contributors. A contributor will not necessarily be familiar with all of the
software's features (and their implementation and interdependence), so the risk
of unintentionally breaking something when they make changes is high. Running
the automated tests can provide an early warning about problems and help
pinpoint which code to change to resolve them.

Most programming languages have at least one tool or package for automated
testing. For popular languages, there are often several.

:::{seealso}
If you'd like to write automated tests for R code, we recommend starting with
the [testthat][] package.

If you'd like to write automated tests for Python code, we recommend starting
with the [pytest][] package.

[testthat]: https://testthat.r-lib.org/
[pytest]: https://docs.pytest.org/
:::
