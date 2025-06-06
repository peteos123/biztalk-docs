---
description: "Learn more about: How to Enable a User Mapping"
title: "How to Enable a User Mapping"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Enable a User Mapping
You must enable a user mapping before it you can use the mapping in the Single Sign-On system.  
  
 When you enable a user mapping, it will appear as (E) **\<domain\>\\<username\>** when you list the user mappings.  
  
 Note that if you have set the credentials using the -setcredentials command, the mapping will already be enabled.  
  
### To enable a user mapping using the administration utility  
  
1.  On the **Start** menu, click **Run**, and then type **cmd**.  
  
2.  At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage –enablemapping \<domain\>\\<username\>\<application name\>**, where **\<domain\>** is the Windows domain for the user account, **\<username\>** is the Windows user name for which you want to enable the credentials, and **\<application name\>** is the name of the affiliate application you want to remove the user mapping for and then press ENTER.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
### To enable a user mapping using the client utility  
  
1.  On the **Start** menu, click **Run**, and then type **cmd**.  
  
2.  At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssoclient –enablemapping \<application name\>**, where **\<application name\>** is the name of the affiliate application you want to remove the user mapping for.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [How to Create User Mappings](../core/how-to-create-user-mappings.md)   
 [SSO Mappings](../core/sso-mappings.md)   
 [Managing Affiliate Applications](../core/managing-affiliate-applications.md)   
 [Managing User Mappings](../core/managing-user-mappings.md)
