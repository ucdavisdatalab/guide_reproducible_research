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


