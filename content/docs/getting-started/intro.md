---
title: "Intro"
date: 2020-02-14T05:09:45-06:00
draft: false
---
# Getting Started: Introduction

This will walk you through setting up the system with some basic information on the components.  

## Set-up

### Spinner
The spinner is the component that tells the volunteer machines what containers to spin up. To start the system, one spinner needs to be running.  

The Spinner can be run in two ways.  
{{< columns >}}
#### Docker Image
Currently there is no publicly available Docker image. When there is, the documentation will change to reflect that.

<--->

#### Golang

Clone the [Spinner repository](https://github.com/armadanet/spinner) and from the build directory execute `make run`

This will create a docker image called nebula-spinner and run it with port 5912 open.   
The port can be configured in the Makefile.

{{< /columns >}}

### Captain
Once a Spinner is in place, Captains can be added. A Captain controls how the system runs on the volunteer node itself. Each volunteer node requires a single Captain to be running at all times.  

The Captain can be run in a similar two ways.
{{< columns >}}
#### Docker Image
Currently there is no publicly available Docker image. When there is, the documentation will change to reflect that.

<--->

#### Golang

Clone the [Captain repository](https://github.com/armadanet/captain).  
Change the URL in `build/Makefile` to the url of Spinner. An example is shown below.

From the build directory, executing `make run` will then create a docker image called nebula-captain and run it connected to the Docker socket. It will use the Spinner URL given to it.  

{{< /columns >}}

{{< expand "Changing the Spinner URL Example" "..." >}}
If the Spinner is running on port 5912 of IP address 8.8.8.8, then the line in `build/Makefile` of the Captain should read `URL := wss://8.8.8.8:5912/join`
{{< /expand >}}

Further captains can be added on other machines the same way.  
