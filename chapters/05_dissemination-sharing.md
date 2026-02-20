# Dissemination & Sharing


(choose-a-license)=
## Choose a License

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


## Release the Data

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


## Open Methods

You can also release or publish your methods and materials as additional open
access research products. This practice helps not only make your research
process transparent, but it also makes your study reproducible and verifiable,
and your approach reusable. Your published paper might explain the methods, but
in order to reproduce your findings, more information on your design, protocol,
materials, etc. is probably needed.

**Open methods** refers to publishing, either formally or informally, all the
details of your processes, procedures, and materials openly so that someone
else could perform your study exactly as you did. Examples may include
protocols, surveys and questionnaires, lab notebooks, equipment settings,
video demonstrations, software and code, and more.

You have many options for sharing these methods and materials. You could add
them as supplementary information files along with a published article, deposit
them in a specific repository (e.g. [protocols.io][protocols-io],
[PROSPERO][prospero]), have them peer reviewed and formally published in a
journal (e.g. registered reports, study protocols, or other methods articles),
or share them publicly another way (e.g. [GitHub][github], [Open Science
Framework][OSF], [Open Lab Notebooks][open-lab-notebooks], [Journal of Visual
Experiments (JoVE)][jove]). You may also need to or want to preregister your
study plan before conducting the research (e.g. a clinical trials registry,
registered reports, [Open Science Framework][OSF]). 

[protocols-io]: https://www.protocols.io/
[github]: https://github.com/
[OSF]: https://osf.io/
[open-lab-notebooks]: https://openlabnotebooks.org/ 
[prospero]: https://www.crd.york.ac.uk/prospero/
[jove]: https://www.jove.com/education/science-education

:::{important}
Some materials and procedures may be not be appropriate to share due to
privacy, confidentiality, security, intellectual property, or other rights or
requirements. 
:::

You should also ensure your methods and materials follow FAIR principles using
the following practices:

**Findable:**
* Publish or deposit with an open access publisher or repository.
* Assign a persistent identifier to your materials, such as a Digital Object
  Identifier (DOI). (This can usually be done by depositing in a repository.)
* Properly cite the methods and materials in any other related published
  materials.

**Accessible:**
* Publish or deposit in an open access repository.
* Include proper metadata describing access, authentication, and authorization.

**Interoperable:**
* Publish the materials in standard, non-proprietary formats.
* {ref}`use-file-formats-effectively`

<!-- FIXME: Other links to other sections??? -->
**Reusable:**
* Provide metadata and adequate documentation for reuse.
* Publish under an open license.

:::{seealso}
Learn more about licensing in the {ref}`open-licenses` section.

Visit the {ref}`sec-prefer-open-source-software` section for more information
on open-source code and software.
:::


(sec-open-access)=
## Publish as Open Access 

Not having access to a piece of research or its underlying data and materials
can be the main roadblock to reproducibility. Open access not only allows
anyone to access and read the papers, but it also permits reproducibility,
replicability, and the opportunity to build on or reuse all or part of your
work in a future project to advance science and knowledge. Many grant providers
and institutions may also require your work to be published open access.

:::{important} Open Licenses

Applying an open license to your materials is key to making them openly
available. Open licenses allow anyone to view, share, and reuse materials. See
more in the {ref}`open-licenses` section below.
:::


### Publish Open Data

Study data are often stored privately, but sharing your data is an integral
part of reproducibility. Research simply cannot be reproduced without access to
the data underlying the results, figures, tables, and conclusions.

**Open data** refers to data shared publicly and licensed under an open license
so that it can be freely accessed, reused, and shared by anyone. Many grant
providers, institutions, and publishers now require underlying data to be
shared openly.

You can deposit your data in open data repositories to make them freely
available. Whether you want a generalist or specialist repository, look for a
reliable repository that meets the following requirements:

* Uses open licenses
* Assigns Persistent Identifiers (PID), such as digital object identifiers
  (DOI), to the dataset(s)
* Plans for long-term maintenance, continued access, and preservation of the
  datasets.
* Financially stable
* No burdensome access requirements for readers, such as registration fees,
  membership requirements, etc.
* Contact information, documentation, and staff or representatives are
  available to address issues and offer user support.

Learn more about trustworthy data repository requirements from
[CoreTrustSeal][cts-repositories-requirements].

[cts-repositories-requirements]: https://www.coretrustseal.org/why-certification/requirements/

<!-- FIXME -->
:::{note}
Some data may be personal or sensitive. Do not share your data openly if they
are protected, nationally or commercially sensitive, contain identifying
information, or you have not obtained proper consent. You can learn more about
considerations for these types of data (maybe Turing Way?)
:::

You should also ensure your data follow FAIR principles using the following
practices:

**Findable:**

* Publish or deposit in an open access repository.
* Assign a persistent identifier to your dataset, such as a Digital Object
  Identifier (DOI). (This can usually be done by depositing in a repository.)
* Properly cite the data in any related published materials.

**Accessible:**

