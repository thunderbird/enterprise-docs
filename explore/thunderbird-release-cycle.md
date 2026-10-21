---
description: Thunderbird Release and Extended Support Release (ESR) channels for organizations
---

# Thunderbird release channels and lifecycle

## Overview

Thunderbird offers two stable release channels for organizations: **[Release](https://support.mozilla.org/kb/thunderbird-release)** and **[Extended Support Release (ESR)](https://support.mozilla.org/kb/thunderbird-esr)**.
Both receive security and stability updates, but differ in how frequently new features and improvements are introduced.

**Thunderbird Release is the default channel** and provides updates every two weeks, allowing organizations to benefit from new features, improvements, and bug fixes as they become available. For organizations able to accommodate regular application changes, Release is a good choice.

**Thunderbird ESR** follows an annual major release cycle and is designed for organizations that require a more predictable environment, with fewer feature changes throughout the year.

The choice between Release and ESR depends on an organization's deployment practices, compatibility requirements, and capacity to test and manage updates.

## Release cycle details

### Thunderbird Release

As of September 2026, Thunderbird Release follows a two-week release cycle, delivering new features, improvements, and security updates on a regular basis. Release dates generally align with the [Mozilla platform release calendar](https://whattrainisitnow.com/calendar/).

These updates typically include:

- Security updates
- New features and functionality
- Improvements to existing features and the user interface
- Stability and correctness fixes

Additional point releases may be issued between releases to address important issues.

The bi-weekly release cycle provides a more continuous delivery of improvements, avoiding the larger accumulation of changes associated with annual upgrades. Organizations with established testing and deployment processes may find this approach easier to manage.

### Thunderbird Extended Support Release (ESR)

Thunderbird ESR follows an annual major release cycle, with maintenance updates provided throughout its supported lifetime.

ESR maintenance updates focus on high-risk or high-impact security vulnerabilities and major stability fixes. Off-schedule releases may also be issued to address critical security issues.

New features and functional enhancements are typically reserved for the next annual ESR release rather than backported to existing ESR versions.

ESR is particularly suitable for organizations that require longer periods of functional consistency, extensive compatibility testing, or tighter control over application changes.

### Overlap between ESR versions

{% hint style="info" %}
Successive Thunderbird ESR versions have a six-release-cycle overlap (approximately 12 weeks). This provides organizations time to test and deploy the new ESR version before the previous version reaches end-of-life.
{% endhint %}

During the overlap period, organizations can evaluate compatibility with extensions, enterprise policies, and their existing deployment environment.

At the end of an ESR version's support period:

- The version reaches end-of-life.
- No further security or maintenance updates are provided for that version.
- An update to the next supported ESR version is offered through Thunderbird's application update service.

## Choosing a release channel

Both Release and ESR are supported options for organizational deployments.

| Consideration           | Release                                            | ESR                                                              |
| ----------------------- | -------------------------------------------------- | ---------------------------------------------------------------- |
| Major release frequency | Every Two Weeks                                    | Annually                                                         |
| New features            | Delivered regularly                                | Primarily with annual upgrades                                   |
| Security updates        | Regular updates                                    | Regular maintenance updates                                      |
| Functional changes      | More frequent, incremental changes                 | Fewer changes between major versions                             |
| Best suited for         | Organizations comfortable managing regular updates | Organizations requiring longer periods of functional consistency |

**Release is worth considering as the preferred option** where an organization's testing, deployment, and change-management processes can accommodate monthly updates. It provides faster access to improvements and fixes without waiting for the next annual ESR.

ESR remains a good choice where minimizing changes to application behaviour is more important than receiving new functionality quickly.

Organizations using Thunderbird extensions or integrations should verify compatibility with their selected release channel before deployment.

## Managing updates

Thunderbird supports automatic application updates, which we recommend keeping enabled to ensure timely delivery of security fixes.

System administrators can manage updates using enterprise policies and deployment tools, including controlling when updates are installed.

Organizations should test new releases against their required extensions, configurations, and workflows before broad deployment.

## Upgrade path between ESR versions

Thunderbird normally offers automatic upgrades between major ESR versions after the initial overlap period, allowing organizations time to evaluate the new version.

For example, an organization using ESR version X would ordinarily be offered an automatic upgrade to ESR version Y around the release of Y.3.0.

Administrators managing updates centrally can coordinate this transition according to their deployment requirements.

Organizations considering a change between Release and ESR should review the applicable migration guidance and test the transition before deploying it broadly.

## Staying informed

Organizations are encouraged to join the [Thunderbird Enterprise discussion group](https://thunderbird.topicbox.com/groups/enterprise) to stay informed about release changes, enterprise deployment considerations, and upcoming updates.

Administrators can also consult the [Thunderbird ESR support article](https://support.mozilla.org/kb/thunderbird-esr) for additional information about the ESR lifecycle.
