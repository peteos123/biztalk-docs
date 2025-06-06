---
description: "Learn more about: How to Set the Duration on an RTA Window"
title: "How to Set the Duration on an RTA Window"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Set the Duration on an RTA Window
Administrators use the **set-rtawindow** command to set the duration for the specified real-time aggregation (RTA).  
  
### To set the duration on an aggregation  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt. Press **ENTER**.  
  
3. Type **bm set-rtawindow -View:\<view name\> -Activity:\<activity name\> -Name:\<RTA name\> -TimeLength:\<integer number\> -TimeUnit:Day&#124;Hour&#124;Minute**.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
4. Press **ENTER**.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Management Utility](../core/bam-management-utility.md)   
 [How to Get the Duration on an RTA Window](../core/how-to-get-the-duration-on-an-rta-window.md)
