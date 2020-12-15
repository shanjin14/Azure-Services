### Azure Batch



#### Using custom image in Azure Batch 

https://docs.microsoft.com/en-us/azure/batch/batch-sig-images

To use your own custom VM image, below are the steps:
1. Create an VM Image (Refer to the link above for more detail steps)
2. Create a Shared Image Gallery (Refer to the link above for more detail steps)
3. Add VM Image definition in step #1 into Shared Image Gallery
4. Create a service prinicpal in Azure Active Directory (Azure Batch only accept AD authentication if want to ue custom VM Image)
5. Give Service principal an appropriate role (contributor) at resource group level or individual components level (need image, storage account, batch)
6. Follow the code above 

##### Benefit:
1. We can pre-install all the packages needed for the work and hence reduce the startup time. 
package such as cmdstan can take long time to install hence better create your own custom image


