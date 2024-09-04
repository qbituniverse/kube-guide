---
title: IV. Adopt Mesh App and Service Architecture
description: Mobile, Web, IoT, Desktop built from independent apps and services
permalink: /adopt-mesh-app-and-service-architecture/
---

# IV. Adopt Mesh App and Service Architecture

## Mobile, Web, IoT, Desktop built from independent apps and services

Software doesn't mean `Desktop` exclusively anymore - these times are long gone. With an advent of mobile devices, swiftly followed by [Internet of Things (IoT)](https://en.wikipedia.org/wiki/Internet_of_things), software development had to extend its reach to cover all these new `runtime` devices.

Nowadays, the expectation that your solution is built form a single source code and then simply `rolled out` onto all these different devices - `all at once` that is...

## What is Mesh App and Service Architecture?

`Mesh App and Service Architecture (MASA)` - it's a term coined by [Gartner](https://www.gartner.com/en) and you can read more about it in this particular research paper: [MASA: How to Create an Agile Application Architecture With Apps, APIs and Services](https://www.gartner.com/en/documents/3980382).

> MASA stipulates that modern applications, `Mesh Applications`, are built from small distinctive `Apps` ([Software](https://en.wikipedia.org/wiki/Application_software)) which run on top of `Services` ([APIs](https://en.wikipedia.org/wiki/API)) which are in turn orchestrated at an `API Mediation Layer` ([API Management](https://en.wikipedia.org/wiki/API_management)).

OK, so that sounds like quite a lot is going on there, so let's unwrap `MASA` a little...

## MASA demystified

#### Inner APIs

Let's start with the lowest layer in our MASA architecture and we’ll call it `Inner APIs`. At that level you might have a number distinct APIs running on your infrastructure. And that could be internal on-premises IIS hosted APIs or more modern cloud hosted PaaS Apps, Functions or best of all Containerised Workloads on Kubernetes. It doesn’t matter how a particular piece of API is hosted, what is important is that:

> The Inner APIs are only accessible on your `internal` networking infrastructure and you have proper `authentication` and `authorisation` mechanisms in place to guard access to these APIs.

A single Inner API in your estate could be responsible for making payments, another for submitting orders and so on... From software development point of view this approach is also called [Microservice](https://en.wikipedia.org/wiki/Microservices) or [Loose coupled](https://en.wikipedia.org/wiki/Loose_coupling) service. It makes [development and testing](/design-container-ready-development) of such components easy and it also allows to fully automate software [builds and releases](/start-early-with-cicd-and-automation).

However, on their own, these APIs are not very useful other than `doing one thing very well`... these APIs need orchestration and we'll be looking into that next.

#### Outer APIs

Enter the world of API orchestration which we'll call `Outer APIs` in our MASA architecture. The purpose for Outer APIs is to chain together one or many Inner API calls to achieve an action or execute a process. Outer APIs are also hosted on your infrastructure, in fact, the same hosting and access principles apply as per Inner APIs. Only difference is `their function`:

> The Outer APIs are `the window` for your Inner APIs and allow you to compose or orchestrate a chain of Inner API calls. The `authentication` and `authorisation` mechanism at this level will depend on you `App` architecture and your identity solution.

An Outer API could be performing product sorting feature or submitting payments on your `App`. Whatever the requirement is, Outer APIs will implement it in the `API Mediation Layer`.

> This also brings another concept for your consideration - [API Lifecycle Management](/api-lifecycle-management-is-the-future).

From software development perspective things get little more complicated as you'll now deal with potentially multiple Inner APIs required to be accessible for development of a single Outer API feature. Again, [thinking containers](/start-thinking-containers) and [container development](/design-container-ready-development) helps a lot here.

From the [CICD perspective](/start-early-with-cicd-and-automation) situation is also similar to Inner APIs, however...

> You might want to start thinking [PlatformOps](/consider-platformops-for-delivering-software) when it comes to running and supporting `Mesh Apps` hosted on `Kubernetes` as these solutions will `depend heavily` on [API Lifecycle Management and API Gateways](/api-lifecycle-management-is-the-future) components.

#### Mesh Applications

Finally, we got to the top of our MASA architecture which we'll just call `Mesh Applications` or `Apps` for short. The applications are [your products](/embrace-product-oriented-delivery-model), either internal (Intranet) or external (Internet) facing. Often the Apps will be in the form of [Responsive websites](https://en.wikipedia.org/wiki/Responsive_web_design) capable of running on many screen sizes and devices. You might also have Apps written for [IoT](https://en.wikipedia.org/wiki/Internet_of_things) devices such as [wearable technology](https://en.wikipedia.org/wiki/Wearable_technology).

> The Apps are in effect `dumb frontends` which need to be able to `execute calls over HTTP protocol` to consume Outer APIs. Outer APIs in effect provide the Apps with all the logic required for them to function. Or to put it in other words, Outer APIs are the `heart of your product`.

Therefore, you can see from the above, the App just needs to look pretty, and it needs to understand API HTTP Request-Response mechanisms. You can also architect your Mesh Application from multiple smaller Apps to provide your users with what it might seem like an `end-to-end desktop product` - which in effect is merged from multi-App components.

Good example could be your hypothetical `Online Store Mesh Application` consisting of one App for user login, one App for products and shopping, one App for checkout process and one App for user dashboard. What’s great about this is that your user can start their shopping journey on tablet, then 2 hours later come back to your Mesh Application and finish off the purchase on Desktop PC or a smart watch. Quite neat, hey?

From both development and infrastructure perspective the Apps are like the APIs. Apps are [developed](/design-container-ready-development) and [deployed](/start-early-with-cicd-and-automation) as a single component.

> You need to consider `Networking, Routing and Authorisation` at this stage so that your `Apps`, and `Outer APIs` for that matter, are accessible to your users - very important for Internet and IoT facing implementations.

### [<< Previous](/embed-least-privileged-approach) | [Next >>](/start-early-with-cicd-and-automation)