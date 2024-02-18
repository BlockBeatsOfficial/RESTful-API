
# Blockbeats RESTful-API

 Domain
```
https://api.theblockbeats.news/v1/
```
## 1 Specifications

### 1.1 Communication Protocol
HTTPS protocol

### 1.2 Request Method
All endpoints only support GET requests.

### 1.3 Character Encoding
UTF-8 character encoding is used for both HTTPS communication 

### 1.4 Request Message Structure

### 1.4.1 Flash Details
- ** article ** 
- **Endpoint：** open-api/open-flash?size={size}&page={page}&type={type}

#### 1.4.2 Query

```
"page":1,  //page
"size":10, //size
"type":push //important news
"lang":cn //language cn,en,cht
```

### 1.7 Response Message Structure
#### 1.7.1 Structure Description
All endpoint responses are in JSON format. Unless specified otherwise, each response contains the following fields:

Parameter Name						|Description  
:----							|:---	
title							|flash title
content 						|flash content
pic							|flash image
link							|BlockBeats link
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
- **Endpoint：** open-api/open-information?size={size}&page={page}&type={type}

#### 2.1.1 Quest

```
"page":1,  //page
"size":10, //size
"type":push //important news
"lang":cn //language cn,en,cht
```

All endpoint responses are in JSON format. Unless specified otherwise, each response contains the following fields:

Parameter Name						|Description  
:----							|:---	
title							|Article title
description 						|Article description
content							|Article content
link							|BlockBeats link
url							|url
create_time					        |create time

示例：

```
{
	"status": 0,
	"message": "获取成功",
	"data": {
		"page": "2",
		"data": [
			{
				"title": "原生资产VS桥接资产：加密货币的安全之路",
				"description": "了解和区分加密货币的原生资产与跨链桥资产的重要性。",
				"content": "",
				"link": "https://m.theblockbeats.info/news/37335",
				"pic": "https://image.theblockbeats.info/headimage/2023-05-25/3f95f1423597e21500ee86c40a453e7f01676a6e.png?x-oss-process=image/quality,q_50/format,webp",
				"column ": "DeFi",
				"create_time": "1684998869",
				"is_original": true
			}
		]
	}
}
```

## 3 Appendix - Response Code Description

Response Code	|Description  
:----	|:---
0		|Processed successfully
## Authors

- [@BlockBeats](https://theblockbeats.info)
