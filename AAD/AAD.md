# Welcome to the AAD Walkthrough 
The purpose of this small exercise is to take the globally permissive access control list (ACL) that has been granted to all users in this session to **ALL** resources to only those you would like on your own resource, namely just you. 

Because the administrator has granted "owner" to all resource groups and YOU are a member of that group, you can reassign "owner" to yourself and remove the more permissive, expansive security group.

## ACL Reassignment Exercise
1. View the current permissions of your resource group by navigating to **https://portal.azure.com**. **NOTE:** This same process can be used on practically EVERY resource in Azure from Azure SQL Databases down to the network interface cards on VMs.

![RGNav](images/RGNav.jpg)

2. Now navigate into the resource group assigned to you from the administrator. In this example, I am *"Student1"*.

![RGnav2](images/rgnav2.jpg)

3. Let's drill into the permissions by clicking on **Access Control (IAM)**

![RGSecurity](images/rgsec1.jpg)

4. Now, let's look at who has rights.

Click **Role Assignments** tab and then look at "Owners" under the  role assignments. ([Here's a description of all roles that come built-in](https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-assign-admin-roles))

In my example, I used my team's security group and assigned it owner. The next step will be to remove that group (since I'm a member of it, I have access to do so vis-a-vis the group membership and the "owner" role) and add only ourselves.

![RGsec2](images/rgsec2.jpg)

5. **IMPORTANT: DO THIS STEP FIRST** First, we'll add ourselves to the resource group and then we can remove the more expansive group permissions. 

![rgadd button](images/rgadd.jpg)

- For **Role**, Select **Owner**. Under **Select** type in your userID that you use on-campus (e.g. janedoe@institution.edu -- in my example I'm using my specific MSFT ID: robrakef@microsoft.com). *Click the name that pops up after you type in the **Select** box*. 

-  Finally, click Save.

![rgadd4](images/rgsec4.jpg)
6. To remove that group and put myself in, we'll start with removing it by selecting the check box and then clicking **Remove** at the top part of the blade. Then click **Yes**.
![rgsec3](images/rgsec3.jpg)


## Conclusion
Now, only YOU have permission to your resource group in Azure. 

Note you can use any combination of users/groups that are being synced from on-premises Active Directory as well as any combination of role assignments for almost every level of resources in Azure a la POSIX!

[Learn More!](https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-overview-user-model)