<a name='def-api-utils-get-market'></a>
## GetMarketList
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

<a name='def-api-trade-market-last-price'></a>
## GetMarketLastPrice
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

<a name='def-api-trade-market-get-trades'></a>
## GetMarketTrades
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

<a name='def-api-trade-get-depth'></a>
## GetDepth
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


<a name='def-api-trade-market-get-candles'></a>
## GetMarketCandles
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
