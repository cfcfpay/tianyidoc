# 发起付款接口

> ## 接口地址

请求方式：`HTTP POST`

    https://pay.jdypay.cc/get_pay/

>## 请求参数

参数名称|含义|类型|必填/选填|说明
:--:|:--:|:--:|:--:|:--:
uid|用户UID|string|必填|您的唯一标识，注册后在“基本配置”页面里获得，一个32位字符串。
money|金额|double/float|必填|发起付款的金额，单位：元，精确到小数点后两位。
channel|支付类型|string|必填|通道名称，当前支持参数有 cfpay-支付宝扫码 wcpay-微信扫码。
notify_url|支付回调地址|string|必填|用户支付成功后，会POST这个地址，由商户自己定义。
return_url|跳转地址|string|必填|用户支付成功后，我们会让用户浏览器自动跳转到这个网址。由您自定义不可加参数。
order_id|订单号|string|必填|订单号，由您自定义，要求唯一性，不可重复。
remark|备注|string|必填|建议传用户的ID
key|加密字符串|string|必填|"格式为 MD5(uid + auth_code + money + notify_url + order_id) （auth_code获取请联系客服）

>## 响应参数 

参数名称|含义|类型|说明
:--:|:--:|:--:|:--:
msg|请求状态描述|string|用于扫描状态码的说明信息，如：“创建成功”、“uid和auth_code 无法通过验证 请检查这两参数配置是否正确”。
code|返回状态码|string|状态码，用于标记接口的请求状态,200代表成功，其他代码表示请求失败，失败原因看msg字段
order_money|订单金额|double/float|用户提交的金额
real_money|订单金额|double/float|用户实际支付的金额
channel|支付类型|string|支付类型
pay_url|跳转的支付链接|string|支付链接字符串，直接跳转到此链接即可支付。
order_no|商户编号|string|后台生成的订单唯一编号
order_id|订单编号|string|用户自己生成的订单编号
add_time|订单生成时间|string|订单生成时间
remark|备注|string|传入的备注

>## 响应示例JSON

```json
{
    "msg": "创建成功",
    "code": 200,
    "order_money": 10,
    "real_money": 10.1,
    "order_no": "201130320161805375396336",
    "order_id": "201931231113111111",
    "add_time": "2019-02-21 06:12:05",
    "channel": "cfpay",
    "pay_url": "https://www.jdypay.cc/pay/20190320161805375396336",
    "remark":"ceshi"
}
```






