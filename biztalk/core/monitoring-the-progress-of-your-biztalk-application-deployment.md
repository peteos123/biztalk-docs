---
description: "Learn more about: Monitoring the Progress of Your BizTalk Application Deployment"
title: "Monitoring the Progress of Your BizTalk Application Deployment"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Monitoring the Progress of Your BizTalk Application Deployment
You can monitor the progress of your BizTalk application deployment in two ways:  
  
- **BizTalk installation log**: You can consult the installation log that BizTalk Server generates. Installation logs are located in %SystemDrive%\Documents and Settings\\<*current user*\>\Application Data\Microsoft\BizTalk Server\Deployment.  
  
- **Local event log**: You can track the progress of an installation in the local event log. Therefore, you can track custom installation actions on a per-server basis.  
  
- **Windows Installer log**: Microsoft Windows Installer creates a log file on the local computer that logs the actions of a custom action. You can specify this log file by using the /log option of the msiexec command. For more information, see the documentation for Windows Installer.  
  
> [!IMPORTANT]
>  Deploying or undeploying a property schema may expose sensitive data, and subsequently expose sensitive information during tracking. Whenever an assembly containing a property schema is deployed or undeployed, the event viewer logs an event in the Windows Application Event Log. You should check the event log for these messages to ensure that all assembly deployment activities are in line with your policies for any sensitive data. (The message generated to the Event Log for deployment is: "The user "{1}" deployed the assembly "{0}" containing property schemas." The message generated to the Event Log for undeployment is: "The user "{1}" undeployed the assembly "{0}" containing property schemas.")  
  
## See Also  
 [Deploying BizTalk Applications](../core/deploying-biztalk-applications.md)
