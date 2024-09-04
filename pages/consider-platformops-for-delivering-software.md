---
title: X. Consider PlatformOps for delivering software
description: Provision infrastructure and release software fast and at scale
permalink: /consider-platformops-for-delivering-software/
---

# X. Consider PlatformOps for delivering software

## Provision infrastructure and release software fast and at scale

We'll start off with the traditional `us versus them` scenario which I'm sure most of us have come across. The `us` is software development team, the `them` is the infrastructure, or operations, or security, and so on, teams. You get the idea, right?

In the traditional, [project-oriented delivery model](https://en.wikipedia.org/wiki/Project_delivery_method), software development, `us`, would write and test the code and then push the package towards the next team, `them`, in line and forget about it. Kind of like `hot potato` scenario.

> This model introduces `reliance` on other teams providing the infrastructure. It also siloes each project regarding release and automation of their software delivery which tends to be done in a `different manner` or even using different tool sets.

## Start doing DevOps right

Every journey starts with a small step in the right direction. [DevOps](https://en.wikipedia.org/wiki/DevOps) adoption is normally the first step many organisations will take when it comes to running [CICD and automation](/start-early-with-cicd-and-automation). `DevOps` is also the right thing to do regardless if your aspirations are just running seamless CICD pipelines or maybe your desire is to venture into `PlatformOps` as you mature your processes.

When it comes to [containerised apps](/start-thinking-containers) DevOps is the must have. It's very likely that you'll end up building and releasing code daily and the last thing you'd want is to manually oversee this process or have a human somewhere in the mix slowing it all down.

> Look into CICD tools such as [Azure DevOps](https://azure.microsoft.com/en-gb/services/devops/), [Jenkins](https://www.jenkins.io/) or [Ansible](https://www.ansible.com/).

If you've done `DevOps` right you have probably found yourself running multiple projects or [delivering products](/embrace-product-oriented-delivery-model) in this CICD automated way.

However, the more software you develop and deliver the more you'll start thinking in terms of `scale and agility`, right? 

## It's time to morph DevOps into PlatformOps

In the `PlatformOps` model the `us` and the `them` I mentioned earlier are working together, or in other words `collaborate`. You don't want pockets of siloed CICD or infra done one way here and another CICD or infra done in a different way there and so on... Result of that?

> Sooner or later you'll end up with what is called [Shadow IT](https://en.wikipedia.org/wiki/Shadow_IT).

Whereby the development community accelerates with new tech, [often seen with cloud adoption](/cloud-first-strategy-is-the-theme-of-the-day), at the detriment to the rest of the organisation - mainly resulting in security breaches and unnecessary costs.

Collaboration in the `PlatformOps` model will often start at developer and operations teams’ level. This is probably the earliest opportunity to shut the `shadow IT` activities and `bridge` automation process under one `PlatformOps umbrella`.

As you mature your PlatformOps expertise, you'll be able to add `security`, `governance`, `self-service` capacity and promote `standards` all across your technology stack.

> The following Gartner research is an excellent explanation of [Using Platform Ops to Scale and Accelerate DevOps Adoption](https://www.gartner.com/document/3988253?ref=solrAll&refval=271967599).

## Benefits of PlatforOps

Let's now briefly summarise the `benefits` PlatformOps can bring to your organisation at different levels:

> 1. `Development`
>   - Agility
>   - Freedom to provision infrastructure
>   - As-code approach to all aspects of the product
> 2. `Operations`
>   - Control the cost
>   - Maintain predefined set of resources
>   - As-code approach to infrastructure
> 3. `Security`
>   - Early insights into workload vulnerabilities
>   - [RBAC](https://en.wikipedia.org/wiki/Role-based_access_control) and access controls
> 4. `Governance`
>   - Set and maintain standards across identity, cost, and resource usage
> 5. `Product`
>   - Ability to deliver features on time and at low cost

### [<< Previous](/api-lifecycle-management-is-the-future) | [Next >>](/embrace-product-oriented-delivery-model)