---
description: "Learn more about: How to Configure a Range of 3270 LUs"
title: "How to Configure a Range of 3270 LUs2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Configure a Range of 3270 LUs
You can create a consecutively numbered range of logical units (LU). To do so, you must identify the base LU name limited to eight characters on which the numbered range of names will be built.  
  
 After identifying the base LU name, you can create the LUs by identifying the number of LUs in the range and the number the range will start with. [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will create LUs using the sequential numbering scheme.  
  
### To configure a range of 3270 LUs  
  
1.  In SNA Manager, ensure that the appropriate service is inactive by right-clicking **SNA service**, and then click **Stop**.  
  
2.  Right-click the connection to which you want to assign the LUs. Point to **All Tasks**, and then click the **Range of LUs**.  
  
3.  Fill in the LU Creation Wizard, and click **Finish** when done.  
  
4.  On the **Action** menu, click **Save Configuration**.  
  
5.  On the **Action** menu, click **Refresh**.  
  
> [!NOTE]
>  When you create a range of LUs, all the LUs are given the same properties. You can modify individual LUs after creating them.  
  
## See Also  
 [Creating and Configuring LUs](../core/creating-and-configuring-lus1.md)
