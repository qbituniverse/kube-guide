---
title: I. Docker, Kubernetes and Helm
description: The Three Musketeers of the modern software era
permalink: /docker-kubernetes-and-helm/
---

# I. Docker, Kubernetes and Helm

## The Three Musketeers of the modern software era

[Docker](https://www.docker.com/), [Kubernetes](https://kubernetes.io/) and [Helm](https://helm.sh/) complement each other very well. Put together, these technologies, or concepts, make an extremely powerful mix. My journey into `containerisation` started with Docker, followed by container orchestrator, in this case Kubernetes and eventually I added Helm to enable the complete solution packaging experience.

## What is Docker?

Docker has taken both software and infrastructure virtualisation to the next level where the concepts of [Virtual Machines](https://en.wikipedia.org/wiki/Virtual_machine) and [Software Runtime](https://en.wikipedia.org/wiki/Runtime_system) got merged into a single [Dockerfile](https://docs.docker.com/engine/reference/builder/) declaration. The `Dockerfile` acts as documentation for your software. It is a source-controlled file, which in essence prevents configuration drift, and it allows you to treat your software as a single, deployable, `self-contained` package.

> The container format standard is now governed by the [Open Container Initiative (OCI)](https://opencontainers.org/).

`Docker` allows you to define your software runtime, dependencies and binaries that need to execute for your software to function properly. This is done using the Dockerfile as a mechanism to build an [Image](https://docs.docker.com/engine/reference/commandline/image/) - a snapshot of your application at a time of the build. Docker also introduces another very important concept called [Least Privileged](/embed-least-privileged-approach). In essence making your software `secure` and self-contained, or `isolated`, from any external influences.

Once you have your `Image` built, all you have to do with it is to run it on what is called [Container Runtime](https://www.docker.com/products/container-runtime) at which point your software becomes a running [Container](https://www.docker.com/resources/what-container).

Finally, you can store your Images in `Container Registries`, such as [Azure ACR](https://azure.microsoft.com/en-us/services/container-registry/), [Google Container Registry](https://cloud.google.com/container-registry), [AWS ECR](https://aws.amazon.com/ecr/) or [IBM Cloud Container Registry](https://www.ibm.com/uk-en/cloud/container-registry). These effectively become your software catalogues from which you pull Images down for deployment at which point they become `Containers`.

## What is Kubernetes?

Software solutions are rarely as simple as single container deployments. Often you will architect your solutions from multiple smaller components, referred as [Microservices](https://en.wikipedia.org/wiki/Microservices) or [APIs](https://en.wikipedia.org/wiki/API). Concepts such as [Mesh App and Service Architecture (MASA)](/adopt-mesh-app-and-service-architecture) are often considered in such scenarios. Therefore, to pull these multi-app, multi-service deployments off you need something more than just Docker, you need `container orchestrator`, and luckily there's one called Kubernetes (k8s)...

`Kubernetes` allows you to automate, scale and manage your containerised applications. It's a `production grade` system which you can run [in development](/design-container-ready-development), on-premises or in the cloud with [Azure AKS](https://azure.microsoft.com/en-gb/services/kubernetes-service), [Google GKE](https://cloud.google.com/kubernetes-engine), [AWS EKS](https://aws.amazon.com/eks) or [IBM Managed Kubernetes Service](https://www.ibm.com/uk-en/cloud/container-service).

> Kubernetes is an open-source system that's been [developed and used at Google](https://queue.acm.org/detail.cfm?id=2898444).

[Kubernetes objects](https://kubernetes.io/docs/concepts/overview/working-with-objects/kubernetes-objects/) describe your containerised application's `desired state`, such as number of instances, resource allocations and networking. These are defined in [YAML Ain't Markup Language (YAML)](https://yaml.org/) and are source controlled. This allows you to always maintain the desired state of your application stack and delegate to Kubernetes to ensure the actual state of your application meets the desired state as defined in YAML.

Finally, any changes to your application are then made to these YAML declarations and pushed automatically to your Kubernetes host via [CICD pipelines](/start-early-with-cicd-and-automation).

## What is Helm?

Simple applications could possibly get away with just deploying YAML declarations directly onto Kubernetes plane. However, more `complex systems`, or multi-app solutions, require much more robust approach. Enter Helm - a package manager for Kubernetes. 

`Helm` allows you to package all your Kubernetes YAML declarations into a single, deployable, configuration driven package. You define your application as [Helm Chart](https://helm.sh/docs/chart_template_guide/getting_started/) and that's where your configuration and YAML declaration go to. You can even reference other `Helm Chart` here so that you build what's called multi-chart or [Umbrella Chart](https://helm.sh/docs/howto/charts_tips_and_tricks/). 

> You can store your Helm Charts in `Container Registries`, good example is [Azure ACR](https://azure.microsoft.com/en-us/services/container-registry/).

These effectively become your software catalogues from which you pull Helm Charts down for deployment into Kubernetes via [CICD pipelines](/start-early-with-cicd-and-automation) at which point these become running, containerised, applications.

### [Next >>](/start-thinking-containers)