---
title: Setup
---

<!--
FIXME: Setup instructions live in this document. Please specify the tools and
the data sets the Learner needs to have installed.
-->

## Data Sets

<!--
FIXME: place any data you want learners to use in `episodes/data` and then use
       a relative link ( [data zip file](data/lesson-data.zip) ) to provide a
       link to it, replacing the example.com link.
-->
We will be using a prebuilt virtual machine that already contains most things needed to get started.  Download the [.ova file](#) to your system but do not do anything else with it at the moment. We will import it as part of the [virtual machines](virtualmachines.html) episode.


## Software Setup

::::::::::::::::::::::::::::::::::::::: discussion

### VirtualBox

<!--
Setup for different systems can be presented in dropdown menus via a `spoiler`
tag. They will join to this discussion block, so you can give a general overview
of the software used in this lesson here and fill out the individual operating
systems (and potentially add more, e.g. online setup) in the solutions blocks.
-->

VirtualBox is the software we will be using for this lesson. Your computer must meet these requirements:

- A recent Intel or AMD CPU 
- Windows, Linux, or MacOS (see the sections below for additional information).
- Administrative access
- 8 GB of total memory
- 7 GB of free disk space

Most laptops that are newer than 5-6 years should work.

The prebuilt virtual machine image you downloaded previously contains a preconfigured Docker installation which will be used for the containers portion of the lesson.

:::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::: spoiler

### Windows

Although VirtualBox runs under older version of Windows, at least Windows 10 v1803 is needed to minimize the chance for conflicts if there is other virtualization software installed (e.g., Hyper-V). 

- On the [downloads page](https://www.virtualbox.org/wiki/Downloads) under the VirtualBox Platform Packages section, select Windows hosts.
- Install the downloaded package.

::::::::::::::::::::::::

:::::::::::::::: spoiler

### MacOS

There are different download packages depending if you have an Intel Mac or an 
If you have a Mac with an Intel CPU or an Apple Arm CPU (M1, M2, or M3).

- Intel Macs: On the [downloads page](https://www.virtualbox.org/wiki/Downloads) under the VirtualBox Platform Packages section, select MacOS / Intel hosts
- Apple M1, M2, or M3: On the [Test builds](https://www.virtualbox.org/wiki/Testbuilds) page, download the MacOS / ARM64 Dev Preview file. This version of VirtualBox is experimental and may or may not work for you.

Install the downloaded package.

::::::::::::::::::::::::


:::::::::::::::: spoiler

### Linux

We recommend installing VirtualBox from your distribution's package manager. If the version that comes with your distribution is different than the version used in this lesson, the screenshots might differ. If you wish to install the latest version, follow the [instructions](https://www.virtualbox.org/wiki/Linux_Downloads) for your distribution.

::::::::::::::::::::::::

