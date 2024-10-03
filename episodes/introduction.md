---
title: "Introduction"
teaching: 23
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
::::::::::::::::::::::: instructor

Lead off script:
*We're all familiar with computers like Macs and PCs. They run an operating system like Windows or Mac, and we can run programs on that computer like web browsers and word processors. The operating system controls all of the physical resources.*


Explain the diagram

- Physical resources, and how the OS controls access to them
- The VMM is a program that gets a slice of those resources and presents them as if they were physical resources to virtual machines
- Define the relationship between the host and guest OS.
- Use the concept of a computer-within-a-computer

::::::::::::::::::::::::::

![An ordinary (unvirtualized) system. The operating system has complete control of the physical hardware resources and is responsible for executing individual applications and allocating those resources to them.](fig/vms-01-resources.png){alt='diagram showing boxes with hardware resources, applications, and the operating system'}

Normally, computers run a single operating system with a single set of applications. Sometimes (for reasons we'll discuss soon), people might want to run a totally separate operating system with a different set of applications. One way to do that is to split up the physical resources like CPU, RAM, etc. and allocate them to that second operating system. The concept of splitting up these resources so that only this second operating system can access them is the idea behind a virtual machine. The operating system inside the virtual machine only sees the virtual resources allocated to it (not the real, physical resources).

![The physical hardware resources are divided between the host operating system and any virtual machines. The virtual machine manager (VMM) takes care of managing the virtualized resources. Each virtual machine only sees the resources allocated to it.](fig/vms-02-virtresources.png){alt='diagram showing boxes with hardware resources, applications, the operating system, and how virtualization shares resources'}

At its core, a virtual machine (referred to as VM from now on) is the self-contained set of operating system, applications, and any other needed files that run on a host machine. The VM files are contained inside of a inside single file (usually) called a VM image. The file you downloaded during the lesson setup is an example of a VM image. 

:::::::::::::::::::::::::::::::::::::callout

One way to think of the concept is that a VM is a computer that runs inside your computer. All the programs that run inside this mini computer can't "see" anything running inside the host (or other VMs). 

::::::::::::::::::::::::::::::::::::

Why would we want to run a mini computer inside of our main computer? VMs are commonly used to 

- Make managing and deploying complex applications easier.
- Run multiple applications and operating systems on the same hardware.

For example, a web application (like your bank's online portal), needs to stay running in case there is a lot of traffic or if the network or server goes down. One way to achieve this is to run several identical servers spread out geographically. While one could install all the software on each server, doing so is complicated by the fact that the physical hardware and software present on each server might be slightly different. Also, we might want to run multiple complex applications on the same server which could result in conflicting software dependencies. VMs help solve these problems.


VMs are also commonly used in academic research scenarios as well as they can help with the problem of research reproducibility by packaging all data and code together so that others can easily re-run the same analysis while avoiding the issue of having to install and configure the environment in the same way as the original researcher. They also help optimize the usage of the computing resources owned by the institution



:::::::::::::::::::::::::::::::::::::callout
Benefits of VMs

- Helps with distributing and managing applications by including all needed dependencies and configurations.
- Increases security by isolating applications from each other.
- Maximizes the use of physical hardware resources by running multiple isolated operating systems at the same time.
:::::::::::::::::::::::::::::::::::::

## What are containers and what do they do?

![Containers are self-contained environments that run using the host operating system's resources. Programs running inside a container only see resources allocated to it via the container manager. For example, from the point of view of the host system, App1's files live in a normal directory somewhere in the file system. From App1's perspective, the only directories that it can directly access on the host are controlled by the container manager.](fig/containers-01.png){alt='diagram showing boxes with hardware resources, applications, containers, and the operating system'}

Containers are conceptually similar to VMs in that they also encapsulate applications and their dependencies into packages that can be easily distributed and run on different physical machines. The big difference is that hardware is not virtualized. This means that applications running in a container must be compatible with the host OS and its hardware. In more technical terms, applications running in a container share the host's kernel and therefore must be compatible with the host's architecture.

Containers are generally more lightweight in terms of disk space and memory requirements than comparable VMs. However, it comes at the cost of portability. Applications inside a container can only run on a compatible host, unlike VMs which can run applications from differing operating systems or hardware architectures.

A core concept is that containers should be ephemeral and all user data and configurations should live outside the container. This means that containers can be created and destroyed quickly and easily without affecting the data that the container depends on. This separation is what enables some of the use cases below.


Examples:

- Web applications (e.g., a web front-end with a database backend -- each running in its own container)
- Data science and machine learning software stacks

Additional characteristics:

- Containers can contain applications from various OSs like Linux or Windows, but containers based on Unix-like OSs (e.g., Linux) are the most common.
- Containers are generally console based. If they have a graphical interface, the main way containers present it is via a web browser.
- Software to create an manage containers is varied. Docker is the most popular one.


:::::::::::::::::::::::::::::::::::::callout
Benefits of containers

- A lighter application footprint (mainly around lower CPU and memory requirements) compared to VMs.
- Quickly and easily update a complex application without affecting any user data or causing issues with conflicting dependencies in the host OS.
- Quickly and easily scale applications. For example, when there is a need to dynamically run multiple instances of an application across a cluster of servers to handle increased demand.
- Robustness of an application stack. If an application is made up of smaller applications that talk to each other via standard mechanisms (e.g., web APIs), it is easier to pinpoint issues and update individual applications.
:::::::::::::::::::::::::::::::::::::



## Comparing virtual machines and containers

|                  | Virtual Machines | Containers |
|------------------|------------------|------------|
| Contains all the dependencies needed to run an application | Yes | Yes |
| Isolates an application from the host OS | Yes | Yes |
| Ease of distribution | Very easy | Easy/hard (depending on complexity and hardware compatibility) |
| Disk space, CPU, and memory requirements | Larger | Smaller |
| Presents virtual versions of real hardware like CPUs, disks, etc | Yes | No |
| Scaling based on computing needs | More difficult | Easier |
| Able to run applications from one operating system on another | Yes | No* |
| Able to run applications from one CPU architecture (e.g., 32 bit x86)  on another (e.g., 64 bit ARM) | Yes (via emulation) | No |


::::::::::::::::::::::::::::::::: challenge


## Challenge 1: 

If you are running a web browser inside a VM, can the host OS see the web pages you're visiting? What your application is making web requests from inside a container? Can the host see the IP addresses your application is connecting to?

:::::::::::::::::::::::: solution 

In both cases, the host can usually see what sites (domain only if using HTTPS) or IP addresses the guest OS or container is connecting to. In the VM case, even though the network hardware is virtualized, the actual data still has to go through the real hardware at some point. For containers, the container already uses the real hardware as if it were running natively in the host and the effect is the same.

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::



::::::::::::::::::::::::::::::::::::: keypoints 

- A virtual machine is a separate computer that runs with its own operating system and applications inside of a host operating system.
- Containers are like lightweight virtual machines with some subtle but consequential differences.
- Containers and virtual machines can address many of the same use cases.
- Both virtual machines and containers are commonly used in academic research but containers are more popular.

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
