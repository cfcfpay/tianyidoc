# 付款成功通知接口

> ## 回调地址

接收方式：`HTTP POST`

    您在发起付款接口里传入的通知接口 即后台的回调地址
    每个订单的异步通知实行分频率发送:15s 3m 6m 10m 

>## 您需接收的参数列表

参数名称|含义|类型|说明
:--:|:--:|:--:|:--:
msg|请求状态描述|string|"用于扫描状态码的说明信息"
real_money|金额|double/float|用户实际支付的金额
order_money|金额|double/float|用户提交的金额
order_no|商户编号|string|后台返回的商户编号
channel|支付通道|string|支付类型
order_id|订单编号|string|您在发起付款接口里传入的订单号
pay_status|支付状态|int|"支付状态 0,1,2,3 代表的状态【0:支付中,1:已支付,2:支付关闭,3:通知失败】"
add_time|创建时间|string|订单创建的时间
pay_time|支付时间|string|订单支付的时间
remark|备注|string|用户备注
key|加密|string|二次验证加密方式MD5(uid + order_no + order_money + auth_code)

>## 接收样例JSON

```json
{
    "msg": "订单处理成功!",
    "key": "65236c320c42150c687e095bc3ef073248b",
    "pay_status": 1,
    "add_time": "2019-02-11 11:11:04",
    "pay_time": "2019-02-11 11:11:13",
    "order_money": 1.00,
    "real_money": 1.00,
    "order_id": "8019022311131211111",
    "order_no": "301903201745151327296265",
    "channel":"ocpay",
    "remark": "测试20190314"
}
```
>## 响应返回


响应状态码``200``停止回调







