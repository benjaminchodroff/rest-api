# Public Rest API for ExCraft (2018-8-28)
请求地址：https://www.excraft.com

# 错误信息：
错误信息包含在http请求头<br>
grpc-status：错误码<br>
grpc-message：错误详情信息<br>
```python
code = response.headers[grpc-status]
details = response.headers[grpc-message]
```

# 变量说明：
## 方向
| Value	| Meaning |
| :-----: | :-------: |
| 1	| Sell |
| 2	| Buy |

## 订单类型
| Value	| Meaning |
| :-----: | :-------: |
| 1	| Limit |
| 2	| Market |

## 订单角色
| Value	| Meaning |
| :-----: | :-------: |
| 1	| Maker |
| 2	| Taker |

# K线时间间隔
| Value	| Meaning |
| :-----: | :-------: |
| 60	| 1 min |
| 300	| 5 min | 
| 900	| 15 min |
| 1800	| 30min |
| 3600	| 1 hour |
| 7200	| 2 hours |
| 14400	| 4 hours |
| 21600	| 6 hours |
| 28800	| 8 hours |
| 86400	| 1 day |
| 604800	| 1 week |

# Public API
## 1 GetMarketList
获取支持的交易对<br>
/apis/trading/v1/markets<br>
请求参数：无<br>
请求类型：get<br>
返回结果：<br>
```python
[
  {
    name:string;
    base:string;
    quote:string;
    fee_prec:int32;
    base_prec:int32;
    quote_prec:int32;
    base_min_size:string;
  }
]
```

## 2 GetMarketLastPrice
获取最近一次市场价格<br>
/apis/trading/v1/markets/{market}/last_price<br>
请求参数：无<br>
请求类型：get<br>
返回结果：<br>
```python
{
  price:string;
}
```

## 3 GetMarketStatusToday
获取24小时交易对状态<br>
/apis/trading/v1/markets/{market}/status_today<br>
请求参数：无<br>
请求类型：get<br>
返回结果：<br>
```python
{
  last:string;
  open:string;
  close:string;
  high:string;
  low:string;
  volume:string;
}
```

## 4 GetMarketTrades
获取最近成交纪录<br>
/apis/trading/v1/markets/{market}/trades<br>
请求参数：<br>
```python
json_encode{
  market:string;
  limit:int32;
  last_id:int32;
}
```
请求类型：get<br>
返回结果：<br>
```python
[
    {
      id:int32;
      timestamp:int32;
      side:int32;
      price:string;
      amount:string;
    }
]
```

## 5 GetDepth
获取交易挂单<br>
/apis/trading/v1/markets/{market}/depth<br>
请求参数：<br>
```python
json_encode{
  market:string;
  limit:int32;
  merge:string;
}
```
请求类型：get<br>
返回结果：<br>
```python
{
  asks:[            //卖单
    {
      price:string;
      amount:string;
    }
  ],
  bids:[            //买单
    {
      price:string;
      amount:string;
    }
  ]
}
```


## 6 GetMarketCandles
获取交易k线图<br>
/apis/trading/v1/markets/{market}/candles<br>
请求参数：<br>
```python
json_encode{
  market:string;
  start_time:int32;
  end_time:int32;
  time_frame:int32;
}
```
请求类型：get<br>
返回结果：<br>
```python
[
  {
    timestamp:int32;
    open:string;
    close:string;
    high:string;
    low:string;
    volume:string;
    market:string;
  }
]
```
