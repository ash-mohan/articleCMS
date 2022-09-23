# Write-up Template

### Analyze, choose, and justify the appropriate resource option for deploying the app.

*For **both** a VM or App Service solution for the CMS app:*
- *Analyze costs, scalability, availability, and workflow*
- *Choose the appropriate solution (VM or App Service) for deploying the app*
- *Justify your choice*

- Virtual Machines provide a lot more control over the underlying infrastructure used for a service. There is a lot of customization when it comes to the type of VM, such as compute or memory-optimized VMs,and other specs like CPU, RAM, and storage. As such, VMs are best suited for situations where customization and accessability of the infrastructure is important. However, it is important to keep in mind the "time" cost that comes with setting up a VM for a production system. This is where App Services may be more beneficial. By allowing Azure to handle infrastructure, developers can focus more time on building the application. Similiar to VMs, App Services are highly scalable. However, the cost can add up as you’re paying for the service plan at all times. Additionally, App Services are limited to a maximum of 14GB of memory and 4 vCPU cores per instance, so they may not be suitable for applications that require large compute resources.

- For this particular application, I decided to choose an App Service. In doing so, I will save time setting up the infrastrcture and can focus on the application code. Additionally, this CMS application will not require more than the maximum hardware resources that an App Service allows for, so I will not have to worry about scalability. 

### Assess app changes that would change your decision.

*Detail how the app and any other needs would have to change for you to change your decision in the last section.* 

- One scenario in which I would switch to a VM is if I was working for a company that had a custom CMS application with high demand. Let's say the on-premises server in which this application was deployed could not keep up with the current demand. Rather than wait for additional hardware to be approved and set up on premises, I could migrate the service using a custom image and deploy it to multiple VMs. 