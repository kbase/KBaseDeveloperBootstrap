# KBaseDeveloperBootstrap
This repo contains a tutorial intended to help a developer who is new to KBase learn the architecture, conventions and basic APIs and services well enough to become a productive developer on the platform.

# Table of Contents
1. [Introduction](#introduction)
1. [Architecture](#architecture)
1. [Core Services](#core-services)
1. [A Local Development Environment](#a-local-development-environment)
1. [KBase SDK](#kbase-sdk)
1. [An SDK App](#an-sdk-app)
1. [Modifying the SDK](#modifying-the-sdk)
1. [Workspace](#workspace)
1. [Narrative](#narrative)

## Introduction

This repository is intended to be a How To for new developers to KBase, that walks them through the
background information necessary to be a confident and productive contributor to the KBase project.
This intended to be a living document - if you have updates or extensions, please fork it and the submit
a pull request.

## Architecture

![KBase Architecture](images/KBaseSoftwareArchitecture.png)

## Core Services

wahwah wahwah wahwah

## A Local Development Environment

In order to develop code for KBase API services and the Narrative, the following needs to be installed on the development host:

* [git tools](https://git-scm.com/doc), [minimally the command line tools](https://git-scm.com/downloads)
* support for [Docker](https://www.docker.com/)
* [Java 1.7+](https://java.com/en/download/)
* [Python 2.7+](https://www.python.org/)
* [Python virtualenv](http://docs.python-guide.org/en/latest/dev/virtualenvs/)
* a reasonably current [NodeJS](https://nodejs.org/en/) installation
* [Bower](https://bower.io/)
* [Xcode](https://itunes.apple.com/us/app/xcode/id497799835?mt=12) ( for MacOS only )
* A suitable code editor [see our recommendations below](#integrated_development_environment)

We assume that the developer is familiar with git, and especially the common [github workflows](https://guides.github.com/introduction/flow/),
as the [KBase source code is all kept in Github](https://github.com/kbase).

### Docker

MacOS developers the recommended setup is to use [Docker for Mac](https://docs.docker.com/docker-for-mac/),
this bundles up all the dependencies for running a Docker environment into a single installer. We recommend using
the "stable" version.

Recent version of Windows also [support docker]( https://docs.docker.com/docker-for-windows/ )

[Most current releases of Linux Distros either include Docker or allow it to be installed](https://docs.docker.com/engine/installation/linux/) provided that you have administrative privileges.

These are the direct links for Redhat and Ubuntu:

https://docs.docker.com/engine/installation/linux/rhel/

https://docs.docker.com/engine/installation/linux/ubuntulinux/

### Integrated Development Environment

IDEs provide significant benefits for developers in terms of code checking and style enforcement. KBase
promotes the use of lightweight IDEs for developers who are not currently using an IDE, and for developers
who are already using an IDE, we recommend code validation tools and standard configurations.

[This document](https://github.com/kbase/project_guides/blob/master/RecommendedEditors.md) describes the recommended editors and configurations.

Python code contributed to KBase should conform to PEP8 guidelines and also pass the flake8+putty configuration described this
[tox.ini file](https://github.com/kbase/kb_sdk/blob/develop/tox.ini)

## KBase SDK

The KBase SDK is fairly well documented in the (README document in Github)[https://github.com/kbase/kb_sdk]
In addition, Mike Sneddon has a [detailed architecture slide deck](https://docs.google.com/presentation/d/18hxRC5enjA6kF-Ezn9xWdZ5xr2tg2c6LxBQXPxQ_5ik/edit?usp=sharing) that provides an overview of the SDK architecture.

## An SDK App

   The layout of a KBase SDK App is described in
[this document](https://github.com/kbase/kb_sdk/blob/master/doc/module_overview.md).
   A collection of SDK documentation references is [being maintained here](https://docs.google.com/document/d/1J6HJGtIoAY9yDI6N9xDyarH8vT7tCao2ZBzvVwLEOdw/edit#) as well.
## Modifying the SDK

made ya look!

## Workspace

The [workspace service](https://github.com/kbase/workspace_deluxe) is the main storage abstraction that most users will have to deal with when
working on narratives and data objects. The API is [documented here](https://ci.kbase.us/services/ws/docs/).

## Narrative

okay, that's all I had

