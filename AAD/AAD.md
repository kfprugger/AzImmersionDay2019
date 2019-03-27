# Welcome to the AAD Walkthrough 
The purpose of this small exercise is to take the globally permissive access control list (ACL) that has been granted to all users in this session to **ALL** resources to only those you would like on your own resource, namely just you. 

Because the administrator has granted "owner" to all resource groups and YOU are a member of that group, you can reassign "owner" to yourself and remove the more permissive, expansive security group.

## ACL Reassignment Exercise
1. View the current permissions of your resource group by navigating to **https://portal.azure.com**. **NOTE:** This same process can be used on practically EVERY resource in Azure from Azure SQL Databases down to the network interface cards on VMs.

![RGNav](AAD/images/RGNav.jpg)

