---
id: call-home-metrics 
title: Call-Home Metrics 
keywords:
 - Call-Home Metrics
description: This section explains about the Call-Home Metrics.
---
# Call-home Metrics 

## Replicated Storage Default Information Collection 

By default, Replicated Storage (a.k.a Replicated Engine and f.k.a Mayastor) collects basic information related to the number and scale of user-deployed instances. The collected data is anonymous and is encrypted at rest. This data is used to understand storage usage trends, which in turn helps maintainers prioritize their contributions to maximize the benefit to the community as a whole. 

:::info
No user-identifiable information, hostnames, passwords, or volume data are collected. **ONLY** the below-mentioned information is collected from the cluster. 
:::

A summary of the information collected is given below:

| **Cluster information** | 
| :--- | 
|**K8s cluster ID**: This is a SHA-256 hashed value of the UID of your Kubernetes cluster's `kube-system` namespace.| 
|**K8s node count**: This is the number of nodes in your Kubernetes cluster.| 
|**Product name**: This field displays the name Replicated Storage.| 
|**Product version**: This is the deployed version of Replicated Storage.| 
|**Deploy namespace**: This is a SHA-256 hashed value of the  name of the  Kubernetes namespace where Replicated Storage Helm chart is deployed.| 
|**Storage node count**: This is the number of nodes on which the IO engine pods are scheduled and running.| 

|**Pool information**| 
| :--- | 
|**Pool count**: This is the number of Replicated Storage DiskPools in your cluster.| 
|**Pool maximum size**: This is the capacity of the Replicated Storage DiskPool with the highest capacity.| 
|**Pool minimum size**: This is the capacity of the Replicated Storage DiskPool with the lowest capacity.| 
|**Pool mean size**: This is the average capacity of the Replicated Storage DiskPools in your cluster.| 
|**Pool capacity percentiles**: This calculates and returns the capacity distribution of Replicated Storage DiskPools for the 50th, 75th and the 90th percentiles.| 
| **Pools created**: This is the number of successful pool creation attempts.|
| **Pools deleted**: This is the number of successful pool deletion attempts.|

|**Volume information**| 
| :--- | 
|**Volume count**: This is the number of Replicated Storage Volumes in your cluster.| 
|**Volume minimum size**: This is the capacity of the Replicated Storage Volume with the lowest capacity.| 
|**Volume mean size**: This is the average capacity of the Replicated Storage Volumes in your cluster.| 
|**Volume capacity percentiles**: This calculates and returns the capacity distribution of Replicated Storage Volumes for the 50th, 75th and the 90th percentiles.| 
| **Volumes created**: This is the number of successful volume creation attempts.|
| **Volumes deleted**: This is the number of successful volume deletion attempts. |

|**Replica Information**| 
| :--- | 
|**Replica count**: This is the number of Replicated Storage Volume replicas in your cluster.| 
|**Average replica count per volume**: This is the average number of replicas each Replicated Storage Volume has in your cluster.| 

### Storage Location of Collected Data 

The collected information is stored on behalf of the OpenEBS project by DataCore Software Inc. in data centers located in Texas, USA.

## Disable Specific Data Collection 

To disable collection of **usage data** or generation of **events**, the following Helm command, along with the flag, can either be executed during installation or can be re-executed post-installation.

### Disable Collection of Usage Data

To disable the collection of data metrics from the cluster, add the following flag to the Helm install command. 

```
--set obs.callhome.enabled=false
```

### Disable Generation of Events Data

When eventing is enabled, NATS pods are created to gather various events from the cluster, including statistical metrics such as *pools created*. To deactivate eventing within the cluster, include the following flag in the Helm installation command.

```
--set eventing.enabled=false
```
