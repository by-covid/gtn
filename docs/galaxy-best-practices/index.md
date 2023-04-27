# Best practices for workflows in GitHub repositories

A workflow, just like any other piece of software, can be formally correct and runnable but still lack a number of additional features that might help its reusability, interoperability, understandability, etc.

One of the most useful additions to a workflow is a suite of tests, which help check that the workflow is operating as intended. A test case consists of a set of inputs and corresponding expected outputs, together with a procedure for comparing the workflow's actual outputs with the expected ones. It might be the case, in fact, that a test may be considered successful even if the actual outputs do not match the expected ones exactly, for instance because the computation involves a certain degree of randomness, or the output includes timestamps or randomly generated identifiers. Providing documentation is also important to help understand the workflow's purpose and mode of operation, its requirements, the effect of its parameters, etc. Even a single, well structured README file can go a long way towards getting users started with your workflow, especially if complemented by examples that include sample inputs and running instructions.


## Community best practices

Though the practices listed above can be considered general enough to be applicable to any kind of software, individual communities usually add their own specific sets of rules and conventions that help users quickly find their way around software projects, understand them more easily and reuse them more effectively. The Galaxy community, for instance, has a [guide on best practices for maintaining workflows](https://planemo.readthedocs.io/en/latest/best_practices_workflows.html): this includes instructions on how to structure inputs and outputs, annotate workflow steps, specify a license and a creator, adding tests, etc.

The [Intergalactic Workflow Commission (IWC)](https://github.com/galaxyproject/iwc) is a collection of highly curated Galaxy workflows that follow best practices and conform to a specific GitHub directory layout, as specified in the [guide on adding workflows](https://github.com/galaxyproject/iwc/blob/main/workflows/README.md#adding-workflows). In particular, the workflow file must be accompanied by a [Planemo test file](https://planemo.readthedocs.io/en/latest/test_format.html) with the same name but a `-test.yml` extension, and a `test-data` directory that contains the datasets used by the tests described in the test file. The guide also specifies how to fulfill other requirements such as setting a license and a version tag. A new workflow can be proposed for inclusion in the collection by opening a pull request to the [IWC repository](https://github.com/galaxyproject/iwc): if it passes the review and is merged, it will be published to [iwc-workflows](https://github.com/iwc-workflows). The publication process also generates a metadata file that turns the repository into a [Workflow Testing RO-Crate](https://crs4.github.io/life_monitor/workflow_testing_ro_crate), which can be registered to [WorkflowHub](https://workflowhub.eu/) and [LifeMonitor](https://www.lifemonitor.eu/).


## Best practice repositories and RO-Crate

The [repo2rocrate](https://github.com/crs4/repo2rocrate) software package allows to generate a [Workflow Testing RO-Crate](https://crs4.github.io/life_monitor/workflow_testing_ro_crate) for a workflow repository that follows community best practices. It currently supports Galaxy (based on IWC guidelines), Nextflow and Snakemake. The tool assumes that the workflow repository is structured according to the community guidelines and generates the appropriate [RO-Crate](https://w3id.org/ro/crate/) metadata for the various entities. Several command line options allow to specify additional information that cannot be automatically detected or needs to be overridden.

To try the software, we'll clone one of the iwc-workflows repositories, whose layout is known to respect the IWC guidelines. Since it already contains an RO-Crate metadata file, we'll delete it before running the tool.

```
pip install repo2rocrate
git clone https://github.com/iwc-workflows/parallel-accession-download
cd parallel-accession-download/
rm -fv ro-crate-metadata.json
repo2rocrate --repo-url https://github.com/iwc-workflows/parallel-accession-download
```

This adds an `ro-crate-metadata.json` file at the top level with metadata generated based on the tool's knowledge of the expected repository layout. By specifying a zip file as an output, we can directly generate an RO-Crate in the format accepted by WorkflowHub and LifeMonitor:

```
repo2rocrate --repo-url https://github.com/iwc-workflows/parallel-accession-download -o ../parallel-accession-download.crate.zip
```