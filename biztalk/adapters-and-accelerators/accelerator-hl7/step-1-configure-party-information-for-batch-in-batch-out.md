---
description: "Learn more about: Step 1: Configure Party Information for Batch In/Batch Out"
title: "Step 1: Configure Party Information for Batch In-Batch Out"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: how-to
---
# Step 1: Configure Party Information for Batch In/Batch Out
In this step, you turn off fragmentation of batching for the party, enabling the Batch In/Batch Out scenario. You then restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to enable the configuration change to take effect.  
  
### To turn off fragmentation of batching for the party  
  
1. Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.  
  
2. In BTAHL7 Configuration Explorer, on the **Parties** tab in the left-hand pane, click **Tutorial_BatchSource**.  
  
3. Click the **Batch Definition** tab.  
  
4. Select **No** for **Fragmentation required**, and then click **Save**.  
  
5. Make sure that in **Recoverable Interchange Support Required** dropdown list **False** is selected.  
  
   Proceed to [Step 2: Modify or Create the Send and Receive Ports](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md).
