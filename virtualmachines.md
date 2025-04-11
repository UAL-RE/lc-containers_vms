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

Let's now turn to exploring how to use VMs. There are [many choices](https://en.wikipedia.org/wiki/Comparison_of_platform_virtualization_software) for running virtual machines, each with their own strengths and weaknesses. The ones you may encounter more often are the VMWare family of products, Hyper-V which is included with Windows, Parallels which is a product for MacOS, and VirtualBox which is owned by Oracle Corporation and is cross-platform and open-source.

As part of the [setup](index.html), you should have already have VirtualBox installed and running on your system before continuing.

## Running the example VM

::::::::::::::::::::::: instructor

Users may be prompted to use the Basic or Expert interface. Make sure students know what they see may not be exactly what is on your screen

::::::::::::::::::::::: 

First, run VirtualBox. Depending on your operating system and exact system configuration, you may get different popups asking for certain permissions or showing you some notifications. Grant all the permissions it asks for and close any popups (if the popup shows an error, ask the instructor for help). You may also get a question asking whether you want to use the "basic" or "expert" interface (choose basic).

You should see a window that resembles this:
![VirtualBox UI on Windows](fig/vbox-gui-win.png)


Now, let's import the VM you downloaded previously

- Extract the Zip file you downloaded into a folder somewhere on your system.
- In VirtualBox, click the big green '+ Add' button
- In the popup, locate the extracted folder and open the .vbox file (on Windows, this file has a blue icon).
- After doing so, a new entry will appear in VirtualBox underneath the Tools row in the left-hand sidebar.

Start the VM

- Select the imported VM if it isn't selected already
- Click the green "-> Start" button
- Accept any additional dialogs that pop up (if any)
- A new window will appear that shows some commands being run, followed by a graphical desktop.

::::::::::::::::::::::::::::::::::::: callout

Look for and open the Firefox browser in the VM. What do you notice about interacting with stuff inside the VM? How is it different or the same than your normal computer?

::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::: instructor

If students get an error opening VirtualBox or importing the VM, there may be something you can do (reinstalling, rebooting, checking there is enough disk space, making sure they are importing the right file). 

If they have an error trying to run the VM, there is less you can do. Some things to try would be tinkering with the VM settings under the System or Display categories

- Making sure they downloaded the right VM for their system
- Reducing the base memory
- Playing with the Paravirtualization Interface choice under the Acceleration tab (expert mode must be selected at the top of the settings for the tab to appear).
- Increasing the video memory

If none of that works, there is nothing else you can do and they will have to pair up with someone that has it working. 

::::::::::::::::::::::: 


## Common tasks

### Shutting down the VM
To properly turn off the VM, use the functionality built into the guest OS. In our case, go to Applications in the top right corner and look for the log out icon at the bottom of the popup menu.

Another way to to turn off the VM is to close the window the VM is running in. On Windows, click the 'X' at the top right corner of the VM window. You should see a popup that's similar to this. 
![Closing the VM](fig/vbox-close-vm.png)

There are three options, two that look like they can turn off the machine. Select the option to "send the shutdown signal". The VM should power off. Not all VMs can be cleanly shut down this way.

::::::::::::::::::::::::::::::::: challenge
## Challenge 1: 

Boot up the VM again and close it using the dialog with the three options. What do you think the difference is between the "send the shutdown signal option" and the "power off the machine" option?


:::::::::::::::::::::::: solution 

The "power off the machine option" is the equivalent of ripping out the power cable from the wall. It will immediately terminate the VM without trying to gracefully allow the guest OS to shut down. This might result in data loss or even render the machine unbootable.

:::::::::::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::

### Saving execution states
- Snapshots


::::::::::::::::::::::::::::::::: challenge
## Challenge 1: 

Take a snapshot of the VM. Start the VM and suspend it. Now Delete the parent snapshot. What will be the result if you boot up the VM again?


:::::::::::::::::::::::: solution 

Todo

:::::::::::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::


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
:::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: keypoints 

- VM point 1

::::::::::::::::::::::::::::::::::::::::::::::::

