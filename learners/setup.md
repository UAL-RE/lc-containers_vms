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

::::::::::::::::::::::::::::: instructor

Instructors are responsible for creating the prebuilt virtual machine and hosting it somewhere accessible to instructors. 

### Building
This lesson will use a single virtual machine for both the virtual machine AND container episodes. Instructors will be responsible for creating this virtual machine image and distributing it to students. The image should be based on a lightweight Linux distribution that has a graphical desktop environment and is able to run Docker. The Debian-based DietPi distribution is one recommendation as it is light on resources and is easily configurable. 

Virtual machine image creation instructions for the Debian Bookworm-based DietPi.

- Follow steps 1-3 of the DietPi VirtualBox installation guide. Ignore the Wifi and Virtualbox extension pack instructions in step 3.  https://dietpi.com/docs/install/#__tabbed_1_2. At the end, you should see the DietPi login prompt. ![DietPi login prompt](instructors/fig/dietpi-login-prompt.png)
- Log in as `root` using the given password. 

  - The DietPi configuration wizard will launch. Use Tab or the arrow keys on your keyboard to change the selection, Enter to confirm a selection.
  - If your keyboard is captured by VirtualBox, you will not be able to use your keyboard/mouse on your main operating system. Press the right `CTRL` key (on Windows) to return the keyboard/mouse to your main operating system.

- In the configuration wizard
  - Opt out of the DietPi survey. Upon selecting `Ok`, the VM will reboot. Let it reboot and the wizard will continue
  - Select the `Generic 105-Key PC` for the keyboard configuration. Select `Ok`
  - Select the `English (US) keyboard layout` (under Other). Select `Ok`
  - Select `No Alt-Gr` and `No compose key` in the next two dialogs.
  - In the dialog that asks to change the global software password, select `Cancel`
  - In the dialog that asks to change the password of the `root` and `dietpi` users, select `Cancel`
  - After completing these steps, you should see the software installation wizard ![DietPi setup menu window](instructors/fig/dietpi-software-menu.png)

- In the software installation wizard
  - Select Browse Software from the menu. Then from the list that appears, select (use the arrow keys to navigate, spacebar to select):
    - `23 LXDE ultra lightweight desktop`
    - `134 Docker compose`
    - `162 Docker`
    - `67 Firefox`
  - Select `Confirm` to return to the main menu
  - From the main menu, select `Install`, then click `Ok` to begin ![DietPi software installation confirmation window](instructors/fig/dietpi-software-install-confirmation.png)
  - Wait for the software to install. On success, the system will return you to a command prompt with the root user already logged in. 
  - Type `dietpi-config` to launch the configuration
  - Select `Autostart` from the menu
  - Select `2: Automatic Login` ![DietPi autologin setup window](instructors/fig/dietpi-autologin-setup.png)
  - Then select `root`, and select `Ok` to confirm
  - Exit out of the menus and exit out of the configuration tool. You should see a command prompt at the bottom of the window. 
  - At the prompt, type `reboot` to reboot the VM.
  - If successful, the system should reboot and you should see a graphical desktop with a green DietPi wallpaper. You may optionally remove this wallpaper via the Desktop Preferences.
  - At this point, the size of the Virtualbox image should be just over 2.5 GB in size.

- Set up Docker according to the lesson

  - TODO

- Shut down the VM via the menus inside the graphical desktop or from the terminal
- Export the image as a VirtualBox appliance (.ova file)



### Hosting
The .ova file can be hosted on any online file sharing service with sufficient space like Box, Google Drive, DropBox, etc. 

If there are many learners, remain mindful of any bandwidth limits. For example, Google Drive may cut off access to publicly shared files that exceed a certain amount of transferred data within a certain time period. Therefore, you may wish to host the file on two different services or accounts.

:::::::::::::::::::::::::::::


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

