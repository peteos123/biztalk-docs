---
title: "Checklist: Maintain and Troubleshoot BizTalk Server Databases"
description: See the best practices to help maintain your BizTalk Server databases, including Auto Update Statistics, Max Degree of Parallelism, rebuild indexes, look for locks and blocks, check the database sizes, use tracking, enable the SQL Server Agent jobs, check for suspended instances, and check for disk performance. Also read about the BizTalk Terminator tool.
ms.custom: ""
ms.date: "06/11/2018"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: checklist
---

# Checklist: Maintaining and Troubleshooting BizTalk Server Databases
BizTalk Server databases and their health are very important for a successful BizTalk Server database messaging environment. This topic lists the steps that you must follow when maintaining or troubleshooting the BizTalk Server databases.

- [Maintaining BizTalk Server Databases](#maintaining-biztalk-server-databases)

- [Troubleshooting BizTalk Server Databases](#troubleshooting-biztalk-server-databases)

## Maintaining BizTalk Server Databases

- Disable the **Auto Update Statistics** and **Auto Create Statistics** options (applies only to BizTalk Server MessageBox databases). By default, these settings are configured as part of the BizTalk Server configuration. You should not make changes to these settings.

  To see if these settings are disabled, execute the following stored procedures in SQL Server:  

  ```sql
  SELECT DATABASEPROPERTYEX('BizTalkMsgBoxDB', 'IsAutoCreateStatistics') AS IsAutoCreateStatistics
  SELECT DATABASEPROPERTYEX('BizTalkMsgBoxDB', 'IsAutoUpdateStatistics') AS IsAutoUpdateStatistics
  ```

  The values returned should be **0** to indicate the setting is disabled. If **0** is not returned, disable the setting by executing the following in SQL Server:

  ```sql
  ALTER DATABASE BizTalkMsgBoxDB SET AUTO_CREATE_STATISTICS OFF
  ALTER DATABASE BizTalkMsgBoxDB SET AUTO_UPDATE_STATISTICS OFF
  ```

  For more information about these settings, go to [You experience blocking, deadlock conditions, or other SQL Server issues when you try to connect to the BizTalkMsgBoxDb database in BizTalk Server](/troubleshoot/biztalk/biztalkmsgboxdb-connection-issue).

- Set the Max Degree of Parallelism property. By default, this settings is configured as part of the BizTalk Server configuration. You should not make changes to these settings.

  Set the Max Degree of Parallelism **run_value** and **config_value** properties to a value of one (1) on the SQL Server instances that host the BizTalk Server MessageBox databases. To check the Max Degree of Parallelism setting, execute the following stored procedure against the Master database in SQL Server:

  ```sql
  exec sp_configure 'max degree of parallelism'
  ```

  If the **run_value** and **config_value** are not set to a value of one (1), execute the following stored procedure in SQL Server:

  ```sql
  exec sp_configure 'max degree of parallelism', '1' reconfigure with override
  ```

  For more information about how the Max Degree of Parallelism setting affects BizTalk Server, go to [You experience blocking, deadlock conditions, or other SQL Server issues when you try to connect to the BizTalkMsgBoxDb database in BizTalk Server](/troubleshoot/biztalk/biztalkmsgboxdb-connection-issue).

- Determine when you can rebuild BizTalk Server indexes.

  Most of the indexes in BizTalk Server databases are clustered (index ID: 1). The DBCC SHOWCONTIG command can be used to display fragmentation information for tables in the BizTalk Server databases. These indexes are GUID-based so it is normal for fragmentation to occur. If the Scan Density value of DBCC SHOWCONTIG is less than 30%, the indexes can be rebuilt during downtime. Many tables in the BizTalk Server databases contain columns that use DataType definitions where online indexing cannot be done. Therefore, the indexes for tables in the BizTalk Server databases should never be rebuilt while BizTalk is processing data.

  For more information on how to rebuild the BizTalk indexes, go to [You experience blocking, deadlock conditions, or other SQL Server issues when you try to connect to the BizTalkMsgBoxDb database in BizTalk Server](/troubleshoot/biztalk/biztalkmsgboxdb-connection-issue).

  You can also use the sys.dm_db_index_physical_stats function to look for fragmentation information in SQL Server. For more information, see [sys.dm_db_index_physical_stats (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql).

- Monitor the database for locks, blocks, or deadlocks.

  It is an expected behavior for locks and blocks to occur on the SQL Server databases used by BizTalk Server. However, it is not expected to have these locks or blocks to continue for an extended period of time. Extended blocking and deadlocking on the SQL Server databases used by BizTalk Server are indicators of a potential problem. 

  For the current known causes of deadlocking and blocking on the SQL Server databases used by BizTalk Server, go to [You experience blocking, deadlock conditions, or other SQL Server issues when you try to connect to the BizTalkMsgBoxDb database in BizTalk Server](/troubleshoot/biztalk/biztalkmsgboxdb-connection-issue).

- Monitor the size of databases and tables.

  The size of the BizTalk Server MessageBox database should typically be no more than approximately 5GB.  The BizTalkMsgBoxDb database should not be holding any data, and should be considered a buffer until the data is processed or moved to the BizTalkDTADb database. An environment with a powerful SQL Server backend and numerous long running orchestrations may have a BizTalkMsgBoxDb database larger than 5GB. A high volume environment with no long-running orchestrations should have a BizTalk Server MessageBox database much smaller than 5GB. 

  The BizTalk Server tracking database can vary greatly in size but if query performance decreases dramatically, then the tracking database is probably too large. As a rule of thumb, a BizTalk Server tracking database larger than 15-20 GB is considered too large and may adversely impact performance.

  The following issues may be attributable to BizTalk Server databases that are too large:

  - The BizTalk Server MessageBox database continues to grow while the data size (not just the log file) remains large. BizTalk Server takes a longer time than normal to process even a simple message flow scenario.
  - Group Hub queries take a longer time than normal and may even timeout.
  - The database log file never gets truncated.
  - The BizTalk SQL Agent jobs run slower than normal.
  - Some tables are considerably large or have too many rows compared to normal.

  The BizTalk Server databases can become large for several reasons including:

  - BizTalk SQL Agent Jobs not running
  - Excessive suspended message or service instances
  - Disk failures
  - High levels of tracking
  - BizTalk Server throttling
  - Poor SQL Server performance
  - Network latency issues

  Similarly, you can have too many rows in a table. There is no set number of rows that are too many. Additionally, this number of rows varies by what kind of data is stored in the table. For example, a **dta_DebugTrace** table that has more than 1 million rows probably has too many rows. A **HostNameQ_Suspended** table that has more than 200,000 rows probably has too many rows.

  Make sure that you know what is expected in your environment to determine whether a data issue is occurring.

- Enable tracking on BizTalk Server host.

  By default, tracking is enabled on the default host. BizTalk requires the **Allow Host Tracking** option be checked on a single host. When tracking is enabled, the Tracking Data Decode Service (TDDS) moves the tracking event data from the BizTalk Server MessageBox database to the BizTalk Server tracking database. If no BizTalk Server hosts are configured with the option to **Allow Host Tracking** or if the tracking host is stopped, then TDDS will not run and the TrackingData_x_x tables in the BizTalk Server MessageBox database will grow unchecked. 

  Therefore, a dedicated BizTalk Server host should be configured with the option to **Allow Host Tracking**. For more information about configuring a dedicated tracking host see [Configuring a Dedicated Tracking Host](configuring-a-dedicated-tracking-host.md).

  To allow TDDS to maintain new tracking events in high volume scenarios, you can create multiple instances of a single tracking host but no more than one host should be configured for tracking.

- Use the correct BizTalk SQL Server Agent jobs.

  Execution of the BizTalk Server SQL Agent jobs are crucial for managing the BizTalk Server databases and for maintaining optimal performance.

  - The  **Backup BizTalk Server** SQL Server Agent job is the only supported method to back up the BizTalk Server databases. This job requires you to set up all BizTalk Server databases to use a Full Recovery Model. You should configure this job for a healthy BizTalk Server environment. You can use the SQL Server methods to back up the BizTalk Server databases only if the SQL Server service is stopped and if all BizTalk Server processes are stopped.

    For more information about using the SQL Server full recovery model when configuring the SQL Agent Backup BizTalk Server job, see [Log Shipping](../core/log-shipping.md) or [Backup Under the Full Recovery Model](/sql/relational-databases/backup-restore/complete-database-restores-full-recovery-model).

  - The **MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb** SQL Server Agent job is designed to run indefinitely. As a result the SQL Agent job history may not indicate that this SQL Agent job has successfully completed; this behavior is by design. If there is a failure, the job will restart within 1 minute and continue running unabated. Therefore, failure notifications for this job can typically be ignored.

    If the job history for the MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb SQL Server Agent job indicates that this job is constantly failing and restarting then further investigation into the cause of the failure/restart cycle may be required.

  - The **MessageBox_Message_Cleanup_BizTalkMsgBoxDb** SQL Server Agent job is the only job that should not be manually enabled because it is initiated by the MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb job.

  - The **DTA Purge and Archive** SQL Server Agent job maintains the BizTalk Server tracking database by purging and archiving tracked messages. This job reads every row in the table and compares the timestamp of each row to determine if the record should be removed.

    When troubleshooting the BizTalk Server SQL Server Agent jobs, verify that all SQL Agent jobs except the MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb are completing without errors.

  For more information about the BizTalk Server SQL Agent Jobs used in SQL Server:

  - [Database Structure and Jobs](../core/database-structure-and-jobs.md)
  - [Description of the SQL Server Agent jobs in BizTalk Server](/troubleshoot/biztalk/sql-server-agent-jobs-biztalk)

- Monitor and terminate suspended instances.

  Service instances can be suspended (resumable) or suspended (not resumable). These service instances may be Messaging, Orchestration, or Port. BizTalk Server accommodates termination and removal of these instances by using the Group Hub page in the BizTalk Server Administration Console or through the use of the Terminate.vbs script. For more information about the Terminate.vbs script, see [Removing Suspended Service Instance](/biztalk/core/technical-reference/removing-suspended-service-instances).

  You can also use the Terminator tool to remove suspended instances. The Terminator tool is included with the [BizTalk Health Monitor](../core/monitoring-biztalk-server.md).

  The terms "orphans” and "zombies" are often used interchangeably. An orphaned or zombie message is a message that does not have an associated service instance, typically because the service instance has terminated before the message was received. An orphaned or zombie service is a service that does not have any associated messages. For more information about zombie messages and service instances in BizTalk Server see [Zombies in BizTalk Server](../core/zombies-in-biztalk-server.md).

- Monitor the performance counters of the **PhysicalDisk** performance object.

  BizTalk Server makes a large number of short, very quick transactions to SQL Server within one minute. If the SQL Server cannot sustain this activity, you may experience BizTalk Server performance issues. Monitor the **Avg. Disk sec/Read**, **Avg. Disk sec/Transfer**, and **Avg. Disk sec/Write** performance monitor counters in the **PhysicalDisk** performance object. The optimal value is less than 10 ms (milliseconds). A value of 20 ms or larger is considered poor performance.

  For more information about BizTalk Server database high availability, see [Providing High Availability for BizTalk Server Databases](../core/providing-high-availability-for-biztalk-server-databases.md).

- Follow best practices for BizTalk Server databases. See [Best Practices for Maintaining BizTalk Server Databases](best-practices-for-maintaining-biztalk-server-databases.md).

## Troubleshooting BizTalk Server Databases

Perform the following tasks to troubleshoot any issues with BizTalk Server databases.

- Ensure all required BizTalk SQL Server Agent jobs are enabled and running.

  All the BizTalk SQL Server Agent jobs except the **MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb** job should be enabled and running successfully. Do not disable any other job.<br /><br /> If a failure occurs, use the **View History** option in SQL Server to view the error information, and then troubleshoot the failure accordingly. Remember that the **MessageBox _Message_ManageRefCountLog_BizTalkMsgBoxDb** SQL Server Agent job runs infinitely. Therefore, you should only be concerned if the job history reports that the job constantly fails and restarts.

- Use the MsgBoxViewer tool to analyze the BizTalk MessageBox and other databases.

  The MsgBoxViewer tool is included with the [BizTalk Health Monitor](../core/monitoring-biztalk-server.md). The MsgBoxViewer tool is useful for troubleshooting because it provides an HTML report that has detailed information about table sizes and the row count. The report can also help determine whether BizTalk Server is throttling. Additionally, the tool provides a snapshot of the BizTalk Server databases and the BizTalk Server configuration.

  When BizTalk Server is running slower than usual, run the MsgBoxViewer tool, click to select all queries on the **Optional Queries** tab, and then review the generated HTML report for any problems. The **Summary Report** section lists warnings in yellow and potential problems in red.

  Additionally, you can use the MsgBoxViewer tool to determine which tables are the largest and have the most records. For a list of tables that typically grow the larges and for instructions on how to manage those tables, see [Large-growing BizTalk Server Database Tables](large-growing-biztalk-server-database-tables.md).

- Use the Terminator tool to resolve issues, if any, identified by the MsgBoxViewer tool.

  The Terminator tool is included with the [BizTalk Health Monitor](../core/monitoring-biztalk-server.md). This tool enables users to easily resolve any issues identified by the BizTalk MsgBoxViewer tool.

- Investigate deadlock scenarios.

  In a deadlock scenario, enable DBCC tracing on the SQL Server so that the deadlock information is written to the SQLERROR log. In SQL Server, execute the following statement to enable DBCC tracing for deadlock scenarios:

  ```sql
  DBCC TRACEON (1222,-1)
  ```

  You can also use the PSSDIAG utility to collect data on the **Lock:Deadlock** event and the **Lock:Deadlock Chain** event. For more information, see [PSSDIAG data collection utility](https://support.microsoft.com/topic/pssdiag-data-collection-utility-513a299f-0b45-eb1a-adb4-bc2ad8ecf194).

  The BizTalkMsgBoxDB database is a high-volume and high-transaction Online Transaction Processing (OLTP) database. With such databases, some deadlocking is expected and this deadlocking is handled internally by the BizTalk Server engine. When this behavior occurs, no errors are listed in the error logs. When you investigate a deadlock scenario, the deadlock that you are investigating in the output must be correlated with a deadlock error in the event logs.

- Look for blocked processes.

  You can use Activity Monitor in SQL Server to obtain the server process identifier (SPID) of a locking system process. You can then run the SQL Profiler to determine the SQL statement that is executing in the locking SPID. You can use the PSSDIAG utility to troubleshoot locking and blocking issues in SQL Server. The utility captures all the Transact-SQL events that have the blocking script enabled. For more information, see [PSSDIAG data collection utility](https://support.microsoft.com/topic/pssdiag-data-collection-utility-513a299f-0b45-eb1a-adb4-bc2ad8ecf194)

  In SQL Server, you can specify the **blocked process threshold** setting to determine which SPID or SPIDs are blocking longer than the threshold that you specify. For more information about the blocked process threshold option, see [blocked process threshold Option](/sql/database-engine/configure-windows/blocked-process-threshold-server-configuration-option).

  When you experience a locking or blocking issue in SQL Server, you can contact Microsoft Customer Support Services.

- Delete all unwanted data.

  If the databases have grown to become too large and if the data contained in the databases will not be required any longer, the preferred method is to delete the data. **Caution:**  Do not use this method in any environment where the data is business critical or if the data is needed.

  **To purge the BizTalkMsgBox database**:

  1. Download and install the Terminator tool, which is included in the [BizTalk Health Monitor](../core/monitoring-biztalk-server.md).
  2. Follow the steps in the topic [How to Manually Purge Data from the MessageBox Database in a Test Environment](../core/how-to-manually-purge-data-from-the-messagebox-database-in-a-test-environment.md) to create the bts_CleanupMsgbox stored procedure in the BizTalk MessageBox database.
  3. Use the Terminator tool to execute the bts_CleanupMsgbox stored procedure and purge the BizTalk MessageBox database.

      The bts_CleanupMsgbox stored procedure deletes data. Be careful when running this stored procedure in a production environment.

  4. Restart all hosts and BizTalk Server services.

  **To purge the BizTalkDTADb database**:

  - **Method 1**
    1. Back up all BizTalk Server databases.
    2. Execute the **dtasp_PurgeAllCompletedTrackingData** stored procedure. For more information about the stored procedure, see [How to Manually Purge Data from the BizTalk Tracking Database](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md).

  - **Method 2**: Use this option only if the BizTalkDTADb database contains many incomplete instances that must be removed.
    1. Back up all BizTalk Server databases.
    2. Stop all BizTalk hosts, services, and custom isolated adapters. If you use HTTP or the SOAP adapter, restart the IIS services.
    3. Execute the **dtasp_CleanHMData** stored procedure on the BizTalkDTADb database.
    4. Restart all hosts and BizTalk Server services.

  If you must have the tracking data, back up the BizTalkDTADb database, restore the database to another SQL Server, and then purge the original BizTalkDTADb database.

If you want help analyzing the MsgBoxViewer data or PSSDIAG output, contact Microsoft Customer Support Services. Before you contact Customer Support Services, compress the MsgBoxViewer data, the PSSDIAG output, and the updated event logs (.evt files). You may have to send these files to a BizTalk Server support engineer.

## Next

- [Best Practices for Maintaining BizTalk Server Databases](best-practices-for-maintaining-biztalk-server-databases.md)

- [Large-growing BizTalk Server Database Tables](large-growing-biztalk-server-database-tables.md)

- [Tools and Utilities for Troubleshooting](tools-and-utilities-for-troubleshooting.md)

## See Also

[SQL Server Settings That Should Not Be Changed](sql-server-settings-that-should-not-be-changed.md)
