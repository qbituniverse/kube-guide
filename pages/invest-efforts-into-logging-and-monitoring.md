---
title: VI. Invest efforts into Logging and Monitoring
description: Traceability and visibility are must-haves in the era of distributed software
permalink: /invest-efforts-into-logging-and-monitoring/
---

# VI. Invest efforts into Logging and Monitoring

## Traceability and visibility are must-haves in the era of distributed software

Back in the days when we used to run [Monolithic applications](https://en.wikipedia.org/wiki/Monolithic_application) more often than not `logs` would be written to `file system` on the host next to the monolith. More advanced implementations might have an ingestion system built to move these logs into a central logging repository where application support could access them easily. Similar pattern would apply to `monitoring` around the monolith with probes connected to a specific page or endpoint listening to these URLs and detecting any non-success responses back.

In the age of modern [Mesh applications](/adopt-mesh-app-and-service-architecture) the practices described above are not feasible mainly due to the fact that software is no longer hosted on physical machines - so for starters no easy access to its file system. Often, modern software is hosted and running on `virtual, serverless, stateless instances` with no or little access to the file system - especially true with [distributed and containerised software](/start-thinking-containers).

## Design your Centralised Logging Strategy

#### Logging Platform

Let's start with the logging platform, which by its nature must be `centralised`, readily available for your apps to send logs to and easily accessible for your support team to browse and query the logs. When it comes to containerised applications you have two main choices here:

> 1. Adopt `container native` logging: [ELK Stack](https://www.elastic.co/what-is/elk-stack)
> 2. Adopt `cloud native` logging: [Azure Application Insights](https://docs.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview), [GCP Cloud Logging](https://cloud.google.com/products/operations), [AWS Centralised Logging](https://aws.amazon.com/solutions/implementations/centralized-logging/), [IBM Log Analysis](https://cloud.ibm.com/docs/Log-Analysis-with-LogDNA?topic=Log-Analysis-with-LogDNA-getting-started)

Your logging platform choice will mainly depend on your `cloud lock-in` situation, appetite for pure-containerised solution, cost, and skills.

Whichever option you go with you need to ensure that you can: 
> 1. `View` all logs in a consistent and predictable format
> 2. `Query` and inspect logs easily – per workload
> 3. `Join` log entries together from multiple microservices – multiple workloads
>   - Situation where many different API calls are made as part of a bigger orchestrated process

#### Writing Logs

It's incredibly easy these days to write logs from your source code. There's a number of external packages that will take the headache away and simply allow you to implement log objects and write logs with just `one line of code`. You need to consider few things when sending logs from your workloads:

> 1. `Networking`: is your app able to reach the logging platform?
>     - Important in hybrid and multi-cloud architectures
> 2. `Authorisation`: is your app allowed to send logs to it?
>     - This is normally achieved with client keys
> 3. `Standard Log Format`: do all your apps implement the same message formats, event codes, etc?
>     - You can enforce it by adopting a single package or repository in all your apps

## Design your Centralised Monitoring Strategy

#### Monitoring Platform

As with logs, monitoring platform needs to be in `centralised` location where all apps can be monitored in one place. This will allow your support team to easily see the overall state of your software at any time. Regarding containerised applications, there are generally two choices:

> 1. Adopt `container native` monitoring: [Prometheus](https://prometheus.io/) and [Grafana](https://grafana.com/)
> 2. Adopt `cloud native` monitoring: [Azure Monitor](https://azure.microsoft.com/en-gb/services/monitor/), [GCP Monitoring](https://cloud.google.com/monitoring), [AWS CloudWatch](https://aws.amazon.com/cloudwatch/), [IBM Cloud Monitoring](https://cloud.ibm.com/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-getting-started)

Your monitoring platform choice will mainly depend on your `cloud lock-in` situation, appetite for pure-containerised solution, cost, and skills. 

> Often logging and monitoring solutions are `bundled` together on your cloud provider side so that in essence you can get both capabilities with a single product.

#### Monitor your Apps

Here your task is to decide `how and what` you need to monitor. In the context of containerised apps this gives few options:

> 1. Container level `probes`, such as `liveliness` or `readiness`
>     - Here you can setup your containers to `register` onto the monitoring platform when these start up, using `Prometheus`
> 2. `Cloud native` applications monitoring
>     - You let your cloud monitoring solution to keep an eye on the `cloud resources`
> 3. Traditional `ping` request-response mechanism
>     - Simply call a URL and inspect response - it's actually a pretty good approach to iron out potential `networking issues`, depending where you ping it from of course

### [<< Previous](/start-early-with-cicd-and-automation) | [Next >>](/cloud-first-strategy-is-the-theme-of-the-day)