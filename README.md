
# Understand Kubernetes
Learn about Kubernetes and its fundamental concepts.
## Overview
Kubernetes is a portable, extensible, open source platform for managing containerized workloads and services, that facilitates both declarative configuration and automation. It has a large, rapidly growing ecosystem. Kubernetes services, support, and tools are widely available.

### Going back in time

Let's take a look at why Kubernetes is so useful by going back in time.

![Deployment evolution](https://d33wubrfki0l68.cloudfront.net/26a177ede4d7b032362289c6fccd448fc4a91174/eb693/images/docs/container_evolution.svg)

+ **Traditional deployment era** 

Early on, organizations ran applications on physical servers. `There was no way to define resource boundaries for applications in a physical server, and this caused resource allocation issues. `

For example, if multiple applications run on a physical server, there can be instances where one application would take up most of the resources, and as a result, the other applications would underperform. 

A solution for this would be to run each application on a different physical server. But this did not scale as resources were underutilized, and it was expensive for organizations to maintain many physical servers.

+ **Virtualized deployment era** 

As a solution, virtualization was introduced. It allows you to run multiple Virtual Machines (VMs) on a single physical server's CPU. `Virtualization allows applications to be isolated between VMs and provides a level of security as the information of one application cannot be freely accessed by another application.`

Virtualization allows better utilization of resources in a physical server and allows better scalability because an application can be added or updated easily, reduces hardware costs, and much more. With virtualization you can present a set of physical resources as a cluster of disposable virtual machines.

Each VM is a full machine running all the components, including its own operating system, on top of the virtualized hardware.

+ **Virtualized deployment era**

Containers are similar to VMs, but they have relaxed isolation properties to share the Operating System (OS) among the applications. Therefore, containers are considered lightweight. Similar to a VM, a container has its own filesystem, share of CPU, memory, process space, and more. As they are `decoupled from the underlying infrastructure, they are portable across clouds and OS distributions.`

### Containers benefits

Containers have become popular because they provide extra benefits, such as:

- **Easy Creation**
  Agile application creation and deployment: increased ease and efficiency of container image creation compared to VM image use.

- **Continuous**

  Continuous development, integration, and deployment: provides for reliable and frequent container image build and deployment with quick and efficient rollbacks (due to image immutability).

- **Decoupling**

  Dev and Ops separation of concerns: create application container images at build/release time rather than deployment time, thereby decoupling applications from infrastructure.

- **Observability**

  not only surfaces OS-level information and metrics, but also application health and other signals.

- **Environmental Consistency**

  Environmental consistency across development, testing, and production: runs the same on a laptop as it does in the cloud.

- **Portability**

  Cloud and OS distribution portability: runs on Ubuntu, RHEL, CoreOS, on-premises, on major public clouds, and anywhere else.

- **Raises the level of abstraction**

  Application-centric management: raises the level of abstraction from running an OS on virtual hardware to running an application on an OS using logical resources.

- **Micro-services**

  Loosely coupled, distributed, elastic, liberated micro-services: applications are broken into smaller, independent pieces and can be deployed and managed dynamically – not a monolithic stack running on one big single-purpose machine.

- **Resource isolation**

  Predictable application performance.

- **Resource utilization**

  High efficiency and density.

### Why you need Kubernetes and what it can do

Containers are a good way to bundle and run your applications. In a production environment, you need to manage the containers that run the applications and `ensure that there is no downtime`. For example, if a container goes down, another container needs to start. Wouldn't it be easier if this behavior was handled by a system?



That's how Kubernetes comes to the rescue! Kubernetes provides you with a framework to run distributed systems resiliently. It takes care of scaling and failover for your application, provides deployment patterns, and more. For example: Kubernetes can easily manage a canary deployment for your system.



Kubernetes provides you with:

+ **Service discovery and load balancing**

  Kubernetes can expose a container using the DNS name or using their own IP address. If traffic to a container is high, Kubernetes is able to load balance and distribute the network traffic so that the deployment is stable.

+ **Storage orchestration**

  Kubernetes allows you to automatically mount a storage system of your choice, such as local storages, public cloud providers, and more.

+ **Automated rollouts and rollbacks**

  You can describe the desired state for your deployed containers using Kubernetes, and it can change the actual state to the desired state at a controlled rate. For example, you can automate Kubernetes to create new containers for your deployment, remove existing containers and adopt all their resources to the new container.

+ **Automatic bin packing**

  You provide Kubernetes with a cluster of nodes that it can use to run containerized tasks. You tell Kubernetes how much CPU and memory (RAM) each container needs. Kubernetes can fit containers onto your nodes to make the best use of your resources.

+ **Self-healing**

  Kubernetes restarts containers that fail, replaces containers, kills containers that don't respond to your user-defined health check, and doesn't advertise them to clients until they are ready to serve.

+ **Secret and configuration management**

  Kubernetes lets you store and manage sensitive information, such as passwords, OAuth tokens, and SSH keys. You can deploy and update secrets and application configuration without rebuilding your container images, and without exposing secrets in your stack configuration.

### What Kubernetes is not

Kubernetes is not a traditional, all-inclusive PaaS (Platform as a Service) system. Since Kubernetes operates at the container level rather than at the hardware level, it provides some generally applicable features common to PaaS offerings, such as deployment, scaling, load balancing, and lets users integrate their logging, monitoring, and alerting solutions. However, Kubernetes is not monolithic, and these default solutions are optional and pluggable. `Kubernetes provides the building blocks for building developer platforms, but preserves user choice and flexibility where it is important.`

Kubernetes:

- Does not limit the types of applications supported. 

  Kubernetes aims to support an extremely diverse variety of workloads, including stateless, stateful, and data-processing workloads. If an application can run in a container, it should run great on Kubernetes.	

  ✅ 

+ Does not provide application-level services.

  Components (such as middleware (for example, message buses), data-processing frameworks (for example, Spark), databases (for example, MySQL), caches, nor cluster storage systems (for example, Ceph) as built-in services. ) can run on Kubernetes, and/or can be accessed by applications running on Kubernetes through portable mechanisms, such as the [Open Service Broker](https://openservicebrokerapi.org/).

  ✅

+ Additionally, Kubernetes is not a mere orchestration system. 

  In fact, it eliminates the need for orchestration. The technical definition of orchestration is execution of a defined workflow: first do A, then B, then C. In contrast, Kubernetes comprises a set of independent, composable control processes that continuously drive the current state towards the provided desired state. It shouldn't matter how you get from A to C. Centralized control is also not required. This results in a system that is easier to use and more powerful, robust, resilient, and extensible.

- Does not deploy source code and does not build your application. 

  Continuous Integration, Delivery, and Deployment (CI/CD) workflows are determined by organization cultures and preferences as well as technical requirements.

  => CI/CD workflows

- Does not dictate logging, monitoring, or alerting solutions. 

  It provides some integrations as proof of concept, and mechanisms to collect and export metrics.

  => [prometheus](https://github.com/prometheus/prometheus)

- Does not provide nor mandate a configuration language/system (for example, Jsonnet). 

  It provides a declarative API that may be targeted by arbitrary forms of declarative specifications.

  => ❎ How to do this ? 

- Does not provide nor adopt any comprehensive machine configuration, maintenance, management, or self-healing systems.

  =>  ❎ How to do this ? 

+ Additionally, Kubernetes is not a mere orchestration system. In fact, it eliminates the need for orchestration. The technical definition of orchestration is execution of a defined workflow: first do A, then B, then C. In contrast, Kubernetes comprises a set of independent, composable control processes that continuously drive the current state towards the provided desired state. It shouldn't matter how you get from A to C. Centralized control is also not required. This results in a system that is easier to use and more powerful, robust, resilient, and extensible.

## Kubernetes Components

When you deploy Kubernetes, you get a cluster.



A Kubernetes cluster consists of a set of worker machines, called [nodes](https://kubernetes.io/docs/concepts/architecture/nodes/), that run containerized applications. Every cluster has at least one worker node.



The worker node(s) host the [Pods](https://kubernetes.io/docs/concepts/workloads/pods/) that are the components of the application workload. The [control plane](https://kubernetes.io/docs/reference/glossary/?all=true#term-control-plane) manages the worker nodes and the Pods in the cluster. In production environments, the control plane usually runs across multiple computers and a cluster usually runs multiple nodes, providing fault-tolerance and high availability.






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
+ [Kubernetes(k8s)手册](https://www.w3cschool.cn/kubernetes/)