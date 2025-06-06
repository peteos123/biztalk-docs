---
description: "Learn how to configure the HTTP receive adapter that receives and submits messages to BizTalk Server."
title: "How to Configure the HTTP Receive Adapter1"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Configure the HTTP Receive Adapter

You can use the HTTP receive adapter to submit messages to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. The HTTP receive adapter is an Internet Information Services (IIS) ISAPI extension that is hosted in the IIS process.  
  
### To configure the HTTP receive adapter  
  
1.  Copy the HTTP receive adapter (BTSHTTPReceive.dll) from **\<BizTalk\>\HttpReceive\>** to the folder that contains your Single Sign-On (SSO) project, for example:  
  
     **<Adapter_install>\biztalk\SSO\mySSODemo**  
  
    1.  Add a new Web service extension mySSODemo.  
  
    2.  Locate and copy **<BizTalk_install>\HttpReceive** to the folder that contains your SSO project, for example:  
  
         **<Adapter_install>\biztalk\SSO\mySSODemo\BTSHTTPReceive.dll.**  
  
    3.  Set the status of mySSODemo Web service extension to **Allowed**.  
  
2.  Restart IIS to apply all changes.  
  
## See Also  
 [Secure the adapter](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)
