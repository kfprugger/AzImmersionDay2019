---
title: Move a Recovery Services vault across Azure subscriptions or to another resource group
description: Instructions to move recovery services vault across azure subscriptions and resource groups.
services: backup
author: sogup
manager: vijayts
ms.service: backup
ms.topic: conceptual
ms.date: 1/4/2019
ms.author: sogup
---

# Move a Recovery Services vault across Azure Subscriptions and Resource Groups (Limited Public Preview)

This article explains how to move a Recovery Services vault configured for Azure Backup across Azure subscriptions, or to another resource group in the same subscription. You can use the Azure portal or PowerShell to move a Recovery Services vault.

## Prerequisites for moving a vault

- When moving between resource groups, both the source resource group and the target resource group are locked during the operation. Until the move completes, write and delete operations are blocked on the resource groups.
- Only the subscription admin has the permissions to move a vault.
- When moving a vault across subscriptions, the target subscription must exist in an enabled state, and must be in the same tenant as the source subscription.
- You must have permission to perform write operations on the target resource group.
- You cannot change the location of the Recovery Services vault. Moving the vault only changes the resource group. The new resource group may be in a different location, but that doesn't change the vault’s location.
- Currently you can move one Recovery Services vault, per region, at a time.
- If a VM doesn’t move with the Recovery Services vault across subscriptions, or to a new resource group, the current VM recovery points remain intact in the vault until they expire.
- Whether the VM is moved with the vault or not, you can always restore the VM from the retained backup history in the vault.
-	The Azure Disk Encryption requires that your key vault and VMs reside in the same Azure region and subscription.
-	To move a virtual machine with managed disks, see this [article](https://azure.microsoft.com/blog/move-managed-disks-and-vms-now-available/).
-	The options for moving resources deployed through the Classic model differ depending on whether you are moving the resources within a subscription, or to a new subscription. For more information, see this [article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-move-resources#classic-deployment-limitations).
-	Backup policies defined for the vault are retained after the vault moves across subscriptions or to a new resource group.
-	Currently, you cannot move vaults containing the Azure Files, Azure File Sync, or SQL in IaaS VMs across subscriptions and resource groups. Support for these scenarios will be added in future releases.
-	If you move a vault containing VM backup data, across subscriptions, you must move your VMs to the same subscription, and use the same target resource group to continue backups.<br>

> [!NOTE]
>
Recovery Services vaults configured to use with **Azure Site Recovery** can’t move, yet. If you have configured any VMs (Azure IaaS, Hyper-V, VMware) or physical machines for disaster recovery using the **Azure Site Recovery**, the move operation will be blocked. The resource move feature for Site Recovery service is not yet available.
>
>

## Register the source subscription to Move your Recovery Services vault

To register the source subscription to **Move** your Recovery Services vault, run the following cmdlets from PowerShell terminal:

1. Sign in to your Azure account

  ```
  Connect-AzureRmAccount
  ```

2.	Select the subscription that you want to register

    ```
    Get-AzureRmSubscription –SubscriptionName "Subscription Name" | Select-AzureRmSubscription
    ```
3.	Register this subscription

  ```
  Register-AzureRmProviderFeature -ProviderNamespace Microsoft.RecoveryServices -FeatureName RecoveryServicesResourceMove
  ```

4. Run the command

  ```
  Register-AzureRmResourceProvider -ProviderNamespace Microsoft.RecoveryServices
  ```

Wait for 30 minutes for the subscription to be whitelisted before you start with the move operation using the Azure portal or PowerShell.

## Use Azure portal to move a Recovery Services vault to different resource group

To move a recovery services vault and its associated resources to different resource group

1. Sign in to the [Azure portal](https://portal.azure.com/).
2. Open the list of **Recovery Services vaults** and select the vault you want to move. When the vault dashboard opens, it appears as shown in the following image.

  ![Open Recover Service Vault](./media/backup-azure-move-recovery-services/open-recover-service-vault.png)

  If you do not see the **Essentials** information for your vault, click the drop-down icon. You should now see the Essentials information for your vault.

  ![Essentials Information tab](./media/backup-azure-move-recovery-services/essentials-information-tab.png)

3. In the vault overview menu, click **change** next to the **Resource group**, to open the **Move resources** blade.

  ![Change Resource Group](./media/backup-azure-move-recovery-services/change-resource-group.png)

4. In the **Move resources** blade, for the selected vault it is recommended to move the optional related resources by selecting the checkbox as shown in the following image.

  ![Move Subscription](./media/backup-azure-move-recovery-services/move-resource.png)

5. To add the target resource group, in the **Resource group** drop-down list select an existing resource group or click **create a new group** option.

  ![Create Resource](./media/backup-azure-move-recovery-services/create-a-new-resource.png)

6. After adding the resource group, confirm **I understand that tools and scripts associated with moved resources will not work until I update them to use new resource IDs** option and then click **OK** to complete moving the vault.

  ![Confirmation Message](./media/backup-azure-move-recovery-services/confirmation-message.png)


## Use Azure portal to move a Recovery Services vault to a different subscription

You can move a Recovery Services vault and its associated resources to a different subscription

1. Sign in to the [Azure portal](https://portal.azure.com/).
2. Open the list of Recovery Services vaults and select the vault you want to move. When the vault dashboard opens, it appears as shown the following image.

    ![Open Recover Service Vault](./media/backup-azure-move-recovery-services/open-recover-service-vault.png)

    If you do not see the **Essentials** information for your vault, click the drop-down icon. You should now see the Essentials information for your vault.

    ![Essentials Information tab](./media/backup-azure-move-recovery-services/essentials-information-tab.png)

3. In the vault overview menu, click **change** next to **Subscription**, to open the **Move resources** blade.

  ![Change Subscription](./media/backup-azure-move-recovery-services/change-resource-subscription.png)

4. Select the resources to be moved, here we recommend you to use the **Select All** option to select all the listed optional resources.

  ![move resource](./media/backup-azure-move-recovery-services/move-resource-source-subscription.png)

5. Select the target subscription from the **Subscription** drop-down list, where you want the vault to be moved.
6. To add the target resource group, in the **Resource group** drop-down list select an existing resource group or click **create a new group** option.

  ![Add Subscription](./media/backup-azure-move-recovery-services/add-subscription.png)

7. Click **I understand that tools and scripts associated with moved resources will not work until I update them to use new resource IDs** option to confirm, and then click **OK**.

> [!NOTE]
> Cross subscription backup (RS vault and protected VMs are in different subscriptions) is not a supported scenario. Also, storage redundancy option from local redundant storage (LRS) to global redundant storage (GRS) and vice versa cannot be modified during the vault move operation.
>
>

## Use PowerShell to move a vault

To move a Recovery Services vault to another resource group, use the `Move-AzureRMResource` cmdlet. `Move-AzureRMResource` requires the resource name and type of resource. You can get both from the `Get-AzureRmRecoveryServicesVault` cmdlet.

```
$destinationRG = "<destinationResourceGroupName>"
$vault = Get-AzureRmRecoveryServicesVault -Name <vaultname> -ResourceGroupName <vaultRGname>
Move-AzureRmResource -DestinationResourceGroupName $destinationRG -ResourceId $vault.ID
```

To move the resources to different subscription, include the `-DestinationSubscriptionId` parameter.

```
Move-AzureRmResource -DestinationSubscriptionId "<destinationSubscriptionID>" -DestinationResourceGroupName $destinationRG -ResourceId $vault.ID
```

After executing the above cmdlets, you will be asked to confirm that you want to move the specified resources. Type **Y** to confirm. After a successful validation, the resource moves.

## Use CLI to move a vault

To move a Recovery Services vault to another resource group, use the following cmdlet:

```
az resource move --destination-group <destinationResourceGroupName> --ids <VaultResourceID>
```

To move to a new subscription, provide the `--destination-subscription-id` parameter.

## Post migration

1. You need to set/verify the access controls for the resource groups.  
2. The Backup reporting and monitoring feature needs to be configured again for the vault post the move completes. The previous configuration will be lost during the move operation.



## Next steps

You can move many different types of resources between resource groups and subscriptions.

For more information, see [Move resources to new resource group or subscription](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-move-resources).
