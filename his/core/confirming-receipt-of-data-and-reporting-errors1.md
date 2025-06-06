---
description: "Learn more about: Confirming Receipt of Data and Reporting Errors"
title: "Confirming Receipt of Data and Reporting Errors1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Confirming Receipt of Data and Reporting Errors
The following calls confirm receipt of data or report an error:  
  
> [!NOTE]
>  The names of the calls are pseudonyms. The actual C function names appear in parentheses after the pseudonyms. For example, **Accept_Conversation** is the pseudonym for a call. The actual function name is **cmaccp**.  
  
 [Confirmed](./confirmed-cpi-c-2.md)( **cmcfmd**)  
 Replies to a confirmation request from the partner program. It informs the partner program that the local program has not detected an error in the received data. Because the program issuing the confirmation request waits for a confirmation, **Confirmed** synchronizes the processing of the two programs.  
  
 [Send_Error](./send-error-cpi-c-2.md)( **cmserr**)  
 Notifies the partner program that the local program has encountered an application-level error. The local program can use **Send_Error** to inform the partner program of an error encountered in received data, to reject a confirmation request, or to truncate an incomplete logical record it is sending.  
  
 [Set_Error_Direction](./set-error-direction-cpi-c-1.md)( **cmsed**)  
 Specifies whether a program detected an error while receiving data or while preparing to send data. Error direction is relevant only when a program issues **Send_Error** in SEND_PENDING state—immediately after issuing [Receive](./receive-cpi-c-2.md) and receiving data as well as a *status_received* value of CM_SEND_RECEIVED.  
  
 [Set_Log_Data](./set-log-data-cpi-c-2.md)( **cmsld**)  
 Used in a basic conversation, this call specifies a log message (log data) and its length to be sent to the partner logical unit (LU). This call has an effect only in basic conversations. If present, log data is sent when **Send_Error** is issued or when the conversation is abnormally deallocated. After the log data is sent, Common Programming Interface for Communications (CPI-C) resets the log data to NULL and the log data length to zero.
