# 为什么 ECS 连接不上 Redis? {#concept_m2x_pbz_xdb .concept}

两者通过内网连接必须满足的条件如下：

-   ECS 和 Redis 在相同的地域

-   ECS 和 Redis 在相同的网络环境，即：必须都属于经典网络或者同一个 VPC 下

-   ECS 内网 IP 在 Redis 白名单中


以下情况中，ECS 无法直接通过内网连接 Redis 数据库。

-   如果您的 ECS 和 redis 在不同地域的 VPC 中，内网是不通的。在不同地域下的 ECS 连接 Redis，目前只能通过高速通道实现跨 VPC 的内网访问，详情参见 [跨地域 VPC 互连](https://help.aliyun.com/document_detail/44842.html)。

-   如果您的 ECS 和 redis 属于不同的网络类型，您可以通过如下方法来解决：

    -   如果可以接受转换为 VPC 网络类型，请参考[切换为专有网络](../cn.zh-CN/用户指南/管理实例/切换为专有网络.md#)或者[迁移方案概述](https://help.aliyun.com/document_detail/55051.html)。

    -   如果不接受转化为 VPC，您需要重新购买同一地域下、同属经典网络的 ECS 和 Redis。


