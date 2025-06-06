---
description: "Learn more about: How to Set Credentials for the Affiliate Application Using the Client Utility"
title: "How to Set Credentials for the Affiliate Application Using the Client Utility"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Set Credentials for the Affiliate Application Using the Client Utility
Use the **setcredentials** command to set the credentials for a user so that the user can access a specific application.  
  
 This command does not display the password as you type it.  
  
 If the user mapping already exists, this command sets the credentials for the existing mapping. If you have not created the user mapping, the Single Sign-On (SSO) system prompts you for the user ID for the application.  
  
### To set credentials for the affiliate application using the client utility  
  
1.  Click **Start**, click **Run**, type `cmd`, and then press ENTER.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssoclient –setcredentials <application name>`, where *\<application name>* is the specific application for which you want to set the credentials.  
  
4.  When prompted for the user credentials, enter the user password for this application.  
  
5.  If you have not created the user mapping, the SSO system prompts you for the user ID for the application.  
  
## See Also  
 [SSO Affiliate Applications](../esso/sso-affiliate-applications.md)   
 [Managing Affiliate Applications](../esso/managing-affiliate-applications.md)
