---
description: "Learn more about: Associate the Interface Definition with the Mainframe Environment"
title: "Associate the Interface Definition with Mainframe"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Associate the Interface Definition with the Mainframe Environment
After you create a BizTalk project for your application that uses the BizTalk Adapter for Host Applications, and then add the .xsd file to the project, you must identify your target mainframe, and then associate the interface definition with the mainframe environment.  
  
## Configure the remote environment using TI Manager  
  
1.  Start TI Manager.  
  
2.  Double-click **Transaction Integrator** in the console tree.  
  
3.  Right-click **Remote Environments**, point to **New**, and then click **Remote Environment**.  
  
4.  Use the New Remote Environment Wizard to describe the environment on your target mainframe.  
  
     For more information about how to use the Remote Environment Wizard, see [Creating and Managing Remote Environments with TI Manager](../core/creating-and-managing-remote-environments-with-ti-manager1.md)  
  
## Administer the TI .NET assembly metadata using TI Manager  
  
1.  Start TI Manager.  
  
2.  Double-click **Transaction Integrator** in the console tree.  
  
3.  In the **Windows-Initiated Processing** node, right-click **Objects**, point to **New**, and then click **Object**.  
  
4.  Use the Object Wizard to associate the TI assembly that you created earlier with the remote environment of your target mainframe.  

  
## See Also  
 [Creating an Application for the BizTalk Adapter for Host Applications](../core/creating-an-application-for-the-biztalk-adapter-for-host-applications2.md)   
 [Creating a BizTalk Application](../core/creating-a-biztalk-application1.md)   
 [How to Export the Schema](../core/how-to-export-the-schema1.md)
