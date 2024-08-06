# Key Types of Compute Resource

## SKU

In Azure, “SKU” stands for “Stock Keeping Unit.” SKU refers to a specific version or offering of a resource within Azure. 
It defines the characteristics, capabilities, features, performance levels, and pricing of various Azure resources and services
like virtual machines, storage accounts, databases, and more.

Example is VCPUs to memory ratios.

## VM

VM is a collection of resources that you make available to a certain unit of work.

When creating a VM you need the pick the SKU based on your needs.

### VM Scale Set

You can pick a certain template, configuration and scale types. Types of scale you can pick:
- Minimum 
- Maximum 
- Autoscale

This will create and delete virtual machines based on some schedule or trigger.


## Azure Dedicated Host

You are buying the whole capacity of the host in the cloud(that can contain multiple VMs). You also buy a host with a particular SKU.
Then the VMs in this host are created using that SKU.

## Azure Batch

Azure Batch is used for large scale workloads. It will run the VMs that are required for a certain job to run, and they will run in parallel.

## Containers

While VMs are about virtualizing the hardware, containers are about virtualizing the software.
Containers are sharing the container runtime, which means there is very little overhead. 
Containers are isolated from each other.

In Azure, container are provided using Azure Container Instance. They can ge grouped, and then they run on the same host.
You can provide a public endpoint or you can integrate with virtual network as well.

## Azure Kubernetes Service

There are two layers:
1. Management(provided as a service)
2. Node pools

## Azure App Service

They can run containers. They are typically related to web focused workload like web app, api, mobile application etc.
Depending on the SKU, they can provide autoscaling.

## Serverless

With serverless, you don't pay for some unit of virtual machine, you pay for the work it actually does.

Serverless services are event driven.

There are two offerings:
1. Azure Functions
2. Azure Logic Apps(no code)

## Azure Virtual Desktop

There are two layers:
1. Management
2. VMs(hosts)