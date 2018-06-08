# 从节点（Slave）是否会与其主节点（Master）一起保持最新状态？ {#concept_nd4_bs5_ydb .concept}

主节点（Master）的更新会自动复制到其关联的从节点（Slave）。不过，鉴于 Redis 的异步复制技术，出于各种原因，Slave 节点更新可能会落后于其 Master 节点。可能的原因包括，Master 节点的 I/O 写入量超过了 Slave 节点同步的速度；或者Master 节点和 Slave 节点之间有网络延迟。因此 Slave 节点与其 Master 节点之间可能存在滞后或在某一时候有一定程度上的数据不一致。

如果问题还未能解决，请联系[售后技术支持](https://selfservice.console.aliyun.com/ticket/createIndex.htm?spm=0.0.0.0.fwiOT5)。

