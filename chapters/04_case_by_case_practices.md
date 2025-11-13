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

### Make Workflow Diagrams

:::{seealso}
See DataLab's [README, Write Me! workshop reader][datalab-readme] for
suggestions about how to create workflow diagrams.
:::

[datalab-readme]: https://ucdavisdatalab.github.io/workshop_how-to-data-documentation/#workflow-diagrams


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




Project Organization
--------------------

### Make a Package


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



### Use a Build System

:::{seealso}
See DataLab's and DIB Lab's [Automating Your Analyses with the Snakemake
Workflow System workshop reader][datalab-snakemake] for a technical
introduction to snakemake.
:::

[datalab-snakemake]: https://ngs-docs.github.io/2021-august-remote-computing/automating-your-analyses-with-the-snakemake-workflow-system.html


### Use Integration Tests

#### On Unit Tests

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
