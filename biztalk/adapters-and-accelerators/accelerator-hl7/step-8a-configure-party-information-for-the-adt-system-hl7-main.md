---
description: "Learn more about: Step 8A: Configure Party Information for the ADT System_hl7_main"
title: "Step 8A: Configure Party Information for the ADT System_hl7_main"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: how-to
---
# Step 8A: Configure Party Information for the ADT System_hl7_main
In this step, you configure the party information for the ADT System.  
  
### To configure the ADT System party information  
  
1. In the BizTalk Administration Console, expand **BizTalk Server Administration**, and then expand **BizTalk Group**. Right-click **Parties**, point to **New**, and then click **Party**.  
  
2. In the Party Properties dialog box, in the **Name** field, type **ADT**. (The value you type in this box should match the original HL7 message instance, QRY^Q01.txt MSH3.)  
  
3. In the Console Tree, click **Send Ports**.  
  
4. In the **Send Port** pane, for **Name** in the first row, select **ADT_Send**, and then click **OK**.  
  
5. Click **Start**, point to **Programs**, point to **Microsoft  BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.  
  
6. In BTAHL7 Configuration Explorer, click the **Acknowledgment** tab. For **Acknowledgment Type**, select **EnhancedMode**.  
  
7. In the Acknowledgment Properties in Inboiund Message pane, for **MSH15 - Accept Acknowledgment Type**, select **AL**.  
  
8. In the Acknowledgment Properties pane, for **MSH16 - Application Acknowledgment Type**, select **NE**.  
  
9. Click **Save**, and then close BTAHL7 Configuration Explorer.  
  
   Proceed to [Step 8B: Configure Party Information for the HI System](../../adapters-and-accelerators/accelerator-hl7/step-8b-configure-party-information-for-the-hi-system.md).
