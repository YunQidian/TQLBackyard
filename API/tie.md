#贴钱活动模块 

[1.发布贴钱活动](#1)

---
##<a id="1">1.发布贴钱活动</a>

### URL
/tie/publish.json

### 请求方式
POST

### Header
Content-Type : application/json

### 请求参数
     参数      | 必选 	    | 类型及范围     |说明
-------------  | ---------- | -------------  |---------- 
uid            | true 	    | long(20)       |用户ID
title          | true 	    | string(100)    |活动名称
thumbnail      | true       | string(500)    |活动小封面、缩略图
brief          | true       | string(500)    |活动简要描述
start_time     | false      | long(15)       |活动开始时间
expire_time    | false      | long(15)       |活动结束时间
detail         | false      | longtext       |活动的详细内容
level          | false      | string(2)      |贴钱的等级
invited        | true       | int(1)         |是否有邀请机制 0或1
type           | false      | int            |贴钱的类型  
has_detail     | true       | int(1)         |是否有详细内容 0或1

### 请求Json示例
	{       
	    "uid" : 300007,
	    "title" : "平安好医生",
	    "thumbnail" ： "http://img3.imgtn.bdimg.com/it/u=3269141824,887330507&fm=21&gp=0.jpg",
	    "brief" : "走路即可赚钱，我已经领得90元",
	    "start_time" : 1443657600000,
	    "expire_time" : 1444176000000,
	    "detail" : "这是这个活动的详细介绍的源码",
	    "level" : 1,
	    "invited" : 1,
	    "type" : 12,
	    "has_detail" : 1
	}

### 返回Json示例
#### 请求成功
	{
		"success":"true",
		"data" : {
		  "tieid" : 123421
		}
	}

#### 请求失败
	{
		"error_code":"10000",
		"error_message":"XXXXX"
	}
[错误码详见错误码对照表](错误码对照表.md)
