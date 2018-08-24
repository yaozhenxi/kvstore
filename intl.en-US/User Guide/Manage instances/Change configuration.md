# Change configuration {#concept_mgf_z25_tdb .concept}

Alibaba Cloud ApsaraDB for Redis provides two billing methods: Monthly/annually payment and pay-by-flow method. The latter can be converted to the former. The configuration of the two mode can be changed.

## Background { .section}

Changing the instance configuration incurs a change in charges. For more information about the billing standard, see [ApsaraDB for Redis pricing](https://www.aliyun.com/price/product?#/kvstore/detail).

## Attention {#section_jnl_v1g_vdb .section}

-   Pay-As-You-Go and Subscription instances both support real-time configuration changes.
-   Cluster instances and non-cluster instances can be switched between each other.
-   During the configuration change, the instance may be disconnected for a few seconds. Please change the configuration during off-peak hours.

## Change the configuration of a Pay-As-You-Go instance {#section_icq_j1g_vdb .section}

1.  Log on to the [Redis console](https://kvstore.console.aliyun.com/).
2.  Locate the target instance in the instance list. Click **Change Configurations** in the Action column.
3.  On the Upgrade page, change the configuration and click **Activate**.

    It notifies the user with a successful resetting and takes an immediate effect upon resetting configuration. \(Pay by new mode at once\)


## Change the configuration of a Subscription instance {#section_tbd_f1g_vdb .section}

1.  Log on to the [Redis console](https://kvstore.console.aliyun.com/).
2.  Locate the target instance in the instance list. Click **Upgrade** or **Downgrade** in the Action column.
3.  On the **Upgrade** page, change the configuration and click **Pay**.
4.  Review the order information and click **Pay**.

    The proedure ends.


