---
title: II. Start thinking Containers
description: If it cannot be containerised then change approach to make it possible
permalink: /start-thinking-containers/
---

# II. Start thinking Containers

## If it cannot be containerised then change approach to make it possible

So you made your mind up, you like the benefits containers bring, such as [workload isolation and packaging](/docker-kubernetes-and-helm) and [focus on security](/embed-least-privileged-approach). You also like the aspect of being able to architect your solutions from [multiple smaller services](/adopt-mesh-app-and-service-architecture) and perform [rapid releases](/start-early-with-cicd-and-automation) to `Kubernetes`.

## Where to start with containerisation?

Any new piece of software should by default enter containerised format. `Lift and shift` of existing, non-containerised, software is also possible - just keep reading...

The chances are that whatever you are trying to containerise has already been containerised. Simply search the official [DockerHub](https://hub.docker.com/) for the piece of software you are after. [Docker's layered architecture](https://docs.docker.com/storage/storagedriver/#images-and-layers) allows you to build on top of other `Base Images`. In other words, extend Base Images to fit your requirement, which is also referred to as [multi-stage builds](https://docs.docker.com/develop/develop-images/multistage-build).

> Using `Base Images` speeds up your development process as you don't have to `reinvent the wheel` allowing you to focus on your requirement and implementation.

## What is containerised?

Pretty much all of the most common programming languages and frameworks already offer `Build and Runtime Images`: [.NET Core](https://hub.docker.com/_/microsoft-dotnet-core), [.NET](https://hub.docker.com/_/microsoft-dotnet), [Node](https://hub.docker.com/_/node), [OpenJDK](https://hub.docker.com/_/openjdk), [Python](https://hub.docker.com/_/python), [Go](https://hub.docker.com/_/golang), [Ruby](https://hub.docker.com/_/ruby), [PHP](https://hub.docker.com/_/php).

You'll also find base `Operating Systems (OS)` in containerised format: [Alpine Linux](https://hub.docker.com/_/alpine), [Ubuntu](https://hub.docker.com/_/ubuntu), [Debian](https://hub.docker.com/_/debian), [Windows Server Core](https://hub.docker.com/_/microsoft-windows-servercore), [Windows Nano Server](https://hub.docker.com/_/microsoft-windows-nanoserver), [Windows IoT Core](https://hub.docker.com/_/microsoft-windows-iotcore).

And of course `Databases`: [Microsoft SQL Server](https://hub.docker.com/_/microsoft-mssql-server), [Oracle Database](https://hub.docker.com/_/oracle-database-enterprise-edition), [MongoDB](https://hub.docker.com/_/mongo), [PostgreSQL](https://hub.docker.com/_/postgres), [MySQL](https://hub.docker.com/_/mysql).

## What if I have an unusual requirement?

Then you can build on top of an existing Base Image and add your code or dependencies that are required for your piece of software.

What's important to stress is that when I say `Think Containers` I mean:

> Treat your software as a bundle: `OS + Dependencies + Source Code`.

Therefore, you `encapsulate`, at the minimum, core OS processes (IIS, nginx, port opening, write permission on file system, networking etc.), dependencies (DLLs, JARs, Gems etc) and source code (C#, Java, Python etc.) required for your software to perform its function in `total isolation`.

#### Proprietary DLLs

For example, if you have .NET Core API which has dependency on a `proprietary DLL` then simply use [ADD](https://docs.docker.com/engine/reference/builder/#add) or [COPY](https://docs.docker.com/engine/reference/builder/#copy) statement in your Dockerfile to include it into the Image. From that point the dependency is there in predefined folder as expected by your source code. 

#### Proprietary executables

Alternatively, you might need to run `proprietary executable` while you build Image for your application or run an installation of a framework - in either case you simply add [RUN](https://docs.docker.com/engine/reference/builder/#run) statement and point it to the executable.

### [<< Previous](/docker-kubernetes-and-helm) | [Next >>](/embed-least-privileged-approach)