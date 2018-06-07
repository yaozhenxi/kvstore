# DescribeInstances {#reference_d5w_1df_xdb .reference}

## 描述 {#section_z1z_2kw_wbb .section}

查询账户下的某一个或多个实例信息。

## 请求参数 {#section_fn4_gkw_wbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共请求参数](cn.zh-CN/API 参考/公共参数.md#section_hph_dhp_wbb)。|
|Action|String|是|操作接口名，取值：DescribeInstances。|
|InstanceIds|String|否|实例 ID（全局唯一）。指定实例 ID 时需输入。若查询多个实例 ID 时，使用英文半角逗号（“,”）分隔各 ID；置空时默认为查询该用户名下所有实例。|
|InstanceStatus|String|否| 按状态过滤所需返回的实例：

 -   Normal：正常
-   Creating：创建中
-   Changing：修改中
-   Inactive：被禁用

 |
|ChargeType|String|否|按付费类型过滤所需返回的实例：-   PrePaid：预付费
-   PostPaid：后付费

 |
|RegionId|String|是|调用 DescribeRegions 查询 RegionId。|
|InstanceType|String|否|引擎类型的过滤。-   Memcache：Memcache 类型的实例
-   Redis：Redis 类型的实例

|
|PageNumber|Integer|否|实例状态列表的页码，起始值为1，默认值为1。|
|PageSize|Integer|否|分页查询时设置的每页行数，最大值50行，默认值为10。|
|NetworkType|String|否|按网络类型过滤：-   CLASSIC：经典网络类型
-   VPC：VPC 网络类型

|

## 返回参数 {#section_e4w_jkw_wbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|参见[公共返回参数](cn.zh-CN/API 参考/公共参数.md#section_rjr_zgp_wbb)。|
|Instances|List|由 Instance 组成的数组。|
|TotalCount|Integer|实例总个数|
|PageNumber|Integer|实例列表的页码|
|PageSize|Integer|输入时设置的每页行数|

## Instance 的参数构成 {#section_f2s_tpw_wbb .section}

|名称|类型|描述|
|--|--|--|
|InstanceId|String|实例 ID （全局唯一）|
|InstanceName|String|实例名称|
|Capacity|Long|申请到的存储实例容量； 单位：MB。|
|InstanceClass|String|实例规格信息|
|Bandwidth|Long|实例带宽限制；单位：Mbps。|
|Connections|Long|实例连接数限制；单位：个。|
|ConnectionDomain|String|实例连接域名（仅支持内网访问。）|
|Port|Int|连接端口|
|UserName|String|连接用户名|
|RegionId|String|申请的存储实例所在区域|
|ZoneId|String|RegionId 下的可用区编码|
|InstanceStatus|String|实例状态：-   Normal：正常
-   Creating：创建中
-   Changing：修改中
-   Inactive：被禁用
-   Transforming：转换中
-   BackupRecovering：备份恢复中
-   MinorVersionUpgrading：实例小版本升级中

|
|ChargeType|String|付费类型：PrePaid 或 PostPaid|
|CreateTime|String|实例创建时间。采用ISO8601 表示法，并使用 UTC 时间。格式为：`YYYY-MM-DDThh:mm:ssZ`。|
|EndTime|String|预付费实例到期时间。采用ISO8601 表示法，并使用 UTC 时间。格式为： `YYYY-MM-DDThh:mm:ssZ`。|
|NetworkType|String|网络类型：CLASSIC 或 VPC|
|VpcId|String|VPC 的 ID|
|VSwitchId|String|虚拟交换机 ID|
|PrivateIpAddr|String|私有 IP 地址|

**说明：** 出于历史兼容性考虑，该函数会有些返回结构在文档中并未提及（如 Config），后续阿里云将逐步把这些字段删除，请您在调用 API 时不要依赖这些在文档中没有涉及的返回字段。

## 请求示例 {#section_d3l_4kw_wbb .section}

```
https://r-kvstore.aliyuncs.com.com/
?<公共请求参数>
&Action=DescribeInstances
&PageNumber=1
&PageSize=10
&InstanceId=de5d88e34d004211
```

## 返回示例 {#section_hjp_tkw_wbb .section}

```
{
    "Instances" : {
        "Instance" : [{
                "Bandwidth" : 128,
                "Capacity" : 512,
                "ConnectionDomain" : "de5d88e34d004211.m.cnhzalicm10pub001.r-kvstore.aliyuncs.com.com",
                "Connections" : 300,
                "ZoneId" : "cn-qingdao-b",
                "InstanceId" : "de5d88e34d004211",
                "InstanceName" : "wl123456",
                "InstanceStatus" : "Available",
                 "InstanceClass" : "redis.master.mid.default",
                "Port" : 11211,
                "RegionId" : "cn-qingdao",
                "UserName" : "de5d88e34d004211"
                “NetworkType”:”CLASSSIC”
“ChargeType”:” PostPaid”
            }
        ]
    },
    "PageNumber" : 1,
    "PageSize" : 10,
    "TotalCount" : 1,
    "RequestId" : "969D0A1D-C91A-4837-9F70-49785DF9BDCE"
}
```

