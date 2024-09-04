---
title: VIII. Design container-ready development
description: Build in container - Test in container - Run in container
permalink: /design-container-ready-development/
---

# VIII. Design container-ready development

## Build in container - Test in container - Run in container

Since you got so far to reach this chapter the chances are that you already [think Containers](/start-thinking-containers) - which is brilliant! However, let's re-wind a little first and look back how software development `used to look like`, or indeed, still looks on non-containerised environments.

Depending on your [Solution stack](https://en.wikipedia.org/wiki/Solution_stack) you'd be running [.NET](https://dotnet.microsoft.com/), [Python](https://www.python.org/) or [Java](https://www.java.com/en/) installations - just to name the few biggest ones. Possibly you'd also run multiple versions of these frameworks alongside each other.

> You know - the typical `this app needs 1.1.5 framework, that app needs 1.3.2 framework` situation...

This is very common, and once in a while such setup causes what we normally define a [Dependency hell](https://en.wikipedia.org/wiki/Dependency_hell) - where your code just stops working because of framework version conflicts.

There's also much, much more serious problem with such setup, and that is the following situation.

> `But it works on my machine`... 

Sounds familiar? We've all seen it; you deploy software to a host and - bang - it doesn't work!

## The Container environment

All you need to do to have a modern, container ready environment is this:

> 1. `Clean workstation`: no frameworks, no rubbish, no magic installations, and no dependencies
> 2. `Any OS`: Windows, Linux, Mac
> 3. `Docker installed`: yes, all you need is that small Docker engine running on your OS

And do you know what's best in all this?

> You can now build software on Mac targeting Windows host or work on Windows machine writing software for Linux

With the setup above your software will now make use of `Dockerfile and Docker Images` bringing the benefits of [OS, dependencies and code encapsulation](/start-thinking-containers).

You will realise stability all across your `environment releases` with [fully automated CICD pipelines](/start-early-with-cicd-and-automation). And, finally you will embed `container native security` into your workloads with adoption of the [least privileged](/embed-least-privileged-approach) concept.

## The Container way of working

The chances are that once you have your Container environment setup you will probably start `architecting` your software with [Microservices and Mesh](/adopt-mesh-app-and-service-architecture) in mind. We already know that microservice architectures introduce agility, fast release patterns and allow re-usability of components. However, microservices also bring few more concepts we need to consider from the `dev-test` perspective.

How about `developing and testing` container native solutions that are made up of more than one container? Normally you'd run instances of these components compiled from source code on your localhost, right?

> The answer is, of course, run these in containers.

#### Docker Compose

[Docker Compose](https://docs.docker.com/compose/) allows you to define and run multi-container applications. All you need to do with Docker Compose is to create a [YAML Compose File](https://docs.docker.com/compose/compose-file/) declaration for your application stack.

You could then either `build and run` local containers or reference images from your `Container Registry`, which normally would be your Development versions. Execute `docker compose up` and the infrastructure will be `up and running locally` for you to develop against.

#### Kubernetes

Docker installation offers you an option to run local [Kubernetes](https://kubernetes.io/) cluster, simply check a box in Docker settings to start up Kubernetes. Alternatively, you can also install [Minikube](https://minikube.sigs.k8s.io) which is a small instance of Kubernetes running locally on your device.

Once you have `Kubernetes` running locally, you'll then be able to execute [YAML Declarations](https://kubernetes.io/docs/concepts/overview/working-with-objects/kubernetes-objects/) on your local `k8s` instance. These could be either single `Pod` declarations, `Services` or `Deployments`. You can even deploy [Helm Charts](https://helm.sh/) onto your k8s to  re-create an `entire application stack` to develop against.

### [<< Previous](/cloud-first-strategy-is-the-theme-of-the-day) | [Next >>](/api-lifecycle-management-is-the-future)
