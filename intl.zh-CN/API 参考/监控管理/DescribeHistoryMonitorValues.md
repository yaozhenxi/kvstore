# DescribeHistoryMonitorValues {#reference_nyv_gcf_xdb .reference}

## 描述 {#section_z1z_2kw_wbb .section}

查看实例的历史的监控信息。

## 请求参数 {#section_fn4_gkw_wbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|是|参见[公共请求参数](intl.zh-CN/API 参考/公共参数.md#section_hph_dhp_wbb)。|
|Action|String|是|系统规定参数，取值：DescribeHistoryMonitorValues。|
|InstanceId|String|是|实例 ID|
|StartTime|String|是|历史监控开始时间点；采用ISO8601 表示法，并使用 UTC 时间。格式为：`YYYY-MM-DDThh:mm:ssZ`。|
|EndTime|String|是|历史监控结束时间点；采用ISO8601 表示法，并使用 UTC 时间。格式为： `YYYY-MM-DDThh:mm:ssZ`。 EndTime 必须大于等于 StartTime。|
|IntervalForHistor|String|是|历史监控数据间隔，单位m（分钟）。取值 01m、05m、15m 或 60m。|
|MonitorKeys|String|否|监控项Key。通过函数DescribeMonitorItems查询。|

## 返回参数 {#section_e4w_jkw_wbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|参见[公共返回参数](intl.zh-CN/API 参考/公共参数.md#section_rjr_zgp_wbb)。|
|MonitorHistory|String| 以 JSON 格式返回的监控信息。返回的监控项，参见[查看监控项列表](intl.zh-CN/API 参考/监控管理/DescribeMonitorItems.md#)。

 **说明：** 为了提高数据传输效率，只有非0的监控数据才会返回，其余未显示给出的监控数据均为默认值0。

 |

## 请求示例 {#section_d3l_4kw_wbb .section}

```
https://r-kvstore.aliyuncs.com、
?<公共请求参数>
&Action= DescribeHistoryMonitorValues
&InstanceId= de5d88e34d004211
&EndTime=2014-11-27T12%3A02%3A00Z
&StartTime=2014-11-27T12%3A00%3A00Z
&IntervalForHistory=01m
```

## 返回示例 {#section_hjp_tkw_wbb .section}

```
{
"MonitorHistory" :
"{"2014-11-27T12:00:00Z":{"IsConnectControl":false,"IsFlowControl":false,"ItemCount":1,"QuotaConnection":500,"QuotaFlow":15360,"QuotaMemCache":1073741824,"QuotaQps":9000,"UsedMemCache":14},
"2014-11-27T12:01:00Z":{"IsConnectControl":false,"IsFlowControl":false,"ItemCount":1,"QuotaConnection":500,"QuotaFlow":15360,"QuotaMemCache":1073741824,"QuotaQps":9000,"UsedMemCache":14},
"2014-11-27T12:02:00Z":{"IsConnectControl":false,"IsFlowControl":false,"ItemCount":1,"QuotaConnection":500,"QuotaFlow":15360,"QuotaMemCache":1073741824,"QuotaQps":9000,"UsedMemCache":14}
}",
"RequestId" : "5C97648D-C85F-4D58-A71F-7B6750856BF7"
}
```

