---
description: "Learn more about: How to Disable Alerts"
title: "How to Disable Alerts"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Disable Alerts
Administrators use the **disable-alerts** command to disable all of the alerts on the specified view.  
  
### To disable an alert  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt. Press **ENTER**.  
  
3. Type **bm disable-alerts -View:\<view name\>**.  
  
   > [!NOTE]
   >  If you have exported a BAM configuration as XML, do not modify the XML related to alerts. If you change XML related to alerts and deploy the changes, bm.exe will detect the change and enable BAM alerts.  
  
4. Press **ENTER**.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Management Utility](../core/bam-management-utility.md)   
 [How to Enable Alerts](../core/how-to-enable-alerts.md)
