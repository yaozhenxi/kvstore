# Use the redis-port tool to synchronize self-built redis RDB files to a cloud Database {#concept_xnh_dk1_wdb .concept}

## Download redis-Port { .section}

[Redis-port address](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/66008/cn_zh/1526545851725/redis-port)

## Using examples { .section}

```
. /Redis-port restore -- input = x/dump. RDB -- target = dst_host: dst_port -- auth = dst_password [-- filterkey = "str1 | str2 | str3"] [-- targetdb = dB] [-- rewrite] [-- bigkeysize = size] [-- logfile = redisport. log]
```

**Parameter descriptions**

-   X/dump. RDB: dump file path of self-built redis
-   Dst\_host: cloud database redis Domain Name
-   Dst\_port: cloud database redis Port
-   Dst\_password: cloud database redis Password
-   Str1 | str2 | str3: Filter key with str1 or str2 or str3
-   DB: dB to be synchronized into the cloud database redis
-   Rewrite: overwrites a key that has already been written
-   Bigkeysize = size: When write value is greater than size, go to Big key write mode

## Viewing data synchronization status according to redis-port log { .section}

![](images/2802_en-US.png)

The data synchronization completes when restore: RDB done appears.

