# ModifyInstanceSpec {#reference_fmf_4yx_wdb .reference}

## 描述 {#section_z1z_2kw_wbb .section}

变更实例规格。实例规格请参见附录中的实例规格表。

## 请求参数 {#section_fn4_gkw_wbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|是|参见[公共请求参数](cn.zh-CN/API 参考/公共参数.md#section_hph_dhp_wbb)。|
|Action|String|是|操作接口名，取值：ModifyInstanceSpec。|
|InstanceId|String|是|实例 ID（全局唯一）。|
|InstanceClass|String|是|申请的 Redis 实例规格。参见实例规格表。|

## 返回参数 {#section_e4w_jkw_wbb .section}

|名称|类型|描述|
|--|--|--|
|<公共请求参数\>|-|参见[公共返回参数](cn.zh-CN/API 参考/公共参数.md#section_rjr_zgp_wbb)。|
|OrderId|String|订单 ID。|

## 请求示例 {#section_d3l_4kw_wbb .section}

```
https://r-kvstore.aliyuncs.com
?<公共请求参数>
&Action=ModifyInstanceSpec
&InstanceId=736538d0a6894665
&InstanceClass= redis.master.mid.default
```

## 返回示例 {#section_hjp_tkw_wbb .section}

```
{
"OrderId" : "201294900260011"
"RequestId" : "283746AF-82B3-4BFF-88CC-BF34CDE2732"
}
```

