---
layout:     post
title:      "Avoid Cascading Failures in Distributed System"
subtitle:   "Distributed System Pattern, Chaos Engineering"
date:       2021-04-04 16:00:00
author:     "Sofia"
header-img: "img/post-default-bg.jpeg"
catalog: true
tags:
    - Distributed System
    - Chaos Engineering
    - Tech
---

## Context and Problem

In big tech company, we usually have complicated system with thousands of micro services. Micro services decouple the monolithic system into different small components and improve engineers productiviy. However, it also increase the complexity of the system and make it hard to debug and maintain. One of the errors that we do not want to encounter is the [cascading failures](https://en.wikipedia.org/wiki/Cascading_failure).

Cascading failures can cause unavailability of multiple services and even the entire system. This is a non-trivial problem that I have seen recently at work. Therefore, I want to note down what I have learned from design and testing perspective to prevent such failure.

![alt text](/img/post-img/2021-04-04-cascading-failure/network-failure-example.gif)

## Design Pattern

### Pattern 1: Setting the limit

Unbounded traffic can cause high latency and error rate, and sometimes even take down your downstream services. It's very important to always get aware of your micro service's traffic and capacity. Stress tests/Performance tests are often used to determine the limit of the service. 

Additionally, we can implement a limit on the concurrent requests at each instance and fail the requests fast so that clients can retry on a different instances.

### Pattern 2: Be careful with client retry behavior

Sometimes we have the control of the client, for example, the system is a server-client architecture, or we are designing a component that sends requests to another micro service. Then, we should be careful with retry behavior. Simple retry can cause huge amount of requests sending to server at the exact same time and take down the server. To avoid that happens, client should limit the number of times and introduce exponential increasing backoff or little random noise between retries. 

An morden pattern is called [Circuit Breaker](https://docs.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker) that prevents an application from performing an operation which is likely to fail. While exponential backoff is specific to a single request, circuit breaker can share state across all requests from a client to the same server.

### Pattern 3: Fuzz testing to detect malformed input

Sometimes, the service can be crashed by the malformed inputs and clients keep retrying. One important thing to prevent this is to have automated testing practice to help detect these bad inputs and handle them in the program beforehand.

### Pattern 4: Be careful when failover

When the services in one data center failed, be careful when failover to another data center. We should make sure the failovered data center has enough capacity for the additional traffics so that we don't bring it down after failover.

### Pattern 5: Avoid long startup time

It will take a long time when you want to start new instances to serve rapidly increasing traffic or restart the instance if it fails for some reason.

### Pattern 6: Turn off traffic on the fly

Sometimes we are launching new features at client that introduces unexpected traffics. To quickly revert back to original state without rolling back, we can turn off the features. The knob can be in config or some experimental tool. One example is [Trex](https://engineering.linkedin.com/blog/2020/making-the-linkedin-experimentation-engine-20x-faster) heavily used at Linkedin which can turn off the feature without redeployment and making any change to code; It's often used to ramp new features.

## Testing - Chaos Engineering

[Chaos Engineering](https://en.wikipedia.org/wiki/Chaos_engineering) is a discipline of experimenting on a system to build confidence in the system's capability to withstand turbulent conditions in production. We intentionally try to break the system under certain stresses to determine potential outage, bottleneck and improve resiliency. It was first developed at Netflix in 2008. 

[![IMAGE ALT TEXT HERE](/img/post-img/2021-04-04-cascading-failure/chaos-engineering-netflix.png)](https://www.youtube.com/watch?v=3WRVgC8SiGc&t=9s)

Unlike fuzz testing, chaos engineering is a testing more from the system perspective instead of components. A blog demonstrate this clearly with the following diagram:

![alt text](/img/post-img/2021-04-04-cascading-failure/testing-diagram.png)

## Reference

[How to Avoid Cascading Failures in Distributed Systems](https://www.infoq.com/articles/anatomy-cascading-failure/)

[Chaos Engineering 101: principles, process, and examples](https://www.educative.io/blog/chaos-engineering-process-principles#what-is)

[Chaos Engineering and Testing](https://medium.com/@lawouach/chaos-engineering-and-testing-686660e3c744)

