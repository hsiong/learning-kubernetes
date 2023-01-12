
# Understand Kubernetes
Learn about Kubernetes and its fundamental concepts.
## Overview
Kubernetes is a portable, extensible, open source platform for managing containerized workloads and services, that facilitates both declarative configuration and automation. It has a large, rapidly growing ecosystem. Kubernetes services, support, and tools are widely available.

## Going back in time

Let's take a look at why Kubernetes is so useful by going back in time.

![Deployment evolution](https://d33wubrfki0l68.cloudfront.net/26a177ede4d7b032362289c6fccd448fc4a91174/eb693/images/docs/container_evolution.svg)

+ **Traditional deployment era** 

Early on, organizations ran applications on physical servers. <u>There was no way to define resource boundaries for applications in a physical server, and this caused resource allocation issues.</u> 

For example, if multiple applications run on a physical server, there can be instances where one application would take up most of the resources, and as a result, the other applications would underperform. 

A solution for this would be to run each application on a different physical server. But this did not scale as resources were underutilized, and it was expensive for organizations to maintain many physical servers.

+ **Virtualized deployment era** 

As a solution, virtualization was introduced. It allows you to run multiple Virtual Machines (VMs) on a single physical server's CPU. <u>Virtualization allows applications to be isolated between VMs and provides a level of security as the information of one application cannot be freely accessed by another application.</u>

Virtualization allows better utilization of resources in a physical server and allows better scalability because an application can be added or updated easily, reduces hardware costs, and much more. With virtualization you can present a set of physical resources as a cluster of disposable virtual machines.

Each VM is a full machine running all the components, including its own operating system, on top of the virtualized hardware.






# Try Kubernetes
Follow tutorials to learn how to deploy applications in Kubernetes.

# Set up a K8s cluster
Get Kubernetes running based on your resources and needs.

# Learn how to use Kubernetes
Look up common tasks and how to perform them using a short sequence of steps.













# Reference & Thanks
+ [kubernetes docs](https://kubernetes.io/docs/home/)
+ [Kubernetes 基础教程](https://lib.jimmysong.io/kubernetes-handbook/)
+ [Kubernetes 指南](https://feisky.gitbooks.io/kubernetes/content/)