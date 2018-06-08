# Redis 集群如何使用 scan 命令? {#concept_pnz_lvz_xdb .concept}

Redis 集群不支持 scan 命令，您可以使用 ISCAN 命令, 它和 Redis 的 SCAN 命令的功能相同。ISCAN 命令的语法如下：

```
ISCAN idx cursor [MATCH pattern] [COUNT count]
```

idx 为节点的 id，从 0 开始。16 到 64 GB 的集群实例为 8 个节点，故 idx 为 0 到 7，128 到 256 GB 的集群实例为 16 个节点。

