---
description: "Learn more about: How to Configure the Virtual Directory"
title: "How to Configure the Virtual Directory"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Configure the Virtual Directory
This topic describes the procedures for configuring the virtual directory and verifying the application for a user.  
  
### To configure the virtual directory  
  
1.  On the %systemdrive%, create a folder to be configured as a virtual directory.  
  
2.  Click **Start**, point to **Programs**, click **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.  
  
3.  Expand **\<server name\>** and then expand **Sites**.  
  
4.  Right-click **Default Web Site** and click **Add Virtual Directory**.  
  
5.  In the **Add Virtual Directory** dialog box, type the alias.  
  
6.  Type the path of the folder created in step 1. Alternatively, click **(…)** to browse to the folder location.  
  
7.  Click **OK**. The folder is displayed under the **Default Web Site** folder.  
  
8.  Right-click the folder and click **Convert to Application**.  
  
9. In the **Add Application** dialog box, click **OK**. The folder is converted to an application (you can see the change in the icon – from a folder icon to the Web site icon).  
  
## See Also  
 [Secure the adapter](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)
