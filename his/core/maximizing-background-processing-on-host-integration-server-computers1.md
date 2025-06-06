---
description: "Learn more about: Maximizing Background Processing on Host Integration Server Computers"
title: "Maximizing Background Processing on Host Integration Server Computers1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Maximizing Background Processing on Host Integration Server Computers
Servers used primarily for communications run many important background processes (processes not related to user actions in the current window). These servers generally do not need to run foreground processes at maximum speed. Therefore, Host Integration Server throughput can be increased by making the operating system more responsive to background processes and less responsive to foreground processes.  
  
 As would be expected, a server that is less responsive to foreground processes will run local applications such as word-processing software, spreadsheets, or SNA Manager more slowly. Tasking is most appropriate for servers used primarily to support clients, not servers used locally as desktop computers.  
  
### To optimize background processing for a Windows server  
  
1.  Click Start, point to **Settings**, click **Control Panel**, and then double-click **System**.  
  
2.  Select the **Advanced** tab.  
  
3.  In the **Performance** box, click **Performance Options**.  
  
4.  In the **Application response** box,select **Background services**.  
  
5.  Click **OK**, and then click **OK** again.
