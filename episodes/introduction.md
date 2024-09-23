---
title: "Introduction"
teaching: 20
exercises: 2
---

<!-- required section -->
:::::::::::::::::::::::::::::::::::::: questions 

- What are virtual machines and containers?
- How are they used in open science?

::::::::::::::::::::::::::::::::::::::::::::::::

<!-- required section -->
::::::::::::::::::::::::::::::::::::: objectives

- Explain the main components of a virtual machine and a container and list the major differences between them
- Explain at a conceptual level how these tools can be used in research workflows to enable open and reproducible research

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

You might have heard of containers and virtual machines in various contexts. For example, you might have heard of 'containerizing' an application, running an application in 'Docker', 'spinning up' a virtual machine in order to run a certain program.

This lesson is intended to provide a hands-on primer to both virtual machines and containers. We will begin with a conceptual overview. We will follow it by hands-on explorations of two tools: VirtualBox and Docker.

If you forget what a particular term means, refer to the [Glossary](reference.html).

:::::::::::::::::::::::prereq
This lesson assumes no prior experience with containers or virtual machines. However, it does assume basic knowledge about computer and networking concepts. These include

- Ability to install software (and obtaining elevated/administrative rights to do so), 
- Basic knowledge of the components of a computer and what they do (CPU, network, storage)
- Knowledge of how to navigate your computer's directory structure (either graphically or via the command line).

Prior exposure to using command line tools is useful but not required.
:::::::::::::::::::::::

## What are virtual machines and what do they do?

We're all familiar with computers like Macs and PCs. They run an operating system like Windows or Mac, and we can run programs on that computer like web browsers and word processors. The operating ssystem controls all of the physical resources.

![An ordinary (unvirtualized) system. The operating system has complete control of the physical hardware resources and is responsible for executing individual applications and allocating those resources to them.](fig/vms-01-resources.png){alt='diagram showing boxes with hardware resources, applications, and the operating system'}

Normally, computers run a single operating system with a single set of applications. Sometimes (for reasons we'll discuss soon), people might want to run a totally separate operating system with a different set of applications. One way to do that is to split up the physical resources like CPU, RAM, etc. and allocate them to that second operating system. The concept of splitting up these resources so that only this second operating system can access them is the idea behind a virtual machine. The operating system inside the virtual machine only sees the virtual resources allocated to it (not the real, physical resources).

![The physical hardware resources are divided between the host operating system and any virtual machines. The virtual machine manager (VMM) takes care of managing the virtualized resources. Each virtual machine only sees the resources allocated to it.](fig/vms-02-virtresources.png){alt='diagram showing boxes with hardware resources, applications, the operating system, and how virtualization shares resources'}

At its core, a virtual machine (referred to as VM from now on) is the self-contained set of operating system, applications, and any other needed files that run on a host machine. The VM files are contained inside of a inside single file (usually) called a VM image. The file you downloaded during the lesson setup is an example of an image. 

:::::::::::::::::::::::::::::::::::::callout

One way to think of the concept is that a VM is a computer that runs inside your computer. All the programs that run inside this mini computer can't "see" anything running inside the host (or other VMs). 

::::::::::::::::::::::::::::::::::::

Why would we want to run a mini computer inside of our main computer? Vs are commonly used in enterprise settings to make managing and deploying complex applications easier. For example, a web application (like your bank's online portal), needs to stay running in case there is a lot of traffic or if the network or server goes down. One way to achieve this is to run several identical servers spread out geographically. While one could install all the software on each server, doing so is complicated by the fact that the physical hardware and software present on each server might be slightly different. Also, we might want to run multiple complex applications on the same server which could result in conflicting software dependencies. VMs help solve these problems

VMs help with

- Running applications on different physical computers by encapsulating all the files and dependencies needed to run them (including the operating system)
- Distributing applications with complex dependencies and configurations so that others can run them more easily.
- Securing applications so that they are isolated from each other.
- Getting the most use of physical hardware resources by running multiple isolated operating systems at the same time instead of running one operating system per physical computer.

Examples of VM usage in research scenarios

- Packaging data and software together into a VM image so others can more easily reproduce results or conduct their own analysis using the same tools and configuration used by the original researcher. 
- Providing computing resources to researchers. For example, a research institution might wish to give access to licensed software to researchers. The institution might set up virtual machines with the software already installed where researchers can then log into remotely to access it.

## What are containers and what do they do?

Containers are conceptually similar to VMs in that they also encapsulate applications and their dependencies into packages that can be easily distributed and run on physical machines that have different underlying hardware and operating systems. 

## Comparing virtual machines and containers


::::::::::::::::::::::::::::::::::::: keypoints 

- A virtual machine is a separate computer that runs with its own operating system and applications inside of a host operating system
- A virtual machine manager handles the sharing of resources and execution of the virtual machine itself.
- Both virtual machines and containers are commonly used in academic research. 

::::::::::::::::::::::::::::::::::::::::::::::::

<!--
:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::: instructor

Inline instructor notes can help inform instructors of timing challenges
associated with the lessons. They appear in the "Instructor View"

::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge 

## Challenge 1: Can you do it?

What is the output of this command?

```r
paste("This", "new", "lesson", "looks", "good")
```

:::::::::::::::::::::::: solution 

## Output
 
```output
[1] "This new lesson looks good"
```

:::::::::::::::::::::::::::::::::


## Challenge 2: how do you nest solutions within challenge blocks?

:::::::::::::::::::::::: solution 

You can add a line with at least three colons and a `solution` tag.

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

## Figures

You can use standard markdown for static figures with the following syntax:

`![optional caption that appears below the figure](figure url){alt='alt text for
accessibility purposes'}`

![You belong in The Carpentries!](https://raw.githubusercontent.com/carpentries/logo/master/Badge_Carpentries.svg){alt='Blue Carpentries hex person logo with no text.'}

::::::::::::::::::::::::::::::::::::: callout

Callout sections can highlight information.

They are sometimes used to emphasise particularly important points
but are also used in some lessons to present "asides": 
content that is not central to the narrative of the lesson,
e.g. by providing the answer to a commonly-asked question.

::::::::::::::::::::::::::::::::::::::::::::::::


## Math

One of our episodes contains $\LaTeX$ equations when describing how to create
dynamic reports with {knitr}, so we now use mathjax to describe this:

`$\alpha = \dfrac{1}{(1 - \beta)^2}$` becomes: $\alpha = \dfrac{1}{(1 - \beta)^2}$

Cool, right?

::::::::::::::::::::::::::::::::::::: keypoints 

- Use `.md` files for episodes when you want static content
- Use `.Rmd` files for episodes when you need to generate output
- Run `sandpaper::check_lesson()` to identify any issues with your lesson
- Run `sandpaper::build_lesson()` to preview your lesson locally

::::::::::::::::::::::::::::::::::::::::::::::::

[r-markdown]: https://rmarkdown.rstudio.com/
-->
