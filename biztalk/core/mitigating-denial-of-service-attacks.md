---
description: "Learn more about: Mitigating Denial of Service Attacks"
title: "Mitigating Denial of Service Attacks"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Mitigating Denial of Service Attacks
It is recommended to use the following mitigation techniques to help protect your BizTalk servers and services against Denial of Service attacks. You must decide which of these mitigation techniques are appropriate for your environment.

-   **Use the Authentication Required property in the receive port.** By default, BizTalk sends all the messages it receives to the MessageBox database, even if they come from an unknown or unresolved party (Guest.) To mitigate the potential of an attacker sending a large number of messages to BizTalk Server and flooding (filling) the MessageBox database, you can use the **Authentication Required** property in the receive port to only receive messages that come from parties BizTalk Server knows. You can choose either to drop the messages coming from an unknown party or to suspend them. For more information about the **Authentication Required** property, see [Authenticating the Sender of a Message](../core/authenticating-the-sender-of-a-message.md). In addition to the **Authentication Required** property, you should consider the use of an external mechanism such as firewall port filtering or IP-address blocking to protect against Denial of Service attacks.

-   **Limit the size of the messages that BizTalk can receive.** For example, when you use the SOAP receive adapter, you can avoid receiving very large messages size by setting the maxRequestLength attribute in the \<httpRuntime\> element to an acceptable size. The \<httpRuntime\> element is defined in the Machine.config file, which is located in the \<*drive*\>:\\<*Windows directory*\>\Microsoft.NET\Framework\vX.X.XXXXX\CONFIG directory. For more information about \<httpRuntime\> element, see the Microsoft MSDN Web site at [https://go.microsoft.com/fwlink/?LinkId=60948](/previous-versions/dotnet/netframework-4.0/e1f13641(v=vs.100)).

-   **Use strong DACLs for receive locations.** It is recommended that you use strong discretionary access control lists (DACLs) in the drop locations for the receive locations. For example, you must use strong DACLs in the directory from which the file receive location picks up messages, so that only authorized users can drop messages in this location.

-   **Use IPSec.** If you do not use hardware or software firewalls, use Internet Protocol security (IPSec) to help protect the messages and data as BizTalk Server transfers it from one server to another. For more information about IPSec, see the [IPSec Technical Reference](/previous-versions/windows/it-pro/windows-server-2003/cc740240(v=ws.10)).

## See Also
 [Identifying Potential Threats](../core/identifying-potential-threats.md)
 [Planning for Security](../core/planning-for-security.md)
