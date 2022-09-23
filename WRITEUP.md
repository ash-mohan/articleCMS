# Write-up Template

### Analyze, choose, and justify the appropriate resource option for deploying the app.

*For **both** a VM or App Service solution for the CMS app:*
- *Analyze costs, scalability, availability, and workflow*
- *Choose the appropriate solution (VM or App Service) for deploying the app*
- *Justify your choice*

The cost table below is for basic service plan App Service and Bs-series VMs. These provide a low-cost option for workloads that typically run at a low to moderate baseline CPU performance. I only examined B1/Basic instances for this exercise as they are the lowest cost that provide dedicated cores. There are free tiers available but resources must be shared. 

| Resource    | Instance | Cores | RAM     | Storage | Cost         |
| ----------- | -------- | ----- | ------- | ------- | ------------ |
| VM          | B1s      | 1     | 1 GiB   | 4 GiB   | $0.0104/hour |
| VM          | B1ms     | 1     | 2 GiB   | 4 GiB   | $0.0207/hour |
| VM          | B2s      | 2     | 4 GiB   | 8 GiB   | $0.0416/hour |
| VM          | B2ms     | 2     | 8 GiB   | 16 GiB  | $0.0832/hour |
| VM          | B4ms     | 4     | 16 GiB  | 32 GiB  | $0.1660/hour |
| App Service | B1       | 1     | 1.75 GB | 10 GB   | $0.075/hour  |
| App Service | B2       | 2     | 3.5 GB  | 10 GB   | $0.15/hour   |
| App Service | B3       | 4     | 7 GB    | 10 GB   | $0.30/hour   |

Scalability

| Criteria      | VMs                        | App Service      |
| ------------- | -------------------------- | ---------------- |
| Autoscaling   | Virtual machine scale sets | Built-in service |
| Load Balancer | Azure Load Balancer        | Integrated       |
| Scale limit   | Platform image: 1000 nodes per scale set, Custom image: 600 nodes per scale set                      | 30 instances, 100 with App Service Environment     |


Virtual Machines provide a lot more control over the underlying infrastructure used for a service. There is a lot of customization when it comes to the type of VM, such as compute or memory-optimized VMs,and other specs like CPU, RAM, and storage. As such, VMs are best suited for situations where customization and accessibility of the infrastructure is important. Both VMs and App Services can be low cost depending on the hardware you choose. While you must pay for an App Service at all times, it is important to keep in mind the "time" cost that comes with setting up a VM for a production system. This is where App Services may be more beneficial. By allowing Azure to handle infrastructure, developers can focus more time on building the application. Similiar to VMs, App Services are highly scalable, allowing for vertical or horizontal scaling. App Services are limited to a maximum of 14GB of memory and 4 vCPU cores per instance, so they may not be suitable for applications that require large compute resources in a single instance. 

For this particular application, I decided to choose an App Service. In doing so, I will save time setting up the infrastrcture and can focus on the application code. I do not require any custom software or setup that would warrant the need for a VM. Additionally, this CMS application will not require more than the maximum hardware resources that an App Service allows for, so I will not have to worry about scalability and can keep costs low by sticking to a B1 instance. 

### Assess app changes that would change your decision.

*Detail how the app and any other needs would have to change for you to change your decision in the last section.* 

One scenario in which I would switch to a VM is if I was working for a company that had a custom CMS application with high demand. Let's say the on-premises server in which this application was deployed could not keep up with the current demand. Rather than wait for additional hardware to be approved and set up on premises, I could migrate the service using a custom image and deploy it to multiple VMs. 