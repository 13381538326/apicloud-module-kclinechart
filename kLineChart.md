/*
Title: kLineChart
Description: kLineChart
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：个人开发者</p>

<div class="outline">

[createView](#a1)

[addFooterData](#a2)

[loadComplete](#a3)

[loadEnd](#a4)

</div>

# **概述**

**kLineChart简介**

金融行业中，有非常复杂的数据及专业知识。展示复杂数据最直观的方式就是各种类型的图表。K线图形态可分为反转形态、整理形态及缺口和趋向线等。后K线图因其细腻独到的标画方式而被引入到股市及期货市场。股市及期货市场中的K线图的画法包含四个数据，即开盘价、最高价、最低价、收盘价，所有的k线都是围绕这四个数据展开，反映大势的状况和价格信息。如果把每日的K线图放在一张纸上，就能得到日K线图，同样也可画出周K线图、月K线图

模块涉及到金融行业专业知识，有非常多的专有名词，使用者应当会了解其中涉及的大量专业名词，因此文档不会过多解释。模块基本属性较多，因此文档如有疏忽，请及时联系作者。

**模块功能**

- 绘制K线联动图
- 定制图表的所有可控样式
- 动态分页载入数据
- K线选中滑动回调
- 自动计算常用基本指标
- 图表缩放
- 全屏显示

**kLineChart 模块概述**

本模块封装了Android原生端的高精度K线图表级联动图功能，用户需要一组简单的数据传入即可绘制出金融行业专业的K线图效果。


**不能同时使用的模块：暂无**    
    
**Android 系统平台上需注意事项**

使用此模块需要自定义loader或者云编译，android版本最低支持4.0.3

<img src="http://thyrsi.com/t6/643/1545911145x2890202402.png" width=400 />
<img src="http://thyrsi.com/t6/643/1545911192x2890202402.png" width=400 />

## [实例widget下载地址](https://github.com/XM-Right/wx-Example/archive/master.zip)
    
## **模块接口**
    
<div id="a1"></div>

# **createView**

在指定位置创建一个自定义的View，用于绘制K线图，默认打开loading状态

createView({params}, callback(ret, err))

## params

```js
{
    x: 0,  //距离左边的距离
    y: 0,  //距离上边的距离
    w: 0,  //宽度 如果为0默认为设备宽度
    h: 350, //高度  如果为0默认为设备高度
    fixedOn: 'xxx', //依附的frame名称
    fixed: true,  //跟随页面滑动
    style: {
        chart: {
            backgroundColor: '#ffffff',  //字符串 背景色(注意所有颜色必须为16进制，不能使用简写)
            candleLineWidth: 1,  //数值 蜡烛线宽度 默认 1
            candleSolid: true,  //布尔 蜡烛是否是实心 默认 true
            candleWidth: 4,  //数值 蜡烛图的宽度 默认 4
        },
        grid: {
            gridLineWidth: 1,  //数值 网格线的宽度 默认 1
            gridRows: 2,  //数值 网格横线的条数 默认 2
            gridColumns: 2,  //数值 网格竖线的条数 默认 2
            gridLineColor: '#ffffff' //字符串 网格线的颜色 默认 #ffffff
        },
        selector: {
            selectorBackgroundColor: '#c830343C', //字符串 选择器的颜色 默认#c830343C
            selectorTextSize: 12,  //数值 选择器的字体大小 默认 12
            selectedLineColor: '#000000', //字符串 十字线的颜色 默认 无
            selectedLineWidth: 1 //数值 十字线的宽度 默认 1
        },
        //注意 tab中 tabTextColor和tabTextSelectedColor字段必须同时存在
        tab: {
            stabBackgroundColor: '#000000', //字符串 tab的背景色 默认 #000000
            tabColor: '#000000', //字符串 下标颜色  默认 #000000
            tabTextColor: '#DDDDDD', //字符串 标签文字颜色 默认  #DDDDDD
            tabTextSelectedColor: '#646464' //字符串 被选中标签文字颜色 默认  #646464
        }
        ma: {
            ma5Color: '#18CCF6', //字符串 ma5线的颜色  默认 #18CCF6
            ma10Color: '#FE5EDF',  //字符串 ma10线的颜色  默认 #FE5EDF
            ma20Color: '#E7A520'  //字符串 ma20线的颜色  默认 #E7A520
        },
        macd: {
            macdWidth: 1,  //数值 macd线宽 默认 1
            difColor: '#18CCF6',  //字符串 DIF指标颜色 默认 #18CCF6
            deaColor: '#FE5EDF',  //字符串 DEA指标颜色 默认 #FE5EDF
            macdColor: '#E7A520',  //字符串 MACD指标颜色 默认 #E7A520
        },
        kdj: {
            kColor: '#18CCF6',  //字符串 K指标颜色 默认 #18CCF6
            dColor: '#FE5EDF',  //字符串 D指标颜色 默认 #FE5EDF
            jColor: '#E7A520',  //字符串 J指标颜色 默认 #E7A520
        },
        rsi: {
            rsi1Color: '#18CCF6',  //字符串 RSI1指标颜色 默认 #18CCF6
            rsi2Color: '#FE5EDF',  //字符串 RSI1指标颜色 默认 #FE5EDF
            rsi3Color: '#E7A520',  //字符串 RSI1指标颜色 默认 #E7A520
        },
        boll: {
            upColor: '#18CCF6',  //字符串 UP指标颜色 默认 #18CCF6
            mbColor: '#FE5EDF',  //字符串 MB指标颜色 默认 #FE5EDF
            dnColor: '#E7A520',  //字符串 DN指标颜色 默认 #E7A520
        }
    }
```

## callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    event: 'loadMore', // loadMore  当开启分页加载，滑动到最左边触发 
                       // select  长按K线选中滑动触发 
    data: Object  //JSONObject 类型，当事件为select时，回调选中的K线信息
}
```

## 示例代码

```js
var klineChart = api.require('klineChart');
klineChart.createView({
    x: 0,
    y: 0,
    w: 0,
    h: 350,
    style: {
        chart: {
            backgroundColor: '#ffffff',
            candleLineWidth: 1,
            candleSolid: true,
            candleWidth: 4,
        },
        grid: {
            gridLineWidth: 1,
            gridRows: 2,
            gridColumns: 2,
            gridLineColor: '#ffffff'
        },
        selector: {
            selectorBackgroundColor: '#c830343C',
            selectorTextSize: 12,
            selectedLineColor: '#000000',
            selectedLineWidth: 1
        },
        ma: {
            ma5Color: '#18CCF6',
            ma10Color: '#FE5EDF',
            ma20Color: '#E7A520'
        },
        macd: {
            macdWidth: 1,
            difColor: '#18CCF6',
            deaColor: '#FE5EDF',
            macdColor: '#E7A520',
        },
        kdj: {
            kColor: '#18CCF6',
            dColor: '#FE5EDF',
            jColor: '#E7A520',
        },
        rsi: {
            rsi1Color: '#18CCF6',
            rsi2Color: '#FE5EDF',
            rsi3Color: '#E7A520',
        },
        boll: {
            upColor: '#18CCF6',
            mbColor: '#FE5EDF',
            dnColor: '#E7A520'
        }
    }
}, function (res, err) {
    console.log(JSON.stringify(res))
})
```

## 可用性

Android系统

可提供的1.0.0及更高版本

<div id="a2"></div>

# **addFooterData**

添加数据

addFooterData({params})

## params

```js
{
    data: [{
        "open": 59.99,  //开盘价
        "date": "2018/02/07",  //交易日期 注意格式必须为 yyyy/MM/dd
        "close": 58.9,      // 收盘价
        "high": 60.39,      //最高价
        "low": 57.03,       //最低价
        "volume": 8208535   //成交量
    },
    {
        "open": 60,
        "date": "2018/02/08",
        "close": 58.51,
        "high": 60.88,
        "low": 58.5,
        "volume": 10398563
    }...]
}
```

## 示例代码

```js
api.ajax({
    url: 'http://47.98.247.192/data2.json'
}, function (ret, err) {
    if (ret) {
        klineChart.addFooterData({
            data: ret
        })
        klineChart.loadComplete()
    } else {
        api.alert({
            msg: JSON.stringify(err)
        });
    };
});
```

## 可用性

Android系统

可提供的1.0.0及更高版本

<div id="a3"></div>

# **loadComplete**

确认数据加载完成，取消loading状态。在addFooterData调用后调用此方法。

使用此方法结束一次数据加载，表示K线图可以分页加载，既向左滑动时，可以触发loadMore回调，配合addFooterData方法，可以继续绘制图，直到调用loadEnd方法为止。用户可以配置计数器来做无限动态加载K线功能，这样既可以保证性能，又能保证加载速度。

loadComplete()

## 示例代码

```js
klineChart.loadComplete()
```
## 补充说明

此方法必须在调用addFooterData加载数据之后调用。默认调用addFooterData后，图表就会绘制。但是loading状态不会取消。只有调用loadloadComplete或者loadEnd方法才会结束loading状态。

## 可用性

Android系统

可提供的1.0.0及更高版本

<div id="a4"></div>

# **loadEnd**

确认数据加载完成，取消loading状态。在addFooterData调用后调用此方法。

使用此方法结束一次数据加载，表示K线图可以分页加载，既向左滑动时，可以触发loadMore回调，配合addFooterData方法，可以继续绘制图，直到调用loadEnd方法为止。用户可以配置计数器来做无限动态加载K线功能，这样既可以保证性能，又能保证加载速度。

loadEnd()

## 示例代码

```js
klineChart.loadEnd()
```
## 补充说明

loadEnd调用表示图表的绘制完成完全结束，在调用此方法后，不得再调用其他方法，以免造成数据紊乱。

## 可用性

Android系统

可提供的1.0.0及更高版本