* Publish or deposit in an open access repository.
* Include proper metadata describing access, authentication, and authorization.

**Interoperable:**

* Publish data and metadata in standard, non-proprietary formats.
* {ref}`use-file-formats-effectively`

**Reusable:**

<!-- FIXME: Other links to other sections??? -->
* Provide metadata and adequate documentation for reuse.
* Publish under an open license.
* Properly cite your source data.

:::{seealso}
See UC Davis Library's [Research Data Management Guide][RDM-guide-data-sharing]
to learn more about how to share your data openly.

Review the {ref}`open-licenses` section below to learn more about publishing
your data under an open license.
:::

[RDM-guide-data-sharing]: https://guides.library.ucdavis.edu/data-management/data-sharing


### Publish Open Access Articles

Publishing an open access article reduces barriers for readers and researchers
by making it freely accessible.

Publishing your work in an open access journal or as an open access monograph
is known as **Gold Open Access**. It generally goes through the same review
process that any submission would, but is then published openly, usually
through an open license, so that anyone can read it without having to pay a
subscription or access fee.

Learn more about open access publishing, including finding reputable journals
and avoiding predatory publishers, and open access funding support at UC Davis
on our [Open Access Publishing Library Guide][open-access-guide].


#### Pre-Prints and Post-Prints

Publishing research Open Access can be expensive and therefore may not always
be feasible. University of California authors may have [Open Access fee
assistance][open-access-guide] available to them. However, authors with no fee
assistance have other options for making their work openly available and,
therefore, reproducible.

[open-access-guide]: https://guides.library.ucdavis.edu/open-access-publishing

Authors can make their work openly available by self-archiving it somewhere
accessible, such as an institutional repository or preprint server. This is
also known as **Green Open Access**. Note that the archived version may be
different than a peer-reviewed and formally published version.

<!-- FIXME -->
**Preprints** are publicly available papers that have not (yet) been peer
reviewed. Usually, authors will post a paper to a preprint server under an
[open license](#open-licenses) after the paper has been written and before
submitting to a journal for peer review and publication. Some preprints are
never submitted or accepted to a journal for formal publication.

[open-licenses]: {ref}`open-licenses`

:::{important}
Articles are often revised, sometimes significantly, during the peer-review
process. A published version of an article in a journal may differ greatly from
a preprint version.
:::

**Post-prints**, or author-accepted manuscripts, have been peer-reviewed and
accepted for publication, then made publicly available somewhere accessible,
such as an institutional repository. These versions are usually the same as or
very similar to the published versions.

:::{important}
Different publishers have different policies about sharing author-accepted
manuscripts, including potential embargo periods. Refer to your publisher’s
policies or [Jisc’s Open Policy Finder][open-policy-finder] to understand your
sharing permissions.
:::

[open-policy-finder]: https://openpolicyfinder.jisc.ac.uk/

:::{seealso}
To learn more about Open Access options, the [Open Access
Network][open-access-network] is a great educational resource that discusses
Diamond, Gold, and Green Open Access.
:::

[open-access-network]: https://open-access.network/en/information/open-access-primers/green-and-gold


(open-licenses)=
### Open Licenses

A **license** grants others permission to possess, copy, and/or use a piece of
work in a variety of ways. An **open license** makes a work freely available
for others to read, copy, distribute, and use without obtaining permission from
the author or creator. Open licenses also provide free, immediate, and
perpetual access to the content. 

For code, an open-source license ensures that software can continue to be
maintained and extended even if the original developers cease development. They
also promote transparency and collaboration, since anyone with the software can
inspect and modify the code.

When an open license is applied to a work, the author or creator retains the
rights to/ownership of the original work, and most open licenses require that
proper credit be given to the creator.

[Creative Commons][creative-commons] licenses are the most common open licenses
for articles and datasets. MIT licenses are common for open code, but many more
are available, as discussed by the [Open Source
Initiative][open-source-licenses].

[creative-commons]: https://creativecommons.org/
[open-source-licenses]: https://opensource.org/licenses

Many open licenses allow for any type of use and reuse, including
modifications, distribution, etc., but authors have options for open licenses
with certain restrictions such as no commercial use or no derivatives, or a
requirement that any copies or adaptations be licensed under a similar open
license.

:::{seealso}
For licensing data, writing, art, or other materials, see Creative Commons'
[Choose a License page][cc-cal] for help deciding on a Creative Commons
license.

For licensing software, see [choosealicense.com][gh-cal] to help you choose an
open license (maintained by GitHub) or the Open Source Initiative's [FAQ answer
about which license to choose][osi-cal].
:::


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
(see {ref}`write-readmes`). For code you plan to share, it's especially
important to include set up or installation instructions, instructions for how
to run the code, and an overview of what's included with the code.


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
Commons licenses][cc-cal] are popular; section {ref}`sec-open-access` provides
more details about licensing non-software content.

:::{seealso}
See also the Open Source Initiative's [FAQ answer about which license to
choose][osi-cal] for even more about licensing software.
:::


### Package the Code

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


### Create Automated Tests for the Code

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
