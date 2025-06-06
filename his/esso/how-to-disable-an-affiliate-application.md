---
description: "Learn more about: How to Disable an Affiliate Application"
title: "How to Disable an Affiliate Application"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Disable an Affiliate Application
Use the MMC Snap-In or the **disableapp** command to disable the specified affiliate application.  
  
### To disable an affiliate application using the MMC Snap-In  
  
1.  Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click the affiliate application, and then click **Disable**.  
  
### To disable an affiliate application using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –disableapp <application name>`, where \<*application name*> is the name of the affiliate application you want to disable.  
  
## See Also  
 [SSO Affiliate Applications](../esso/sso-affiliate-applications.md)   
 [How to Enable an Affiliate Application](../esso/how-to-enable-an-affiliate-application.md)   
 [Managing User Mappings](../esso/managing-user-mappings.md)   
 [Managing Affiliate Applications](../esso/managing-affiliate-applications.md)
