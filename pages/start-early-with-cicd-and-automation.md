---
title: V. Start early with CICD and Automation
description: Continuous Integration for code builds and Continuous Delivery for software releases
permalink: /start-early-with-cicd-and-automation/
---

# V. Start early with CICD and Automation

## Continuous Integration for code builds and Continuous Delivery for software releases

Do you remember the times when software used to be compiled on developers' machines and then released, or in other words copied, to the host machine? Sounds crazy now, but that's how release process used to look like in many organisations.

If you are still doing this then [start thinking containers](/start-thinking-containers) as soon as you can, and keep reading this article to learn how you can add robust [CICD and Automation](https://en.wikipedia.org/wiki/CI/CD) to your `code builds and software releases`. 

## Continuous Integration for Docker Image Builds

This is the [Continuous Integration (CI)](https://en.wikipedia.org/wiki/Continuous_integration) stage where changes to your code base are made on a frequent, `continuous`, basis and merged, `integrated`, into the main code branch. From that point a version of your software is built and a potential candidate for release is created.

This process will apply to every single [deployable containerised component](/start-thinking-containers) of your [Kubernetes solution](/docker-kubernetes-and-helm). For instance this could be a build for a single `API` (Inner/Outer) or `App` (Mesh Application) component of your [Mesh App and Service Architecture](/adopt-mesh-app-and-service-architecture).

At a high level you'll need to automate the following `Build Tasks` using your chosen [DevOps](https://en.wikipedia.org/wiki/DevOps) tool:

> 1. Run code build and unit tests as part of `Pull Request`
> 2. Assign unique `Version` number to your Build
> 3. Build `Docker Image` from Dockerfile and Tag it with Version
> 4. Push Image to `Development Container Registry`

At stage 4 above we assume you have one Container Registry per environment: Development, Staging and Production Images. An alternative is to have one single Container Registry for all environments, which makes the infrastructure maintenance easier but security wise less secure. 

## Continuous Delivery for Kubernetes Deployments

For the [Continuous Delivery(CD)](https://en.wikipedia.org/wiki/Continuous_delivery) stage all we are concerned with is to frequently, `continuously`, pushing, `delivering`, a particular build to our environments for testing and finally Production release. We already have a release candidate which in our case is the `Image` we've built, Tagged with Version number and pushed to Development Container Registry.

Similar to the `CD` stage, this procedure applies to every single [deployable containerised component](/start-thinking-containers) of your [Kubernetes solution](/docker-kubernetes-and-helm) - API, App and so on.

At a high level you'll need to automate the following `Release Tasks` using your chosen [DevOps](https://en.wikipedia.org/wiki/DevOps) tool:

> 1. Package `Helm Chart` for release referencing Image with Version from `Development Container Registry`
> 2. Release the `Helm Chart Package` to Development environment
> 3. `Promote` Docker Image from Development Container Registry to `Staging Container Registry`
> 4. Package Helm Chart for release referencing Image with Version from `Staging Container Registry`
> 5. Release the Helm Chart Package to `Staging` environment
> 6. Promote Docker Image from Staging Container Registry to `Production Container Registry`
> 7. Package Helm Chart for release referencing Image with Version from `Production Container Registry`
> 8. Release the Helm Chart Package to `Production` environment

The example above assumes one Container Registry per environment: Development, Staging and Production Images. We've also bypassed Approval gates here as probably not every single release will always get delivered straight through Development => Staging => Production.

### [<< Previous](/adopt-mesh-app-and-service-architecture) | [Next >>](/invest-efforts-into-logging-and-monitoring)