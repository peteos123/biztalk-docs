---
description: "Learn more about: How to List the Properties of an Affiliate Application"
title: "How to List the Properties of an Affiliate Application"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to List the Properties of an Affiliate Application
This command shows the following information about the affiliate application. For more information about the properties for an affiliate application, see [SSO Affiliate Applications](../core/sso-affiliate-applications.md).  
  
 The SSO system obtains this information from the xml file that you used to update the affiliate application. For more information, see [How to Update the Properties of an Affiliate Application](../core/how-to-update-the-properties-of-an-affiliate-application.md).  
  
### To display the properties of an affiliate application using the administration utility  
  
1. On the **Start** menu, click **Run**, and then type **cmd**.  
  
2. At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3. Type **ssomanage –displayapp \<application name>**, where \<application name> is the name of the Affiliate Application you want to display the properties for.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
### To display the properties of an affiliate application using the client utility  
  
1. On the **Start** menu, click **Run**, and then type **cmd**.  
  
2. At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is \<*install drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3. Type **ssoclient –displayapp \<application name>**, where \<application name> is the name of the Affiliate Application you want to display the properties for.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [Managing User Mappings](../core/managing-user-mappings.md)   
 [Managing Affiliate Applications](../core/managing-affiliate-applications.md)
