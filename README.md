
# Blockbeats RESTful-API

## 1 Specifications

### 1.1 Communication Protocol
HTTPS protocol

### 1.2 Request Method
All endpoints only support POST requests.

### 1.3 Character Encoding
UTF-8 character encoding is used for both HTTP communication and BASE64 encoding of messages.

### 1.6 Request Message Structure
The endpoints accept only two parameters: RequestData and SignData. The value of RequestData represents the request content, while the value of SignData represents the signature content.

#### 1.6.3 Request Message Example
Plain text request content:

```
{
    "request":{
        "email":"example@*.com",
        "password":"******"
    }
}

```

### 1.7 Response Message Structure
#### 1.7.1 Structure Description
All endpoint responses are in JSON format. Unless specified otherwise, each response contains the following fields:

Parameter Name						|Type		|Requirement	|Description  
:----						|:---		|:------	|:---	
code						|int		|R			|Response code. Refer to "Appendix - Response Code Description" for the code definitions.
message						|string		|R			|Response description
data						|object		|R			|Parameters specific to each endpoint, see each endpoint definition for details


#### 1.7.2 Response Message Example

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


## 2.  Endpoint Definitions
Endpoint Domain
```
https://api.theblockbeats.info/v4/
```


### 2.1 Article Details
- **Endpoint Description：** 首页列表数据
- **Endpoint：** /home/select

#### 2.1.1 请求参数
  
Parameter Name						|Type		|Requirement	|Description  
:----						|:---		|:------	|:---	
Header						|&nbsp;		|R			|请求报文头
&emsp;lang					|string		|R			|对应语言
body						|&nbsp;		|R			|&nbsp;
&emsp;page					|boolean	|R			|对应页码


Request Example:

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
