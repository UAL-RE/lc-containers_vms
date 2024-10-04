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

![A conceptual representation of an ordinary computer system. The operating system oversees the physical hardware resources and is responsible for executing individual applications and allocating those resources to them.](fig/vms-01-resources.png){alt='diagram showing boxes with hardware resources, applications, and the operating system'}

Normally, computers run a single operating system with a single set of applications. Sometimes (for reasons we'll discuss soon), people might want to run a totally separate operating system with a different set of applications. One way to do that is to split up the physical resources like CPU, RAM, etc. and present them to that second operating system for its exclusive use. The concept of splitting up these resources (i.e., virtualizing them) so that only this second operating system can access them is the idea behind a virtual machine. 
![In a virtual machine, physical hardware resources are divided between the host operating system and any virtual machines (guest operating systems). The virtual machine manager (VMM) takes care of managing the virtualized resources. Each virtual machine only sees the resources allocated to it.](fig/vms-02-virtresources.png){alt='diagram showing boxes with hardware resources, applications, the operating system, and how virtualization shares resources'}

At its core, a virtual machine (referred to as VM from now on) is a self-contained set of operating system, applications, and any other needed files that run on a host machine. The VM files are usually encapsulated inside of a inside single file called a VM image. The file you downloaded during the lesson setup is an example of a VM image. 

:::::::::::::::::::::::::::::::::::::callout

One way to think of the VM concept is a computer that runs inside your computer. All the programs that run inside this mini computer can't "see" anything running outside of it, either in the host or other VMs running on the same physical computer.

::::::::::::::::::::::::::::::::::::

Why would we want to run a mini computer inside of our main computer? VMs are commonly used to 

- More easily manage and deploy complex applications.
- Run multiple operating systems and their applications on the same physical hardware.

### Examples:

- Deploying a complex application on several servers. Your bank's internal systems need to be robust against risks like hardware failure, hacking, weather events, etc. One way to achieve this is to run several identical servers spread out geographically. While one could install all the software on each server, using a VM reduces complexity by allowing the same software and associated configurations to be quickly deployed and managed across varying hardware
- Maximize usage of available hardware. Many cloud computing providers like Amazon allow users to purchase resources on their systems. To maximize their investment, these companies will set up a virtual server for each customer. Functionally, these virtual servers behave as a standalone machine but in reality, there may be dozens of other virtual servers running on the same physical system


VMs are also commonly used in academic research scenarios as well as they can help with the problem of research reproducibility by packaging all data and code together so that others can easily re-run the same analysis while avoiding the issue of having to install and configure the environment in the same way as the original researcher. They also help optimize the usage of the computing resources owned by the institution. You might have interacted with VMs at your institution if you've ever logged into a "remote desktop" or "virtual computing environment" that many instutions use to provide access to licensed software.



:::::::::::::::::::::::::::::::::::::callout
Benefits of VMs

- Help with distributing and managing applications by including all needed dependencies and configurations.
- Increase security by isolating applications from each other.
- Maximize the use of physical hardware resources by running multiple isolated operating systems at the same time.
:::::::::::::::::::::::::::::::::::::

## What are containers and what do they do?

![Containers are environments that encapsulate applications and their dependencies. Applications running inside a container are functionally isolated from the host. The container manager runs containers and determines what each container can "see" outside of itself.](fig/containers-01.png){alt='diagram showing boxes with hardware resources, applications, containers, and the operating system'}

Containers are conceptually similar to VMs in that they also encapsulate applications and their dependencies into packages that can be easily distributed and run on different physical machines. A notable difference is that when using containers, hardware is not virtualized and containerized applications must be compatible with the host OS and its hardware. In more technical terms, applications running in a container share the host's kernel and therefore must be compatible with the host's architecture. In practical terms, this means that containers:

- Are generally less resource-intensive than comparable VMs, at the cost of portability. 
- Are not able to run, for example, Windows applications on Linux, or applications written for one CPU architecture on a system with a different architecture.

### Two core concepts

#### Ephemerality

Containers should be considered ephemeral so that they can be destroyed and recreated at any time such that the application within simply resumes as if nothing had happened. Therefore, containerzied applications must be designed in such a way that allows the container manager to save all user data and configurations outside of the container. This separation is what enables some of the use cases below.

#### Modularization
A popular approach to leveraging containers is modularizing a complex application into "microservices", each running in their own container. This helps with maintenance, scalability, and troubleshooting.


### Examples

- Web applications. E.g., a web front-end with a database backend -- each running in its own container. In this case, the ephemerality concept allows for easily updating the software, while being sure that the data won't be affected. The microservices concept allows, for example, easily replacing one database software with another without needing to touch the front-end software at all. 
- Data science, data management, and other research uses. In these applications, the same benefits of ephemerality and modularization via microservices can be realized. Furthermore,  containers enable reuseable, reproducible, and cloud-native workflows. Finally, due to their lighter weight and the ability to define and create containers via plain-text blueprints (e.g., Dockerfiles -- more on that later), containers have become more popular than virtual machines in research environments.

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
| Able to run applications from one operating system on another | Yes | Sometimes* |
| Able to run applications from one CPU architecture (e.g., x86)  on another (e.g., ARM) | Yes (via emulation) | No |

* It's possible in some cases. For example, Docker on Windows can run Linux containers because it secretly runs them inside a Linux VM.

::::::::::::::::::::::::::::::::: challenge


## Challenge 1: 

If you are running a web browser inside a VM, can the host OS see the web pages you're visiting? What about making web requests from inside a container? Can the host see the IP addresses your containerized application is connecting to?

:::::::::::::::::::::::: solution 

In both cases, the host can usually see what sites or IP addresses the guest OS or container is connecting to. In the VM case, even though the network hardware is virtualized, the actual data still has to go through the real hardware at some point. For containers, the container already uses the real hardware as if it were running natively in the host and the effect is the same.

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
