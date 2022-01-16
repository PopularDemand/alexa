---
layout: post
title: Setting Up Docker Desktop for Windows and WSL2
excerpt_separator: <!--more-->
---

Windows Subsystem Linux provides an intuitive Linux development interface for Windows users.

Unlike the usual Linux Docker installation process where the Docker process is installed and
runs as a Linux process,
To develop Docker applications within Windows Subsystem Linux, Docker Desktop must be installed and running within the Windows operating system.

<!--more-->

Docker Desktop and WSL2 are built with integrations such that docker container information and functions
are shared between the Desktop application and `docker` commands from the Linux CLI.

Cursory experience with WSL and Docker Desktop has shown the integrations to work seemlessly once installed.
This is a solution walkthrough of installing Docker Desktop for Windows and WSL2 Development.

---

## Prerequisites

Before you install Docker Desktop, you must complete the following steps:

#### Install Windows 10, version 1903 or higher or Windows 11.

WSL is not supported on earlier Windows operating systems.

#### Enable WSL 2 feature on Windows.

**Important:** The Linux distro must be running in WSL 2, not WSL 1. If the distro is using WSL 1, it can be changed to WSL 2 with a simple command.

```
# Check what version WSL your linux distros are running (from Windows)
> wsl.exe -l -v
  NAME                   STATE           VERSION
* Ubuntu-18.04           Running         2
```

<p style="text-align:center">
	<img src="/assets/img/posts/wsl-l-v.png" style="width:50%;min-width:320px;" />
</p>

```
# Upgrade existing distro to WSL2 (from Windows)
> wsl.exe --set-version [distro_name] 2
```

Warning: Changing the version takes up all your RAM. It's a huge memory operation, and the only community solutions are to a) patch the process to have max-memory consumption or b) start the process and expect the PC to be locked up for a bit of time. I went with option B, and it took approximately an hour. See the Github issue in the references for more details.

#### Have a project that can be initiated with `docker-compose up`.

See the reference link *Get Started with Docker Compose* for a walkthrough of creating such a project if you do not yet have this.


## Download

Download [Docker Desktop 2.3.0.2](https://docs.docker.com/desktop/windows/wsl/#download) or a later release.

## Install

Follow the usual installation instructions to install Docker Desktop. Docs from the developers say to read any information displayed on the screen, and select any options to enable WSL 2 to continue.

I did not encounter any questions about enabling WSL2 in January 2022, and found the configuration enabled by default.

Start Docker Desktop from the start menu or however.

## Run Docker Commands in WSL

From the Linux CLI, you can now run docker commands. Container, image, and other information can be seen within Docker Desktop. From Linux:

```
# start a container
$ docker-compose up -d

# list available containers
$ docker ps

# exec onto the container
$ docker exec -it [container_name] bash
```

---

### References

Check WSL2 version - [https://docs.microsoft.com/en-us/windows/wsl/install#check-which-version-of-wsl-you-are-running](https://docs.microsoft.com/en-us/windows/wsl/install#check-which-version-of-wsl-you-are-running)

Docker Desktop Prerequisites - [https://docs.docker.com/desktop/windows/wsl/#prerequisites](https://docs.docker.com/desktop/windows/wsl/#prerequisites)

Getting Started with Docker Compose - [https://docs.docker.com/compose/gettingstarted/](https://docs.docker.com/compose/gettingstarted/)

WSL2 Conversion Time issue - [https://github.com/microsoft/WSL/issues/5344](https://github.com/microsoft/WSL/issues/5344)

WSL2 Conversion Memory Consumption Issue - [https://github.com/microsoft/WSL/issues/4669#issuecomment-559817819](https://github.com/microsoft/WSL/issues/4669#issuecomment-559817819)

Installing Docker Desktop - [https://docs.docker.com/desktop/windows/wsl/](https://docs.docker.com/desktop/windows/wsl/)

About WSL - [https://docs.microsoft.com/en-us/windows/wsl/about](https://docs.microsoft.com/en-us/windows/wsl/about)