---
title: Rocky Linux Release Version Guide
---

This page goes over the Rocky Linux Release Versions, their support, timelines, and how it affects our users.

## Current Supported Releases

Below is a table of Rocky Linux versions, with accompanying general release and (planned or are planned) end of life dates.

| Major Version  | Codename       | Release Date  | Active Support       | End of Life          | Latest Version           |
|----------------|----------------|---------------|----------------------|----------------------|--------------------------|
| Rocky Linux 8  | Green Obsidian | June 21, 2021 | May 31, 2024         | May 31, 2029         | 8.9 (November 22, 2023)  |
| Rocky Linux 9  | Blue Onyx      | July 14, 2022 | May 31, 2027         | May 31, 2032         | 9.3 (November 20, 2023)  |

Click any of the tabs below to obtain more information about a current release.

{% include "releng/version_table.md" %}

See the timeline and release cadence sections below for more information on how these dates are determined.

## Timeline

For a major release of Red Hat Enterprise Linux and thus Rocky Linux, the following should be true:

* Major version is released with support of ten (10) years (exception is Rocky Linux 8, which started at 8.4)
* Five (5) years of minor release updates

    * There is generally one (1) major release with ten (10) minor release updates
    * Minor releases come typically every six (6) months
    * Minor releases generally come with new features, modules, and sometimes software rebases

* After five (5) years of minor releases, Enterprise Linux and derivatives go into maintenance only mode for the remainder of its life

### Release Cadence

Based on the cadence set out by Red Hat, the months of May and November are generally when minor releases should be released. May is also generally when major releases arrive. Rocky Linux attempts to follow as closely as possible to this same cadence.

Below is a general guideline (based on Red Hat documentation) for the "full support" cycle for an Enterprise Linux distribution.

| Version | Month    |
|---------|----------|
| .0      | May      |
| .1      | November |
| .2      | May      |
| .3      | November |
| .4      | May      |
| .5      | November |
| .6      | May      |
| .7      | November |
| .8      | May      |
| .9      | November |
| .10     | May      |

Upon a new minor release (`X.Y+1`), the previous Rocky Linux release is no longer supported and is moved to the [vault](repo.md#vault).

After `X.10` is released, the following may be true:

* Maintenance Mode starts for the next five (5) years
* No more minor releases; `X.10` is considered the final release version and only this receives updates until End of Life
* CentOS Stream X will cease development (likely before release)

## Version Policy

Rocky Linux attempts to follow the same pattern as Red Hat Enterprise Linux. As such, releases aim to be as on time as possible as they are released upstream.

For Rocky Linux 8, previous versions of packages will coexist in the repositories to allow a user to downgrade in case of a regression or other use cases (such as security only updates).

Rocky Linux 9 does not currently support this policy and can be expected in a future Rocky Linux 9 version. Please see [Peridot Issue #18](https://github.com/rocky-linux/peridot/issues/18). Older versions of packages can by found in [Koji](https://kojidev.rockylinux.org) when they're uploaded.

For all Rocky Linux versions: When a new minor release arrives, all previous updates/versions are *not* carried over.

### General Update Timeline

Updates for Rocky Linux are generally expected to be built and released between twenty-four (24) and fourty-eight (48) hours, assuming best effort allows the packages to build without any complications or unforeseen added dependencies by upstream mid-support cycle.

Minor releases for Rocky Linux are generally expected to be built and released at least a week (7 days) after upstream, assuming best effort allows the packages to build without any complications and it passes the Testing Team OpenQA and general testing.

## End of Life and Unsupported Release Policy

A version of Rocky Linux is considered unsupported if:

* The Rocky Linux version has been superseded by another minor release *or*
* The Rocky Linux release is End of Life

See the examples below.

### Example: An Unsupported Release

When a new Rocky Linux minor release arrives (using version format `X.Y`, `Y+1` or an increment of `Y`) the following is true:

* The previous version is no longer supported by Release Engineering and the community
* This version is no longer updated and is moved to the [vault](http://dl.rockylinux.org/vault/rocky/).
* This version does not receive bug fix nor security updates.
* You are recommended to update your system with `dnf update`.

### Example: An End of Life Release

When a Rocky Linux release has reached its End of Life date typically after ten (10) years (for example, May of 2029), the following is true:

* The release is no longer supported in full by Release Engineering and the community
* The final version is moved to the [vault](http://dl.rockylinux.org/vault/rocky/).
* This release no longer receives updates and thus no longer supported.
* You are recommended to install a supported Rocky Linux version and migrate your data.

If you cannot install a new system and migrate and you still need support for your system or systems, you may be able to find a support provider. Note that support providers will maintain their own packages and policies outside of the Rocky Linux ecosystem, and thus their policies *do not* apply here. The release is still considered EOL and unsupported by the Rocky Linux project.

## Beta to Stable Policy

Rocky Linux may release beta versions that are typically in line with the upstream Red Hat Enterprise Linux beta releases. These are released specifically to find bugs or issues in our build process as well as correlate the issues with the upstream beta in case they also have bugs. These are released typically to the Testing team members and others in the community (whether or not they're publicly announced) and are free to download and test by anyone else.

When the stable version is released, updating from the beta to the stable version is not a supported nor recommended system setup.

The following is unsupported:

* Updating from a stable release to beta release
* Updating from a beta release to stable release

## Upgrade Policy

Upgrades are not generally supported by Release Engineering nor most of the Rocky community. If you wish to perform upgrades between releases, there is a tool called ELevate that can help you. But as a note of caution, this has not been formally tested and we cannot provide official assistance.
