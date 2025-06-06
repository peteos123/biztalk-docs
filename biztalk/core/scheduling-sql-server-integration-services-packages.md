---
description: "Learn more about: Schedule SQL Server Integration Services Packages in BizTalk Server"
title: "Scheduling SQL Server Integration Services Packages"
ms.custom: "biztalk-2020"
ms.date: "01/14/2020"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---

# Schedule SQL Server Integration Services Packages in BizTalk Server

Users create BAM views based on data stored in an online analytical processing (OLAP) cube. The Cube Update Integration Services package refreshes the data in the cube so that OLAP views reflect the correct data.

 You must run this package at least once for the OLAP views to work. For ongoing maintenance, you should schedule the package to run on a regular basis.

> [!IMPORTANT]
>  If you restored the BAM Star Schema database or stopped [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] before running the Cube Update Integration Services package, you must refresh the data sources in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Manager or restart the OLAP service before you can run the package successfully.

 You can schedule a saved package to execute at specific times, either once or at recurring intervals. For example:

- Daily at midnight.

- Weekly on Sunday at 06:00.

- The first or last day of the month.

  A scheduled package is executed by [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] as a job.

  For information about running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] packages, see [https://go.microsoft.com/fwlink/?LinkId=125738](/sql/integration-services/packages/sql-server-agent-jobs-for-packages).

> [!NOTE]
>  By default, logging for archiving and cubing BAM SSIS packages is turned on and is stored in the msdb database. Overtime, this may result in a significant volume of SSIS event log data caused by large number of BAM activities or frequent execution of BAM owned SSIS packages. To resolve this, you can delete the old log entries because these entries are used primarily for debugging.

## Prerequisites

You must be logged on as a member of the BizTalk Server Administrators group to perform these procedures.

## Run the Cube Update Integration Services package

### BizTalk Server 2020 and newer

1.  Start **SQL Server Management Studio**.

2.  In the **Connect to server** dialog box, in the **Server type** drop-down list, select **Database Services**.

3.  In the **Server name** drop-down list, select the name of the server on which you are running the package.

4.  In the **Authentication** drop-down list, select the type of authentication that you are using to connect to the server.

5.  If necessary, type your user name and password.

6.  Click **Connect**.

7.  In the console tree, expand **Integration Services Catalogs** > **SSISDB** > **BizTalk Server** > **Projects** > **BAM_AN_\<View name\>** > **Packages**.

8.  Right-click the **BAM_AN_\<View name\>.dtsx** package, and then click **Execute...**.

### BizTalk Server 2016 and older

1.  Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP1** or **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.

2.  In the **Connect to server** dialog box, in the **Server type** drop-down list, select **Integration Services**.

3.  In the **Server name** drop-down list, select the name of the server on which you are running the package.

4.  In the **Authentication** drop-down list, select the type of authentication that you are using to connect to the server.

5.  If necessary, type your user name and password.

6.  Click **Connect**.

7.  In the console tree, expand **Integration Services** > **Stored Packages**, and then click **MSDB**.

8.  Right-click the **BAM_AN_\<View name\>** package, and then click **Run Package**.

## Run the Maintaining BAM Data Integration Services package

### BizTalk Server 2020 and newer

1.  Start **SQL Server Management Studio**.

2.  In the **Connect to server** dialog box, in the **Server type** drop-down list, select **Database Services**.

3.  In the **Server name** drop-down list, select the name of the server on which you are running the package.

4.  In the **Authentication** drop-down list, select the type of authentication that you are using to connect to the server.

5.  If necessary, type your user name and password.

6.  Click **Connect**.

7.  In the console tree, expand **Integration Services Catalogs** > **SSISDB** > **BizTalk Server** > **Projects** > **BAM_DM_\<Activity name\>** > expand **Packages**.

8.  Right-click the **BAM_DM_\<Activity name\>.dtsx** package, and then click **Execute...**.

    > [!div class="mx-imgBorder"]
    > ![Execute the BizTalk Server BAM activity in SQL Server Management Studio](../core/media/bam-dts-dm-execute.png)

### BizTalk Server 2016 and older

1.  Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP1** or **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.

2.  In the **Connect to server** dialog box, in the **Server type** drop-down list, select **Integration Services**.

3.  In the **Server name** drop-down list, select the name of the server on which you are running the package.

4.  In the **Authentication** drop-down list, select the type of authentication that you are using to connect to the server.

5.  If necessary, type your user name and password.

6.  Click **Connect**.

7.  In the console tree, expand **Integration Services** > **Stored Packages**, and then click **MSDB**.

8.  Right-click the **BAM_DM_\<Activity name\>** package, and then click **Run Package**.

## Schedule the packages to run regularly

1.  Open **SQL Server Management Studio**.

2.  In the **Connect to server** dialog box, in the **Server type** drop-down list, select **Database Engine**.

3.  In the **Server name** drop-down list, select the name of the server on which you are running the package.

4.  In the **Authentication** drop-down list, select the type of authentication that you are using to connect to the server.

5.  If necessary, type your user name and password.

6.  Click **Connect**.

7.  In the console tree, expand your server, and select **SQL Server Agent**.

8.  If **SQL Server Agent** is disabled, right-click **SQL Server Agent**, and then select **Start**.

9. Right-click **SQL Server Agent**, and select  **New Job**.

10. In the **New Job** dialog box, type a name for the job in the **Name** text box.

11. In the **Select a page** window, click **Steps**, and then click **New**. This opens the **New Job Step** dialog box.

12. In the **Step name** text box, type an identifying name for the step.

13. In the **Type** drop-down list, select **SQL Server Integration Services Package** and in the **Package source** drop-down list, select **SSIS Catalog**.
    For BizTalk Server 2016 and older, in the **Package source** drop-down list, select **SSIS Package Store**.

14. In the **Server** drop-down list, select the server on which you are running the job.

15. Click the file selector button for the **Package** text box, select the package you are scheduling (either the **BAM_DM_\<Activity name\>** or **BAM_AN_\<View name\>** package), and then click **OK**.

16. In the **Select a page** window, click **Schedules**, and then click **New**. This opens the **New Job Schedule** dialog box.

17. In the **Name** text box, type a name for the schedule.

18. Create your schedule using the frequency fields.

19. Click **OK** to save the job.

    > [!NOTE]
    >  If BAM is configured with a non-default instance of SQL Server, then the BAM_AN_POCube DTSPackage does not get scheduled/executed accurately. You need to modify the configuration file to allow packages to continue running. For more information, refer to the "Modifying the Contents of the Configuration File" section at [https://go.microsoft.com/fwlink/?LinkId=196768](/sql/integration-services/service/integration-services-service-ssis-service).

## See Also

 [Managing BAM Databases](../core/managing-bam-databases.md)
