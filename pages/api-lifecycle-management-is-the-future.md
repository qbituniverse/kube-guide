---
title: IX. API Lifecycle Management is the future
description: APIs are and always will be at the heart of any solution
permalink: /api-lifecycle-management-is-the-future/
---

# IX. API Lifecycle Management is the future

## APIs are and always will be at the heart of any solution

World runs on [APIs](https://en.wikipedia.org/wiki/API) - Apps on smart phones, social media, your doorbell, self-driving cars... the list is endless and it's growing.

> `APIs are the veins` - `API Management is the heart` - `API Lifecycle is a process`

What we are concerned with in the context of [MASA Mesh Apps and Services](/adopt-mesh-app-and-service-architecture) is the notion of `Web APIs` or `Microservices`. Web APIs are delivered over [Hypertext Transfer Protocol (HTTP)](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) protocol and normally implement either [Extensible Markup Language (XML)](https://en.wikipedia.org/wiki/XML) or [JavaScript Object Notation (JSON)](https://en.wikipedia.org/wiki/JSON) messaging format.

`HTTP, XML/JSON` are set standards that software development community adopted with `Web APIs` implementations. This promotes consistency, agility, and re-usability. Advent of [Docker Containers and Kubernetes](/docker-kubernetes-and-helm) has accelerated adoption of Microservices and Mesh Architectures ([MASA](/adopt-mesh-app-and-service-architecture)) and that in turn made [API Management (APIM)](https://en.wikipedia.org/wiki/API_management) product a central component in any modern MASA solution.

`API Management (APIM)` is a facade, a central location to discover and consume APIs within your organisation or amongst your consumers. It plays a `fundamental` role in an API driven architecture not just from routing HTTP calls to underlying services, but also `enhances the API experience` with features such as `Policies` and `Gateways`.

> Most popular APIM cloud-based products: [Azure APIM](https://azure.microsoft.com/en-gb/services/api-management/), [Google Apigee](https://cloud.google.com/apigee), [AWS APIM](https://aws.amazon.com/api-gateway/api-management/), [IBM API Connect](https://www.ibm.com/uk-en/cloud/api-connect).

## Enter API Lifecycle

We got to the stage where we have APIs and possibly even APIM in place. It might seem that we've got all we need to get the API economy going... However, ...

> How do you get from an `initial API idea` all the way to `delivering the API` to your consumers?

Well, this is role of `ALF` or `API Lifecycle Framework` which consists of three key stages as outlined below. 

### Building APIs

At this point it's all about the [product team](/embrace-product-oriented-delivery-model) working on the API. The team will design it and deliver an end-to-end API package containing the `API spec`, `API documentation` and the actual `deployed API`.

#### Design

This is probably the most important phase in any API lifecycle. You'll be designing the API here or at best modifying or adding new endpoint features on an existing API. The API contract, or spec, should follow a `standard` for example [OpenAPI Specification](https://swagger.io/specification/), [RAML](https://raml.org/) or [GraphQL](https://graphql.org/).

> The key element here is `collaboration`, and that involves developers, data teams, business, analysts and test working together on the `API Spec`.

#### Develop

Now we have the `API Spec` defined and agreed upon amongst the API stakeholders. The spec then makes its way to source control, such as [GitHub](https://github.com/), and development on the API commences. Code build and quality check in your [CICD Pipelines](/start-early-with-cicd-and-automation) should test if the code implementation `adheres the API Spec`. If not, API should not be allowed to move beyond DEV stage.

> Development will follow the `API Spec` so that code is written to `programmatically implement` the requirement.

#### Document

Another benefit of adopting `API Spec` is the fact that these specification files can serve as `API Documentation`. The outcome of the design stage should be providing well defined and complete API specification which will serve as feature for development as well as documentation for the API consumers.

> Start with the premise that the `design phase defines API's structure and behaviour`, and nothing else beyond that can change that.

#### Catalogue

Whichever API specification standard you decide to follow, it'll enable you to feed these spec files into API collaboration tools such as [Postman](https://www.postman.com/). The process of feeding `API Specs` can be automated with standard [CICD Pipelines](/start-early-with-cicd-and-automation) every time API definition changes or perhaps when API feature is developed. For example you [can convert API Specs to Postman collections](https://blog.postman.com/converting-openapi-specs-to-postman-collections/) with use of converters.

This will ensure that what is in the `API catalogue` is always an up-to-date representation of the API either available to consume as a `real implementation` or `mock`.

> Enable everyone in your organisation to `discover`, explore and use your APIs `in one place`.

#### Test

At this stage you have the API coded according to the `API Spec`. We'll now consider testing the API to ensure that it meets the criteria as set out by the API collaborators group. Probably this is a good opportunity to introduce a concept of `Contract Testing` which can be achieved with adoption of tools such as [Pact](https://docs.pact.io/) or [Dredd](https://dredd.org/en/latest/).

> Close the `API Design loop` by making sure the API has been developed according to the `API Spec`.

### Hosting APIs

At this point we'll revisit `API Management (APIM)` as this is where we move our API `beyond development` into general consumption and implementation in your product. You'll now need to consider the `where` - the API is deployed, and `how` - the API is accessed.

#### Policies

API Policies change the behaviours of your APIs, this could be message `transformation` from XML to JSON, or `validating` JWT tokens. Policies can also apply call limits, `quotas`, IP Address whitelisting, `caching`, setting headers and so on...

What is important to remember at this stage is that policies don't require code changes to the underlying service exposed via API Management.

> Therefore, you define API policies once, at the APIM level, and link these to relevant APIs.

#### Gateways

One level down from APIM is the API Gateway. Gateways are very powerful concept allowing you to `group APIs` into easily accessible, `low latency` buckets which are deployed close to the underlying services. For example, you might have group of services hosted on k8s cluster in a single region and expose these through a single gateway.

One of the key considerations designing APIs is latency. You'd host the gateway close to your services, hence `reducing latency` to single digit milliseconds. The key features of such design are:

> 1. Gateway is hosted close to the underlying services ensuring `low latency`
> 2. Gateway is linked to APIM `inheriting policies` as result
> 3. Consumers are `accessing APIs directly via the gateway` rather than via APIM
    - Benefiting from low-latency of the gateway & policies inheritance from APIM

### Observing APIs

At this point your APIs are, hopefully, running and serving `Production` applications or `paying clients`. However, you need to know whether the APIs are used as intended, are there any issues, bottlenecks, or abuse of the API?

#### Monitoring

Here we are simply looking at the API from `performance` and `troubleshooting` point of view. This requires your product development team to [invest time and efforts into efficient logging and monitoring](/invest-efforts-into-logging-and-monitoring) standards and tools. Once you API `log` and `trace` data is sent to your central monitoring system you'll then be able to analyse it, set reports or alerts up as well as `proactively` detect anomalies with your APIs.

#### Dependencies

The nature of [distributed systems](/adopt-mesh-app-and-service-architecture) built from a mesh of small components interconnected with each other is that you introduce `numerous dependencies` between these components. When it comes to releasing new versions of your APIs or decommissioning old ones it's important that none of these dependencies is broken. There are possibly two ways of addressing the API Observability:

> 1. Leverage your `monitoring solution` which might offer API-to-API mapping out of the box based on API metrics and logs
> 2. Describe API-to-API mapping in `source code` where dependencies are defined in code: [Pivio](http://pivio.io/) or [Stackify](https://stackify.com/application-dependency-mapping-performance/)

### [<< Previous](/design-container-ready-development) | [Next >>](/consider-platformops-for-delivering-software)