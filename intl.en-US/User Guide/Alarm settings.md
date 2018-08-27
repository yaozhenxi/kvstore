# Alarm settings {#concept_sj5_m2z_5db .concept}

## Background information {#section_gp1_cff_vdb .section}

ApsaraDB for Redis provides an instance monitoring function and sends an SMS message to you when detecting an instance exception.

Monitoring and alarming are implemented through CloudMonitor. CloudMonitor enables you to set metrics and notify all contacts in the alarm contact group when the alarm policies of the metrics are triggered. You can maintain an alarm contact group corresponding to an alarm metric so that relevant contacts are promptly notified when an alarm occurs.

## Procedure {#section_yx2_2ff_vdb .section}

1.  Log on to the [Redis console](https://kvstore.console.aliyun.com/) and find the target instance.
2.  Click the instance ID or **Manage** to go to the **Instance Information** page.
3.  Select **Alarm Settings** in the left-side navigation pane.
4.  Click **Alarm Settings** to go to the CloudMonitor console. You can click **Refresh** to manually refresh the current status of the monitoring metrics.
5.  Select**Alarm Rules** \> **Create Alarm Rule**.
6.  Add alarm rules on the **Batch Alarm Rule Settings** page.
7.  Click **Next** to set the notification object. You can click **Quickly Create a Contact Group** to create an alarm contact or alarm contact group.
8.  Click **Confirm** and then click **Close**.

    **Note:** 

    After the alarm setting is completed, you can modify, disable, and delete alarm rules on the Alarm Rules page of the CloudMonitor console. You can also view the alarm history on this page.


