---
description: "Learn more about: How to Retrieve the BAM Configuration File Using the BAM Management Utility"
title: "How to Retrieve the BAM Configuration File Using the BAM Management Utility"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Retrieve the BAM Configuration File Using the BAM Management Utility
Administrators and developers can use the BAM Management utility to retrieve the current configuration of the BAM infrastructure. The retrieved configuration can be used to migrate a BAM installation to a new server or it can be modified and used to update an existing BAM installation.  
  
## Prerequisites  
 The following are prerequisites for performing the procedure in this topic:  
  
-   Configured BAM databases  
  
-   Permissions to read the BAM Primary Import database  
  
### To retrieve the BAM configuration file using the BAM Management utility  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3. Type the following at the command line prompt: **bm get-config -FileName:\<output file\>**, where \<*output file*\> is replaced by the name of your BAM configuration file. Press **ENTER**.  
  
## See Also  
 [BAM Management Utility](../core/bam-management-utility.md)
