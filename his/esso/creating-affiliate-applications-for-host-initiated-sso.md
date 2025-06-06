---
description: "Learn more about: Creating Affiliate Applications for Host Initiated SSO"
title: "Creating Affiliate Applications for Host Initiated SSO"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Creating Affiliate Applications for Host Initiated SSO
You can define two types of applications:  
  
-   **Individual** There is a one-to-one relationship between Windows users and non-Windows users.  
  
-   **Host Group** Multiple non-Windows users can be mapped to the same Windows account.  
  
### To create an affiliate application using the MMC Snap-In  
  
1.  Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **Affiliate Applications**, and then click **New** to start the **Create New Affiliate Application Wizard**.  
  
4.  Use the wizard to select the properties of your affiliate application.  
  
### To create an individual type affiliate application using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –createapps <AffApp.xml>`, where *AffApp.xml* is the name of the xml file.  
  
     The following is a sample file:  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
      <application name="SSOApp_Host1">  
        <description>An Individual Type Affiliate Application for Host Initiated SSO</description>  
        <contact>someone@companyname.com</contact>  
        <appUserAccount>DomainName\AppUserGroup_HISSO</appUserAccount>  
        <appAdminAccount>DomainName\AppAdminGroup_HISSO</appAdminAccount>  
        <field ordinal="0" label="User ID" masked="no" />  
        <field ordinal="1" label="Password" masked="yes" />  
        <flags windowsInitiatedSSO="no" enableApp="yes" />  
      </application>  
    </SSO>  
  
    ```  
  
### To create a host group type affiliate application  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –createapps <AffApp.xml>`, where *AffApp.xml* is the name of the xml file.  
  
     The following is a sample file:  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
      <application name="SSOApp_HostGroupApp1">  
        <description>A Group Type Affiliate Application for Host Initiated SSO associating multiple non-Windows user to a single Windows user account(DomainName\WindowsUserAccount1)</description>  
        <contact>someone@companyname.com</contact>  
        <windowsAccount>DomainName\WindowsUserAccount1</windowsAccount>  
        <appAdminAccount>DomainName\AppAdminGroup_HISSO</appAdminAccount>  
        <field ordinal="0" label="User ID" masked="no" />  
        <field ordinal="1" label="Password" masked="yes" />  
        <flags  enableApp="yes" />  
      </application>  
    </SSO>  
  
    ```  
  
### To create an affiliate application supporting both Windows initiated SSO and host initiated SSO  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –createapps <AffApp.xml>`, where `AffApp.xml` is the name of the XML file.  
  
     The following is a sample file:  
  
    ```  
    <?xml version="1.0" ?>   
    - <SSO>  
    - <application name="SSOApp1">  
      <description>An Individual Type Affiliate Application for both Host Initiated SSO and Windows Initiated SSO</description>   
      <contact>someone@companyname.com</contact>   
      <appUserAccount>DomainName\AppUserGroup</appUserAccount>   
      <appAdminAccount>DomainName\AppAdminGroup</appAdminAccount>   
      <field ordinal="0" label="User ID" masked="no" />   
      <field ordinal="1" label="Password" masked="yes" />   
      <flags  enableApp="yes" />   
      </application>  
      </SSO>  
  
    ```  
  
## See Also  
 [Host Initiated Single Sign-On](../esso/host-initiated-single-sign-on.md)
