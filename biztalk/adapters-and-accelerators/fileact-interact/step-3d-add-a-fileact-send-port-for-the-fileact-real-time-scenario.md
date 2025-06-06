---
description: "Learn more about: Step 3D: Add a FILEACT Send Port for the FileAct Real-Time Scenario"
title: "Step 3D: Add a FILEACT Send Port for the FileAct Real-Time Scenario"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Step 3D: Add a FILEACT Send Port for the FileAct Real-Time Scenario
Before you start this step, you must complete [Step 3C: Add a FILE Send Port to Capture Sw:HandleRequest Message for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-message-for-fileact.md).  
  
### To add a FILEACT send port  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.  
  
3.  Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.  
  
4.  In the **Send Port Properties** window, name the send port, Tutorial_FA_SendRequest_RealTime.  
  
5.  In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILEACT**, and then click **Configure**.  
  
6.  In the **FILEACT Transport Properties** dialog box, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Password**|Set the password as appropriate for SAG connectivity.|  
    |**User name**|Set the user name as appropriate for SAG connectivity.|  
    |**Adapter Mode**|From the drop-down list, select **Store and Forward**.|  
    |**Non-Repudiation Indicator**|From the drop-down list, select **FALSE**.|  
    |**Request Type**|Set to the appropriate \<RequestType\> string, based on your provisioning with SWIFT.|  
    |**ResponseCrypto**|From the drop-down list, select **FALSE**.|  
    |**Requestor**|Set to the appropriate \<Requestor\> string, based on your provisioning with SWIFT.|  
    |**Responder**|Set to the appropriate \<Responder\> string based on your provisioning with SWIFT.|  
    |**Service Name**|Set to the appropriate \<service name\> based on your provisioning with SWIFT.|  
    |**Acknowledgement Indicator**|From the drop-down list, select **FALSE**.|  
    |**Event end-point**|From the drop-down list, select **FALSE**.|  
    |**File Compression**|From the drop-down list, select **None**.|  
    |**Physical Folder Name**|Type C:\SWIFTAdapterTutorial\Fileact\ClientLocation.|  
    |**Transfer end-point**|Type the appropriate end-point for the SAG routing set. This value should match the SnL endpoint you configured in SAG.|  
    |**ServiceProfile**|From the drop-down list, select **Transaction Count**.|  
    |**Delivery notification**|From the drop-down list, select **FALSE**.|  
    |**Notify queue**|Type the queue name, based on your provisioning with SWIFT.|  
  
    > [!NOTE]
    >  If message with Transaction Count is to be transferred, set the Service Profile Mode to “Transaction Count” in the FileAct send port.  
  
7.  Click **OK**.  
  
8.  In the **Send Port Properties** window, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Send handler**|From the drop-down list, select the Fileact host.|  
    |**Send pipeline**|From the drop-down list, select **XMLTransmit**.|  
    |**Receive pipeline**|From the drop-down list, select **XMLReceive**.|  
  
9. In the Send Port Properties window, on the **Filters** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Property**|From the drop-down list, select **BTS.ReceivePortName**.|  
    |**Operator**|From the drop-down list, select **==**.|  
    |**Value**|Type Tutorial_FA_InputRequest_RealTime.|  
    |**Group by**|Leave the default value.|  
  
10. Click **OK**.  
  
## See Also  
 [Step 3: Create the Send Ports and Receive Ports for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md)   
 [Step 3A: Add a FILE Receive Location for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-real-time-scenario.md)   
 [Step 3B: Add a FILEACT Receive Location for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario.md)   
 [Step 3C: Add a FILE Send Port to Capture Sw:HandleRequest Message for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-message-for-fileact.md)   
 [Step 3E: Add a FILE Send Port to Capture Sw:ExchangeFileResponse Message for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3e-add-file-send-port-to-get-sw-exchangefileresponse-message-for-fileact.md)
