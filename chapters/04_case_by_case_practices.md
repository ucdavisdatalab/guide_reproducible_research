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


### Use Continuous Integration

#### Lint the Code

#### GitHub Actions


Environment Management
----------------------

### Use Virtualization

#### Containers

#### Virtual Machines

### Go to the Cloud



### Publish Your Code

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


#### Document the Code

Provide documentation with your code, so that others will know how to use it
(see {ref}`FIXME`). For code you plan to share, it's especially important to
include set up or installation instructions, instructions for how to run the
code, and an overview of what's included with the code.


#### Choose an Open-Source License

A **license** is a legal document that grants others permission to do, use, or
possess something. If you plan to make your code widely or publicly available,
it's a good idea to select a license so that you can retain some control over
how it's used and protect yourself against certain kinds of legal claims.

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
it's language-agnostic and the conda-forge maintainers provide [documentation
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
