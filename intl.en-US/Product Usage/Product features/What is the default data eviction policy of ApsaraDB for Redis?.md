# What is the default data eviction policy of ApsaraDB for Redis? {#concept_e5v_hs5_ydb .concept}

ApsaraDB for Redis instances adopt the volatile-lru eviction policy by default. To change to another eviction policy, log on to the Redis console and click System Parameters.

-   **volatile-lru**

    Only old data with an expiration time is evicted in accordance with the LRU algorithm.

-   **volatile-ttl**

    Only data with an expiration time is evicted in an ascending order of TTL values.

-   **allkeys-lru**

    Old data is evicted in accordance with the LRU algorithm.

-   **volatile-random**

    Only old data with an expiration time is evicted randomly.

-   **allkeys-random**

    Old data is evicted randomly.

-   **noeviction**

    No data is evicted. An error message is returned when new data is written.


