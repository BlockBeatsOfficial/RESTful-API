
# Blockbeats公司PC平台接口文档 v1.0.0

## 1 规范说明

### 1.1 通信协议
HTTPS协议

### 1.2 请求方法
所有接口只支持POST方法发起请求。

### 1.3 字符编码
HTTP通讯及报文BASE64编码均采用UTF-8字符集编码格式。

### 1.4 格式说明
元素出现要求说明：

符号				|说明
:----:			|:---
R				|报文中该元素必须出现（Required）
O				|报文中该元素可选出现（Optional）
C				|报文中该元素在一定条件下出现（Conditional）

### 1.5 报文规范说明

1. 报文规范仅针对交易请求数据进行描述；  

2. 报文规范中请求报文的内容为Https请求报文中RequestData值的明文内容；

3. 报文规范分为请求报文和响应报文。请求报文描述由发起方，响应报文由报文接收方响应。

### 1.6 请求报文结构
接口只接收两个参数 **RequestData** 和 **SignData** ，其中RequestData的值为请求内容，SignData的值为签名内容。

#### 1.6.1 参数说明
**RequestData（请求内容）：** 其明文为每次请求的具体参数，采用 JSON 格式

**SignData（签名内容）：** 请求参数（明文）的MD5加密字符串，用于校验RequestData是否合法。

#### 1.6.2 请求内容（RequestData）明文结构说明

采用JSON格式，其中包含Header（公有参数）、Body（私有参数）节点：

名称		|描述											|备注
:--		|:--											|:--
公共参数	|每个接口都包含的通用参数，以JSON格式存放在Header属性	|详见以下公共参数说明
私有参数	|每个接口特有的参数，以JSON格式存放在Body属性		|详见每个接口定义

**公共参数说明：**

公共参数（Header）是用于标识产品及接口鉴权的参数，每次请求均需要携带这些参数：

参数名称				|类型		|出现要求	|描述  
:----				|:---		|:------	|:---	
token				|string		|R			|用户登录后token，没有登录则为空字符串
lang				|string		|R			|对应语言，zh,tw,en

#### 1.6.3 请求报文示例
请求内容明文：

```
{
    "header":{
        "token":"2366CF921FAD44CCBB07FF9CD02FC90E",
        "lang":"zh"
    },
    "body":{
        "email":"example@*.com",
        "password":"******"
    }
}

```

### 1.7 响应报文结构
#### 1.7.1 结构说明
所有接口响应均采用JSON格式，如无特殊说明，每次请求的返回值中，都包含下列字段：

参数名称						|类型		|出现要求	|描述  
:----						|:---		|:------	|:---	
code						|int		|R			|响应码，代码定义请见“附录A 响应吗说明”
message						|string		|R			|响应描述
data						|object		|R			|每个接口特有的参数，详见每个接口定义


#### 1.7.2 响应报文示例

```
{
    "code":200,
    "mssage":"success",
    "data":{
        "name":"example",
        "sex":1
    }
}
```


## 2. 接口定义
接口域名
```
https://api.theblockbeats.info/v4/
```


### 2.1 首页数据
- **接口说明：** 首页列表数据
- **接口地址：** /home/select

#### 2.1.1 请求参数
  
参数名称						|类型		|出现要求	|描述  
:----						|:---		|:------	|:---	
Header						|&nbsp;		|R			|请求报文头
&emsp;Token					|string		|R			|用户登录后token，没有登录则为空字符串
&emsp;lang					|string		|R			|对应语言
body						|&nbsp;		|R			|&nbsp;
&emsp;page					|boolean	|R			|对应页码


请求示例：

```
{
    "Header":{
        "token":"",
        "lang":"zh"
    },
    "body":{
        "page":"1"
    }
}

```


#### 2.1.2 返回结果

参数名称						|类型		|出现要求	|描述  
:----						|:---		|:------	|:---	
code						|int		|R			|响应码，代码定义请见“附录A 响应吗说明”
msg							|string		|R			|&nbsp;
bannerList					|object		|R			|轮播图
libraryList					|object		|R			|文库列表
newsList					|object		|R			|文章快讯列表
&emsp;id					|object		|R			|文章/快讯的id
&emsp;title					|object		|R			|文章/快讯标题
&emsp;im_abstract			|object		|R			|文章简介
&emsp;content				|object		|R			|快讯时的内容
&emsp;type					|object		|R			|文章为1/快讯为2

示例：

```
{
    "code":200,
    "Msg":"success",
    "newsList":[
		{
			"id": 0,
			"title": "BlockBeats",
			"im_abstract": "abstract",
			"type": 1
		}
	]
}
```

## 3 附录A 响应码说明

响应码	|说明  
:----	|:---
200		|处理成功
205		|未登录
201		|参数不正确
401		|未知错误



## Authors

- [@BlockBeats](https://theblockbeats.info)
