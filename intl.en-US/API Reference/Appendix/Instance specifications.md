# Instance specifications {#reference_evw_z5x_wdb .reference}

## Types of ApsaraDB for Redis instances {#section_njr_vlz_xbb .section}

|Type|InstanceClass \(API used\)|Maximum number of connections|Maximum throughput \(MB\)|
|----|--------------------------|-----------------------------|-------------------------|
|256 MB master/slave|redis.master.micro.default|10000|10|
|1 GB master/slave|redis.master.small.default|10000|10|
|2 GB master/slave|redis.master.mid.default|10000|16|
|4 GB master/slave|redis.master.stand.default|10000|24|
|8 GB master/slave|redis.master.large.default|10000|24|
|16 GB master/slave|redis.master. 2xlarge.default|10000|32|
|32 GB master/slave|redis.master. 4xlarge.default|10000|32|
|1 GB master/slave \(advanced\)|redis.master.small.special2x|20000|48|
|2 GB master/slave \(advanced\)|redis.master.mid.special2x|20000|48|
|4 GB master/slave \(advanced\)|redis.master.stand.special2x|20000|48|
|8 GB master/slave \(advanced\)|redis.master.large.special1x|20000|48|
|16 GB master/slave \(advanced\)|redis.master. 2xlarge.special1x|20000|48|
|32 GB master/slave \(advanced\)|redis.master. 4xlarge.special1x|20000|48|

**Note:** The Pay-As-You-Go billing method does not support the 256 MB master/slave version.

|Type|InstanceClass \(API used\)|Maximum number of connections|Maximum throughput \(MB\)|
|----|--------------------------|-----------------------------|-------------------------|
|1 GB single-host|redis.basic.small.default|10000|10|
|2 GB single-host|redis.basic.mid.default|10000|16|
|4 GB single-host|redis.basic.stand.default|10000|24|
|8 GB single-host|redis.basic.large.default|10000|24|
|16 GB single-host|redis.basic. 2xlarge.default|10000|32|
|32 GB single-host|redis.basic. 4xlarge.default|10000|32|
|1 GB single-host \(advanced\)|redis.basic.small.special2x|20000|48|
|2 GB single-host \(advanced\)|redis.basic.mid.special2x|20000|48|
|4 GB single-host \(advanced\)|redis.basic.stand.special2x|20000|48|
|8 GB single-host \(advanced\)|redis.basic.large.special2x|20000|48|
|16 GB single-host \(advanced\)|redis.basic. 2xlarge.special2x|20000|48|
|32 GB single-host \(advanced\)|redis.basic. 4xlarge.special2x|20000|48|

**Note:** Regions outside China and financial regions do not support the single-host versions currently.

|Type|InstanceClass \(API used\)|Maximum number of connections |Maximum throughput \(MB\)|
|----|--------------------------|------------------------------|-------------------------|
|16 GB cluster|redis.sharding.small.default|80000|384|
|32 GB cluster|redis.sharding.small.default|80000|384|
|64 GB cluster|redis.sharding.large.default|80000|384|
|128 GB cluster|redis.sharding. 2xlarge.default|160000|768|
|256 GB cluster|redis.sharding. 4xlarge.default|160000|768|

|Type|InstanceClass \(API used\)|Maximum number of connections|Maximum throughput \(MB\)|
|----|--------------------------|-----------------------------|-------------------------|
|16 GB cluster \(single-host\)|redis.sharding.basic.small.default|80000|384|
|32 GB cluster \(single-host\)|redis.sharding.basic.mid.default|80000|384|
|64 GB cluster \(single-host\)|redis.sharding.basic.large.default|80000|384|
|128 GB cluster \(single-host\)|redis.sharding.basic. 2xlarge.default|160000|768|
|256 GB cluster \(single-host\)|redis.sharding.basic. 4xlarge.default|160000|768|

**Note:** 

Regions outside China and financial regions do not support the single-host versions currently.

## Types of ApsaraDB for Memcache instances {#section_vqs_1nz_xbb .section}

|Type|InstanceClass \(API used\)|
|----|--------------------------|
|1-core 1 GB|memcache.master.small.default|
|1-core 2 GB|memcache.master.mid.default|
|1-core 4 GB|memcache.master.stand.default|
|1-core 8 GB|memcache.master.large.default|
|2-core 16 GB|memcache.sharding.small.default|
|4-core 32 GB|memcache.sharding.mid.default|
|8-core 64 GB|memcache.sharding.large.default|
|16-core 128 GB|memcache.sharding. 2xlarge.default|
|16-core 256 GB|memcache.sharding. 4xlarge.default|

