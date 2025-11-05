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


Environment Management
----------------------

### Use Virtualization

#### Containers

#### Virtual Machines

### Go to the Cloud



### Publish Your Code

> Your lab invented a specialized scientific instrument, an ovisometer, to
> collect data about sheep. You preprocess and calibrate the raw data from the
> ovisometer with SheepWorks, a piece of software, before doing any analysis.
> An important part of the calibration process is running the DRYSHEEP
> algorithm on the data. The algorithm is widely used in your discipline, but
> known to perform poorly for data collected on high-humidity days. Since your
> lab is in sunny California, you just avoid collecting data on high-humidity
> days.
>
> A friend and fellow researcher in New England emails you with a large
> collection of ovisometer readings, hoping you can collaborate on a new paper.
> They asked you to preprocess the data and begin analysis, but there's a
> problem: all of the data are from high-humidity days.
>
> A postdoc in your lab mentions they read a paper about an extension of
> DRYSHEEP, called WETSHEEP, that works well for both low- and high-humidity
> days, and volunteers to modify the SheepWorks code to implement the
> algorithm. Unfortunately, you don't *have* the code for SheepWorks, because
> it's closed-source software. You try contacting the publisher of SheepWorks,
> but they refuse to provide a copy of the code. Modifying DRYSHEEP to run
> WETSHEEP only requires a few changes, but implementing DRYSHEEP from the
> ground up is a challenging, time-consuming task. You tell the postdoc you'll
> have to think about how to proceed.



#### Package Your Code


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
