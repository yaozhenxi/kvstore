# DescribeRegions {#reference_yrv_cv2_xdb .reference}

## 描述 {#section_z1z_2kw_wbb .section}

用来查询可创建实例的数据中心（Region）。

## 请求参数 {#section_fn4_gkw_wbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|是|参见[公共请求参数](cn.zh-CN/API 参考/公共参数.md#section_hph_dhp_wbb)。|
|Action|String|是|系统规定参数，取值： DescribeRegions。|
|AcceptLanguage|String|否|系统规定参数，取值： zh-CN 或 en-US 或 ja 三者之一，分别表示：中文、英文、日语，如参数值错误或为空，默认为英文。如不填写该参数，则向旧API保持兼容，默认为中文|

## 返回参数 {#section_e4w_jkw_wbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|参见[公共返回参数](cn.zh-CN/API 参考/公共参数.md#section_rjr_zgp_wbb)。|
|RegionIds|List|RegionIds 为一个 List，里面每个元素由两部分组成：RegionId、 ZoneIds，其中的 ZoneIds 也是一个 String，多个 ZoneId 用“,”分隔。|

## 请求示例 {#section_d3l_4kw_wbb .section}

```
https://r-kvstore.aliyuncs.com、
?<公共请求参数>
&Action=DescribeRegions
```
或 https://r-kvstore.aliyuncs.com、
?<公共请求参数>
&Action=DescribeRegions&AcceptLanguage=en-US
```

## 返回示例 {#section_hjp_tkw_wbb .section}

```
{
    "RequestId":"535A88D3-5408-4B29-AFD4-07319D97EBC4",
    "RegionIds":
    {
                {
                    "RegionId": "eu-central,
                    "ZoneIdList": [
                        "eu-central-a",
                        "eu-central-b"
                    ],
                    "RegionEndpoint": "xxxyyyy.aliyuncs.com",
                    "ZoneIds": "eu-central-a,eu-central-b",
                    "LocalName": "德国（法兰克福）"
                },
              {
                "RegionId": "cn-chengdu-1",
                "ZoneIdList": [
                  "cn-chengdu-a"
                ],
                "RegionEndpoint": "xxxxx.aliyuncs.com",
                "ZoneIds": "cn-chengdu-xa",
                "LocalName": "西南（成都）"
              },
    }
}
```

