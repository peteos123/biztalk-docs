---
description: "Learn more about: How to Set Credentials for the Affiliate Application Using the Client Utility"
title: "How to Set Credentials for the Affiliate Application Using the Client Utility"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Set Credentials for the Affiliate Application Using the Client Utility
Use this command to set the credentials for a user so that the user is able to access a specific application. This command also automatically enables the mapping.  
  
 This command does not display the password as you type it.  
  
 If the user mapping already exists, this command will set the credentials for that existing mapping. If you have not created the user mapping, the SSO system will prompt you for the user ID for the application.  
  
### To set credentials for the affiliate application using the client utility  
  
1.  On the **Start** menu, click **Run**, and then type **cmd**.  
  
2.  At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssoclient –setcredentials \<application name\>**, where **\<application name\>** is the specific application for which you want to set the credentials for.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
4.  When prompted for the user credentials, enter the user password for this application.  
  
5.  If you have not created the user mapping, the SSO system will prompt you for the user ID for the application.  
  
## See Also  
 [SSO Affiliate Applications](../core/sso-affiliate-applications.md)   
 [Managing Affiliate Applications](../core/managing-affiliate-applications.md)
