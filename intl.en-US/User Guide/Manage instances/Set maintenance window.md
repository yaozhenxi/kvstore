# Set maintenance window {#concept_sjv_kpl_vdb .concept}

## Background {#section_mxr_3ql_vdb .section}

To guarantee the stability of ApsaraDB for Redis instances, the backend system irregularly maintains instances and machines on the Alibaba Cloud platform.

Before the official maintenance, ApsaraDB for Redis sends SMS messages and emails to contacts configured in your Alibaba Cloud account.

To guarantee the stability during maintenance process, instances enter the **Being Maintained** state before the preset O&M time on the day of maintenance. When an instance is in this state, the normal access to data in the database is not affected. However, change-related functions \(for example, configuration change\) are temporarily unavailable for this instance on the console, whereas query functions such as performance monitoring are still available.

**Note:** After the preset maintenance window time is reached, instances may experience intermittent interruption during maintenance, so we recommend that instances be maintained during off-peak hours if possible.

## Procedure { .section}

1.  Log on to the [Redis console](https://kvstore.console.aliyun.com/) and find the target instance.
2.  Click **Instance ID** or **Manage** to go to the Instance Information page.
3.  Click **Set** next to **Maintenance Window** in Basic Information, as shown in the following figure.

    The default maintenance window for ApsaraDB for Redis  is from 02:00 to 06:00.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/3144/2169_en-US.png)

4.  Select an maintenance window and click **Save**.

    **Note:** The time period is Beijing time.


