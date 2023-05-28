
# Blockbeats RESTful-API

 Domain
```
https://api.theblockbeats.news/v1/
```
## 1 Specifications

### 1.1 Communication Protocol
HTTPS protocol

### 1.2 Request Method
All endpoints only support POST requests.

### 1.3 Character Encoding
UTF-8 character encoding is used for both HTTPS communication 

### 1.4 Request Message Structure

### 1.4.1 Flash Details
- ** article ** 
- **Endpoint：** open-api/open-flash?size={size}&page={page}

#### 1.4.2 Quest

```
"page":1,
"size":10
```

### 1.7 Response Message Structure
#### 1.7.1 Structure Description
All endpoint responses are in JSON format. Unless specified otherwise, each response contains the following fields:

Parameter Name						|Description  
:----							|:---	
title							|flash title
content 						|flash content
pic							|flash image
link							|Original link
url							|url
create_time					        |create time

#### 1.7.2 Response Message Example

```
{
	"status": 0,
	"message": "获取成功",
	"data": {
		"page": 1,
		"data": [
			{
				"id": 147280,
				"title": "MULTI短时上涨逼近5美元，24小时涨幅超40%",
				"content": "BlockBeats 消息，5 月 28 日，行情数据显示，MULTI（Multichain）短时上涨逼近 5 美元，现报价 4.73 美元，24 小时涨幅 41.62%。",
				"pic": "",
				"link": "https://m.theblockbeats.info/flash/147280",
				"url": "",
				"create_time": "1685275243"
			}
			
		]
	}
}
```


### 2.1 Article Details
- ** article ** 
- **Endpoint：** open-api/open-information?size={size}&page={page}

#### 2.1.1 Quest

```
"page":1,
"size":10
```


#### 2.1.2 Response Results

Parameter Name							|Type		|Requirement	|Description  
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
    "message":"success",
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

## 3 Appendix - Response Code Description

Response Code	|Description  
:----	|:---
200		|Processed successfully
205		|Not logged in
201		|Incorrect parameters
401		|Unknown error



## Authors

- [@BlockBeats](https://theblockbeats.info)
