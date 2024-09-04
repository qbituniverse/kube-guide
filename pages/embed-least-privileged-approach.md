---
title: III. Embed Least Privileged approach
description: Only provide enough privileges that are necessary
permalink: /embed-least-privileged-approach/
---

# III. Embed Least Privileged approach

## Only provide enough privileges that are necessary

Before Docker arrived we used to run software on [bare-metal servers](https://en.wikipedia.org/wiki/Bare-metal_server) or [virtual machines](https://en.wikipedia.org/wiki/Virtual_machine) at best. Your host [Operating Systems (OS)](https://en.wikipedia.org/wiki/Operating_system) had to be `carefully prepared` with all the dependencies pre-installed. The chances of running multiple applications on the same host, even built on similar stack, were slim due to `dependency clashes` - also known as [Dependency Hell](https://en.wikipedia.org/wiki/Dependency_hell).

What's worst these applications often had to operate in an `elevated administrator privilege` context due to its requirements to write to file system or having to open up communication channel on a specific port.

## How containers solve the elevated privileges problem?

You design your application [with containers in mind](/start-thinking-containers) by virtue of adopting Dockerfile declaration for your application. [From the previous chapter](/start-thinking-containers) we know that containerised applications build on top of `Base Images`, such as Core OS ([Windows Server Core](https://hub.docker.com/_/microsoft-windows-servercore) or [Alpine Linux](https://hub.docker.com/_/alpine)) or a Framework ([.NET Core](https://hub.docker.com/_/microsoft-dotnet-core) or [Node](https://hub.docker.com/_/node)) - which in turn are built on core OS...

The `Least Privileged` restrictions can be applied in two ways: 
> 1. Inside `Dockerfile` composition stage for Image Builds
> 2. Inside `YAML Declaration` for Kubernetes Deployments.

> Note: useful reference points on [Docker Security](https://docs.docker.com/engine/security/) and [Resource Constraints](https://docs.docker.com/config/containers/resource_constraints/).

## What are my options for the Least Privileged restrictions?

#### Run Container as unprivileged user

This is simply saying `don't run this workload as Administrator`. As result, whoever manages to enter your workload will not be able to cause too much damage other than whatever is in the remit of the `unprivileged user` running it.

#### Prevent privilege escalation

In addition to the above, you can also explicitly state that `privilege escalation` is to be completely banned inside of the container workload.

#### Add or remove Container capabilities

As with any OS, Docker Container is no exception - it has several processes running inside. These are defined as `capabilities` and range from opening ports, firewalls, file system commands or networking. If your container workload doesn't need any of these OS capabilities, you should simply `disable` them before these get exploited.

#### Limit computer resources available to Container

Only assign [CPU](https://en.wikipedia.org/wiki/Central_processing_unit) and [RAM](https://en.wikipedia.org/wiki/Random-access_memory) levels that are required for the application to function properly - and nothing more. As result, you also prevent your host from [Denial-of-service attack](https://en.wikipedia.org/wiki/Denial-of-service_attack) since both `CPU` and `RAM` are capped to a fixed ceiling.

#### Read-only file system

If your container workload is stateless by nature and `doesn't need to modify its file system`, then simply turn off the ability to write to it.

### [<< Previous](/start-thinking-containers) | [Next >>](/adopt-mesh-app-and-service-architecture)