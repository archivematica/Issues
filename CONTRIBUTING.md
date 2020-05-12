# Contributing

The Archivematica Issues repository is the place to file Archivematica bug
reports as well as make suggestions for new or enhanced features. Anyone with a
GitHub account can add an issue, comment on someone else's issue, or make a pull
request to the pages in the repo.

As of July 2018, all new issues related to Archivematica or its companion
repositories should be filed in this repo. Prior to July 2018, issues were filed
in different repositories in the https://github.com/artefactual and
https://github.com/artefactual-labs/ organizations.

More information about contributing to the Archivematica project can be found
here:
https://github.com/artefactual/archivematica/blob/stable/1.11.x/CONTRIBUTING.md

## Security

If you have a security concern about Archivematica or any of its companion
repositories, please do not file it here. See the [security policy](SECURITY.md)
in this repository for directions on how to report security issues.

## Filing an issue

All changes to Archivematica or its companion libraries should start with an
issue, including bug fixes, new features, and enhancements to existing features.

To file an issue, go to [the Issues
tab](https://github.com/archivematica/Issues/issues) and click the green **New
issues** button in the top right-hand corner. You can select the appropriate
template from the list. Fill out the template with as much information as you
can.

An issue should describe a behaviour without implying a solution. The pull
request that may follow, if changes to the codebase are necessary, fixes the
problem. Framing your issue as a problem statement helps everyone understand why
the issue is important - it describes how Archivematica is not performing as it
should (bug) or as it could (enhancement). Please title your issue as a problem
statement, starting with "Problem:". You can check [existing
issues](https://github.com/archivematica/Issues/issues) for examples.

### Reporting a bug

To report a bug, select **Bug report template** from the issue templates and
fill out the fields with as much information as possible.

You can also post in our
[user](https://groups.google.com/forum/#!forum/archivematica) mailing list. A
post to the mailing list is always welcome, especially if you're unsure if it's
a bug or a local problem!

Useful information to provide includes:

* What version of Archivematica and the Storage Service are you using?
* How was Archivematica installed? Package install, Ansible, etc?
* Was this a fresh install or an upgrade?
* What did you do to cause this bug to happen?
* What did you expect to happen?
* What did you see instead?
* Can you reproduce this reliably?
* If a specific job is failing, what output did it produce? This is available by
  clicking on the gear icon to the right of the job name.

### Submitting an enhancement idea

To suggest a new feature or an enhancement to an existing feature, select
**Feature request** from the issue templates and fill out the fields with as
much information as possible.

### Submitting a documentation report

To report an issue with the Archivematica documentation, select **Documentation
report template** from the issue templates and fill out the fields with as much
information as possible. Please try to provide a link to the specific section
where the issue occurs.

## Adding labels

[Labels](https://github.com/archivematica/Issues/labels) help to organize issues
and pull requests. Only members of the Archivematica GitHub organization can add
labels. Artefactual has created a [list of reserved
labels](https://docs.google.com/spreadsheets/d/1hPeZTL0XuWBxk021VAnmYWiRX6Sc3Ch1wMknO0gkLAA/edit#gid=1813603898)
for reference.

Reserved labels are maintained by Artefactual and must not be deleted, changed,
or added to without the express consent of the Product Owner. Adding new labels
to the reserved set should only be done after communal discussion and with a
clearly-defined need in mind. Reserved labels always begin with one of the
following four terms:

* **REQUEST** labels are an at-a-glance way to indicate to other community
  members that an issue needs extra attention (i.e. `Request: help wanted`)
* **SEVERITY** labels indicate the level of seriousness of a reported problem
  (i.e. `Severity: critical`)
* **STATUS** labels indicate the state that an issue is in during different
  phases of development. Some of these labels are used by external tools that
  Artefactual uses to manage issues (i.e. `Status: ready`)
* **TYPE** labels indicate the nature of the issues as it relates to the extent
  of the code change (i.e. `Type: bug`)

Unreserved labels can be created on the fly by anyone who is a member of the
Archivematica repository. Theme labels (i.e. `Continuous integration`) are meant
to help community members see related issues and to facilitate searching. Client
labels (i.e. `IISH`) are used by Artefactual to track client work, and will be
regularly deleted to keep the list of available labels manageable. Sponsorship
of a feature is always maintained in the release notes. Colours don't matter,
but try not to use any of the reserved colours.

## Becoming a member of the Archivematica GitHub organization

If you want to become a member of the Archivematica GitHub organization, send us
an email at info@artefactual.com.
