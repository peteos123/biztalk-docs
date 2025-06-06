---
description: "Learn more about: How to Use the ThrowDetailedError Switch"
title: "How to Use the ThrowDetailedError Switch"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Use the ThrowDetailedError Switch
If an error occurs, the Web client receives a generic **SoapException**.  
  
 To debug your published Web service, you can add a switch to the Web.config file to control the level of the exception details returned from the published Web service.  
  
 The Web.config file contains an application setting switch, **ThrowDetailedError**. **False** is the default setting for **ThrowDetailedError**. If you change the setting to **True**, the server proxy returns inner exception information to the Web client enabling you to debug the published Web service.  
  
 The following XML code shows the **ThrowDetailedError** switch that appears in the Web.config file under the \<appSettings\> node:  
  
```  
<appSettings>  
  <add key="ThrowDetailedError" value="False" />  
<appSettings/>  
```  
  
> [!IMPORTANT]
>  BizTalk Server does not return inner exception information to the Web client by default since it may contain sensitive information, such as application call stacks. After debugging, you should set the **ThrowDetailedError** setting to **False**.  
  
## See Also  
 [Debugging Published Web Services](../core/debugging-published-web-services.md)
