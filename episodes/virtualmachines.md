---
title: "Virtual machines using VirtualBox"
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions 

- How do you import and launch a VM using VirtualBox?
- How do you accomplish common tasks?
- How and why do you change settings for a VM?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Explain how to navigate the VirtualBox interface
- Demonstrate how to run a VM
- Show how to manage resources
- Show how to take advantage of snapshots
- Explore changing resource allocations

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

Let's now turn to exploring how to use virtual machines (VMs). There are [many choices](https://en.wikipedia.org/wiki/Comparison_of_platform_virtualization_software) for running virtual machines, each with their own strengths and weaknesses. The ones you may encounter more often are the VMWare family of products, Hyper-V which is included with Windows, Parallels which is a product for MacOS, and VirtualBox which is owned by Oracle Corporation and is cross-platform and open-source.

As part of the [setup](index.html), you should have already have VirtualBox installed and running on your system before continuing.

## Running the example VM

::::::::::::::::::::::: instructor

Users may be prompted to use the Basic or Expert interface. Make sure students know what they see may not be exactly what is on your screen

::::::::::::::::::::::: 

Exploring the UI
- Run VirtualBox
- import the VM
- run it
- see a desktop
- proper way to stop the VM

## Common tasks?
- Suspend, resume
- Snapshots
- Mapping folders and hardware resources (?)

::::::::::::::::::::::::::::::::: challenge
## Challenge 1: 

Take a snapshot of the VM. Start the VM and suspend it. Now Delete the parent snapshot. What will be the result if you boot up the VM again?


:::::::::::::::::::::::: solution 

Todo

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::


## Managing VMs

::::::::::::::::::::::::::::::::: challenge
## Challenge 2: 

Increase the RAM available to the VM to 2 GB (2048 MB). Verify it by running this command inside a terminal window
```
cat /proc/meminfo | grep MemTotal
```
What number do you see? What should be the effect on the VM's performance?


:::::::::::::::::::::::: solution 

You should see `2014504 kB`. Performance should increase, especially when applications are loading a lot of data into memory. Web browsers are especially heavy memory users.

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints 

- VM point 1

::::::::::::::::::::::::::::::::::::::::::::::::

