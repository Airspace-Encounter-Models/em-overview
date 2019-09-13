# How to contribute

We encourage the use of the [GitHub Issues](https://guides.github.com/features/issues/) for bug report, new feature requests, etc. To streamline reporting, issues will only be enabled for the [em-overview](https://github.com/airspace-encounter-models/em-overview/) repository.

Due to the encounter models routine use in aviation research, we like to minimize the risk of inadvertent bugs or software challenges to maintain the encounter models as a trusted benchmark. To encourage traceability, development should occur via [forking](https://guides.github.com/activities/forking/).

- [How to contribute](#how-to-contribute)
  - [Code of Conduct](#code-of-conduct)
  - [Roadmap](#roadmap)
  - [Workflow](#workflow)
  - [Bugs](#bugs)
    - [Reporting Bugs](#reporting-bugs)
    - [Patching Bugs](#patching-bugs)
    - [Cosmetic Patch](#cosmetic-patch)
  - [Enhancements and New Features](#enhancements-and-new-features)
    - [Requesting features](#requesting-features)
    - [Developing features](#developing-features)
    - [Requesting documentation](#requesting-documentation)
  - [Convention Guide](#convention-guide)
    - [Documentation](#documentation)
    - [Variable Names](#variable-names)
    - [Units](#units)
    - [Colors](#colors)
  - [Questions about the source code](#questions-about-the-source-code)
  - [Distribution Statement](#distribution-statement)

## Code of Conduct

This project and everyone participating in it is governed by the [Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to [encounter-model-ml-admin@mit.edu](mailto:encounter-model-ml-admin@mit.edu).

## Roadmap

No public technology roadmap for development is available yet. As the encounter models transition to a more community-focused model, this may change.

## Workflow

A variety of organizations from academia, federal agencies, federal funded research and development centers (FFRDC), and industry have supported encounter model development. Each organization has different policies on release review and procedures to disseminate content. Organizations may also have their own enterprise self-hosted version control systems.

We recommend the following workflow that perseveres content part of the [airspace-encounter-models](https://github.com/airspace-encounter-models) organization as a "gold benchmark" while promoting a traceable workflow for contributors.

![Workflow](images/workflow.png)

We'll use an illustrative example with MIT Lincoln Laboratory, a FFRDC with strict release review policies, with their public [mit-ll](https://github.com/mit-ll) organization and a private enterprise system to explain this workflow. For organizations that permit public development, ignore steps with the enterprise instance.

1. The repository required for development is identified in [airspace-encounter-models](https://github.com/airspace-encounter-models)
2. This repository is forked by the [mit-ll](https://github.com/mit-ll) organization.
3. The new repository on [mit-ll](https://github.com/mit-ll) organization is cloned by the enterprise self-hosted GitHub. Note you can't fork from public to private, see this Stack Overflow question for mitigations: [Is it possible to fork a public GitHub repo into an enterprise repository?](https://stackoverflow.com/q/29952033)
- Prior to any changes, there are now three instances of the repository: a private enterprise clone (airspace-encounter-models-internal), a public fork ([mit-ll](https://github.com/mit-ll)), and the original ([airspace-encounter-models](https://github.com/airspace-encounter-models)).
4. Development is conducted using branches on the enterprise clone.
5. When development is over, the clone will be released review according to internal policies.
6. Once the clone is approved for public release, changes will be pushed to the public fork.
7. A pull request will be opened to contribute back to the original.
8. The encounter model administrators will review the pull request and either accept or reject it.

## Bugs

According to [Wikipedia](https://en.wikipedia.org/wiki/Software_bug), a software bug is a:
> A software bug is an error, flaw, failure or fault in a computer program or system that causes it to produce an incorrect or unexpected result, or to behave in unintended ways.

### Reporting Bugs

- **Ensure the bug was not already reported** by searching on GitHub under [Issues](https://github.com/airspace-encounter-models/em-overview/issues).
- If you're unable to find an open issue addressing the problem, [open a new one](https://github.com/airspace-encounter-models/em-overview/issues) using the [bug report](.github/ISSUE_TEMPLATE/bug_report.md) template. Be sure to include a title, a clear description, and as much relevant information as possible.
- Confirm that the bug report template assigned a BUG label to the issue.

### Patching Bugs

- Open a new GitHub pull request with the patch.
- Ensure the pull request description clearly describes the problem and solution. Include the relevant issue number if applicable.
- Before submitting, please read the [convention guide](#convention-guide) to know more about coding conventions and recommended units.

### Cosmetic Patch

Changes that are cosmetic in nature, such as fixing whitespaces characters or formatting code, and do not add anything substantial to the stability, functionality, or testability will generally not be accepted. Our rational aligns with those expressed by the [Ruby on Rails team](https://github.com/rails/rails/pull/13771#issuecomment-32746700).

## Enhancements and New Features

According to [Wikipedia](https://en.wikipedia.org/wiki/Software_feature) and IEEE 829, a software feature is a:
> A distinguishing characteristic of a software item (e.g., performance, portability, or functionality.

### Requesting features

- **Ensure the feature was not already requested** by searching on GitHub under [Issues](https://github.com/airspace-encounter-models/em-overview/issues).
- If you're unable to find an open issue for the desired feature, [open a new one](https://github.com/airspace-encounter-models/em-overview/issues) using the [feature request](.github/ISSUE_TEMPLATE/feature_request.md) template. Be sure to include a title, a clear description, and as much relevant information as possible.
- Confirm that the feature request template assigned an ENHANCEMENT label to the issue.

### Developing features

- Fork the repository associated with the feature request and develop the desired capabilities
- Open a new GitHub pull request with the enhancement
- Ensure the pull request description clearly addresses the feature request. Include the relevant issue number. Unlike bugs, enhancements without a traceable issue number will not have the pull request accepted.
- Before submitting, please read the [convention guide](#convention-guide) to know more about coding conventions and recommended units. Some documentation and code commenting is required for the pull request to be accepted too.

### Requesting documentation

Requesting more or a clarification of documentation is a valid feature request. Note as a community development project, it would be nearly impossible to enforce authors of a specific piece of code to respond to the documentation request.

## Convention Guide

### Documentation

**Pull requests with no documentation will be rejected.** We believe documentation is good and integral to the success of a community software project. However, we recognize that everyone has different expectations and opinions on code documentation. [Self-documenting code](https://en.wikipedia.org/wiki/Self-documenting_code) should be sufficient in most cases but the use of inline comments to organize blocks of code are encouraged.

### Variable Names

- When applicable, variable names should include units, such as `speed_kt` or `el_ft_msl`. 
- Delimiter-separated words should use an underscore, `_`
- Variable names should be short yet meaningful. The choice of a variable name should be mnemonic — that is, designed to indicate to the casual observer the intent of its use. One-character variable names should be avoided except for temporary "throwaway" variables. Common names for temporary variables are `i`, `j`, `k`.

### Units

We employ units commonly used by the United States aviation community. We strongly recommend converting to these units as soon as possible when reading in data. We discourage converting to a different units within stand alone functions or as part of intermediate code. **Excess use of non U.S. aviation units may prompt a rejection of a pull request.**

For more information, refer to Aviation Stackexchange: "[Why doesn't the aviation industry use SI units?](https://aviation.stackexchange.com/q/2572)" and "[What is the measurement system used in the aviation industry?](https://aviation.stackexchange.com/q/2566)"

Dimension | Unit
------------ | -------------
time | [second (s)](https://en.wikipedia.org/wiki/Second)
length - altitude & elevation | [foot (ft)](https://en.wikipedia.org/wiki/Foot_(unit))
length - longitudinal and lateral distance | [foot (ft)](https://en.wikipedia.org/wiki/Foot_(unit)) or [nautical mile (nm)](https://en.wikipedia.org/wiki/Nautical_mile)
speed - vertical rate | [foot per second (fps)](https://en.wikipedia.org/wiki/Foot_per_second)
speed - airspeed or ground speed | [knot (kts)](https://en.wikipedia.org/wiki/Knot_(unit))
plane angle - course, heading, roll, pitch, yaw | [degree (deg)](https://en.wikipedia.org/wiki/Degree_(angle))
latitude & longitude coordinates | [decimal degrees (DD)](https://en.wikipedia.org/wiki/Decimal_degrees)
world geodetic system | [WGS 84 (EPSG:4326)](https://epsg.io/4326)
mass | [pound mass (lb)](https://en.wikipedia.org/wiki/Pound_(mass))
force | [pound force (lbf)](https://en.wikipedia.org/wiki/Pound_(force))
temperature | [degree Fahrenheit (°F)](https://en.wikipedia.org/wiki/Fahrenheit)

### Colors

To promote accessibility and align with graphic best practices, we recommend a color guidelines proposed by B. Wong that is perceived as reasonably distinct by both normal and color blind individuals. Selecting a widely perceived color scheme is particularly important for peer reviews, as B. Wong notes:

> If a submitted manuscript happens to go to three male reviewers of Northern European descent, the chance that at least one will be color blind is 22 percent...The palette of eight colors shown [below] has good overall variability and can be differentiated by individuals with red-green color blindness.

![Colors optimized for color-blind individuals](images/nmeth.1618-F2.jpg)

<details> <summary> B. Wong, “Points of view: Color blindness,” Nature Methods, vol. 8, pp. 441–441, May 2011.</summary>
<p>

```tex
@article{wongPointsViewColor2011,
	title = {Points of view: {Color} blindness},
	volume = {8},
	copyright = {2011 Nature Publishing Group},
	issn = {1548-7105},
	shorttitle = {Points of view},
	url = {https://www.nature.com/articles/nmeth.1618},
	doi = {10.1038/nmeth.1618},
	language = {en},
	urldate = {2019-08-27},
	journal = {Nature Methods},
	author = {Wong, Bang},
	month = may,
	year = {2011},
	pages = {441--441},
	}
```
</p>
</details>

## Questions about the source code

Please contact the administrators at [encounter-model-ml-admin@mit.edu](mailto:encounter-model-ml-admin@mit.edu). As the encounter models transition to a more community driven effort, a separate mailing list for code discussion may be created.

## Distribution Statement

DISTRIBUTION STATEMENT A. Approved for public release. Distribution is unlimited.

This material is based upon work supported by the Federal Aviation Administration under Air Force Contract No. FA8702-15-D-0001.

Any opinions, findings, conclusions or recommendations expressed in this material are those of the author(s) and do not necessarily reflect the views of the Federal Aviation Administration.

This document is derived from work done for the FAA (and possibly others), it is not the direct product of work done for the FAA. The information provided herein may include content supplied by third parties.  Although the data and information contained herein has been produced or processed from sources believed to be reliable, the Federal Aviation Administration makes no warranty, expressed or implied, regarding the accuracy, adequacy, completeness, legality, reliability or usefulness of any information, conclusions or recommendations provided herein. Distribution of the information contained herein does not constitute an endorsement or warranty of the data or information provided herein by the Federal Aviation Administration or the U.S. Department of Transportation.  Neither the Federal Aviation Administration nor the U.S. Department of Transportation shall be held liable for any improper or incorrect use of the information contained herein and assumes no responsibility for anyone’s use of the information. The Federal Aviation Administration and U.S. Department of Transportation shall not be liable for any claim for any loss, harm, or other damages arising from access to or use of data or information, including without limitation any direct, indirect, incidental, exemplary, special or consequential damages, even if advised of the possibility of such damages. The Federal Aviation Administration shall not be liable to anyone for any decision made or action taken, or not taken, in reliance on the information contained herein.
