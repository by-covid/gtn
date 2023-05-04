# Submitting workflows to LifeMonitor

[LifeMonitor](https://www.lifemonitor.eu/) (LM) is a service to support the
sustainability and reusability of published computational workflows. The
LifeMonitor helps alleviate the burden of maintaining workflows over time
through **automation**.

This document will show you **how to use the
[LifeMonitor](https://www.lifemonitor.eu/) service and its [GitHub
app](https://github.com/apps/lifemonitor)** on a workflow in a GitHub
repository.

## Why use the LifeMonitor?

Keeping workflows reusable takes work! Like all software, even the best
workflows can break over time if left unmaintained: for instance, there could be
a regression or an API change in an unpinned dependency, or an external resource
that the workflow relies upon might be moved to a different URL. Periodic
automated **testing** is a fundamental practice that helps expose such problems,
giving workflow maintainers a chance to intervene and fix them.  The
[LifeMonitor](https://www.lifemonitor.eu/) helps you monitor and periodically
execute the automated tests for your workflow.

Moreover, workflows should be findable to be reusable.
[LifeMonitor](https://www.lifemonitor.eu/) helps automate the generation of
[RO-Crate metadata](https://www.lifemonitor.eu/workflow_testing_ro_crate) as
well as registering new releases of your workflow with the
[WorkflowHub](https://workflowhub.eu).

Finally, [LifeMonitor](https://www.lifemonitor.eu/) can apply automated checks
to your workflow repository to help you follow [community best
practices](https://by-covid.github.io/gtn/galaxy-best-practices).


## Pre-conditions

We assume you **published a Galaxy workflow** to a GitHub repository following the
[*Galaxy Community best
practices*](../galaxy-best-practices#community-best-practices).

In addition, we assume you have followed the same best practices to [**create
tests** for your
workflow](../galaxy-best-practices#generating-tests-for-your-workflow) using
[Planemo](https://planemo.readthedocs.io/en/latest/best_practices_workflows.html#tests),
as well as configuring a [GitHub Actions
workflow](../galaxy-best-practices#adding-a-github-workflow) to automatically
run those tests.  Don't worry if this sounds like a lot: the [best
practices*](../galaxy-best-practices) document provides straightforward
instructions.

### Running example

As a running example, we're going to use a simple "sort and change case"
workflow: it merely takes a text file, sorts the lines and swaps the case of
all the letters.  You can access and inspect this example workflow, its tests
and its GitHub Action through [this link](./sort-and-change-case-workflow/).


## Installing the LM GitHub App

The [LM GitHub App](https://github.com/apps/lifemonitor) provides the most
straightforward way to use LM with your GitHub-hosted workflow. The app can do
the following things. 

* Examine your repository and apply a series of automated *checks*.
* Suggest pull requests to make changes or additions to bring the workflow
  repository closer to conforming to best practices.
* Open issues to let you know about problems detected by the checks:
  * in some cases, you can interact with the LifeMonitor bot through the issues,
      to provide information or issue commands.
* Register new releases/versions of the workflow with both the [LifeMonitor
  service](https://app.lifemonitor.eu/) (for test monitoring) and the
  [WorkflowHub](https://workflowhub.eu/) workflow registry.


Follow the instructions provided by the [LifeMonitor
documentation](https://www.lifemonitor.eu/lm_wft_best_practices_github_app#installation)
to complete the app installation on your repository, and:

* we recommend that you enable the LifeMonitor "Issue Checks";
* we also recommend that you enable the automatic upload to the
    [WorkflowHub](https://workflowhub.eu/).

:bulb: Note that completing the installation steps may require you to create an
account with both LifeMonitor and WorkflowHub.  We recommend **using [LS
Login](https://lifescience-ri.eu/ls-login/)** to authenticate with both
services.

:bulb: You will also need to connect your GitHub account to your LifeMonitor
account.






Examples of popular platforms that help set up automated testing (and more) are
[GitHub
Actions](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions),
[Jenkins](https://www.jenkins.io/) and [Travis CI](https://www.travis-ci.com/).
LifeMonitor is a service that can connect with the above platforms, collecting
test results for multiple workflows and presenting them under a single
[graphical interface](https://app.lifemonitor.eu/dashboard).
