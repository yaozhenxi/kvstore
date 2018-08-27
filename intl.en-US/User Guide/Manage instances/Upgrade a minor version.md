# Upgrade a minor version {#concept_itn_f44_tdb .concept}

## Background { .section}

Deep kernel optimization is performed on ApsaraDB for Redis to fix security vulnerabilities and improve the stability of service. You can upgrade to the latest kernel version in one click on the console.

**Note:** 

-   The system automatically detects the kernel version of your instance. If the current version is the latest, the Basic Information page of the console does not show the **Upgrade Minor Version** button.
-   Upgrading the kernel version interrupts your connection for 30 seconds, so perform upgrade during off-peak hours and make sure your applications have a reconnection mechanism.

## Procedure { .section}

1.  Log on to the [Redis console](https://kvstore.console.aliyun.com/) and find the target instance.
2.  Click the instance ID or **Manage** to go to the Instance Information page.
3.  Click **Upgrade Minor Version** in the Basic Information column.

4.  Click **Upgrade Now** in the Upgrade Minor Version window.

    On the Basic Information page, the instance status shows **Upgrading minor version…** . Upgrade is completed when the instance status shows **In use**.


