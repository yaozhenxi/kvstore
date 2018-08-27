# Set the network type {#concept_mtb_nz5_tdb .concept}

## Background {#section_snh_bbg_vdb .section}

ApsaraDB supports two types of network: classic and Virtual Private Cloud \(VPC\), a classic network and VPC have following differences:

-   **Classic network**: The cloud services on a classic network are not isolated, and unauthorized access to a cloud service is blocked only by the security group or whitelist policy of the service.

-   **VPC**: The VPC helps you build an isolated network environment on Alibaba Cloud. You can customize the route table, IP address range, and gateway in VPC. In addition, you can combine your machine room and cloud resources in the Alibaba Cloud VPC into a virtual machine room through a leased line or VPN to migrate applications to the cloud smoothly.      


## Note: {#section_g2p_2bg_vdb .section}

-   A classic network can be switched to VPC, but not vice versa.

-   When switching the classic network to VPC, you can choose to retain the classic network IP address. 


## Prerequisites {#section_vnh_bbg_vdb .section}

To switch a classic network type Redis instance to a VPC network type instance, you should firstly create a VPC and a switch in the same region of the instance.

**Note:** 

Choose the same zone as the Redis instance when creating a switch.

## Procedure {#section_gfs_hbg_vdb .section}

1.  Log on to  [Redis Console](https://kvstore.console.aliyun.com/),  find the target instancen, and click **Manage**.
2.  Click **Switch to VPC** on the Instance Information page.
3.  On the Switch to VPC page, select **VPC** and **VSwitch**. Select **whether to retain the classic network IP address** and the **retention period**, and then click **OK**.

    **Note:** 

    On the **Instance Information** page, Click **Refresh** to view the access address.


