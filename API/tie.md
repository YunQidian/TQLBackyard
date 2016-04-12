#贴钱活动模块 

[1.发布或者修改贴钱活动](#1)

[2.查询申请发布贴钱的记录](#2)

[3.审核用户申请的贴钱活动是否符合标准](#3)

[4.设置用户申请的贴钱记录的贴文ID](#4)

[5.通过贴的ID查询贴的内容](#5)

---
##<a id="1">1.发布贴钱活动</a>

### URL
/tie/saveOrUpdate.json

### 请求方式
POST

### Header
Content-Type : application/json

### 请求参数
     参数      | 必选 	    | 类型及范围     |说明
-------------  | ---------- | -------------  |---------- 
tid            | false 	    | long(20)       |贴ID,在修改的时候传入,发布时不传入
uid            | true 	    | long(20)       |用户ID
title          | true 	    | string(100)    |活动名称
thumbnail      | true       | string(500)    |活动小封面、缩略图
brief          | true       | string(500)    |活动简要描述
start_time     | false      | long(15)       |活动开始时间
expire_time    | false      | long(15)       |活动结束时间
has_detail     | true       | int(1)         |是否有详细内容 0或1
detail         | false      | longtext       |活动的详细内容
level          | false      | int(1)         |贴钱的等级
invited        | true       | int(1)         |是否有邀请机制 0或1
type           | false      | int            |贴钱的类型  
status         | true       | int(1)         |贴的状态 0草稿 1预发布 2暂停发布 9正式发布

### 请求Json示例
	{       
	    "uid" : 300007,
	    "title" : "平安好医生",
	    "thumbnail" ： "http://img3.imgtn.bdimg.com/it/u=3269141824,887330507&fm=21&gp=0.jpg",
	    "brief" : "走路即可赚钱，我已经领得90元",
	    "start_time" : 1443657600000,
	    "expire_time" : 1444176000000,
	    "has_detail" : 1,
	    "detail" : "这是这个活动的详细介绍的源码",
	    "level" : 1,
	    "invited" : 1,
	    "type" : 12,
	    "status" : 0
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
	
---
##<a id="2">2.查询申请发布贴钱的记录</a>

### URL
/tie/apply/list.json

### 说明
默认返回20条数据，低于20条则返回实际数量

### 请求方式
POST

### Header
Content-Type : application/json

### 请求参数
     参数      | 必选 	    | 类型及范围     |说明
-------------  | ---------- | -------------  |---------- 
uid            | false 	    | long(20)       |用户ID
invited        | false 	    | int(1)         |是否有邀请机制 0 或者 1
title          | false      | string(100)    |活动名称
phone          | false      | string(15)     |手机号码
status         | false      | string(1)      |审核状态 0审核中 1不通过 2通过
start          | false      | int            |分页的起始记录

### 请求Json示例
	{       
	    "uid" : 300007,
	    "invited" : 1,
	    "title" ： "平安"
	}

### 返回Json示例
#### 请求成功
	{
		"success":"true",
		"data" : {
		  "count" : 30,  
		  "list" : [
		  	{"id":111, "uid":300007,tid:0,brief:"走路即可赚钱","invited":1,
		  	"title":"平安好医生","link":"","code":"",phone:"","status":"0",
		  	"create_time":1459833585589,"update_time":0,"is_deleted":0},
		  	{"id":112, "uid":300007,tid:0,brief:"走路即可赚大钱","invited":1,
		  	"title":"平安太好医生","link":"","code":"",phone:"","status":"0",
		  	"create_time":1459833588589,"update_time":0,"is_deleted":0}
		  ]
		}
	}

#### 请求失败
	{
		"error_code":"10000",
		"error_message":"XXXXX"
	}

---
##<a id="3">3.审核用户申请的贴钱活动是否符合标准</a>

### URL
/tie/apply/approve.json

### 请求方式
POST

### Header
Content-Type : application/json

### 请求参数
     参数      | 必选 	    | 类型及范围     |说明
-------------  | ---------- | -------------  |---------- 
applyid        | true 	    | long(20)       |申请ID
status         | true 	    | string(1)      |"1"审核不通过"2"审核通过
reason         | false 	    | string(50)     |审核不通过的原因,当status为"1"时,传入该参数

### 请求Json示例
	{       
	    "applyid" : 300007,
	    "status" : "1",
	    "reason" : "真实性不强"
	}

### 返回Json示例
#### 请求成功
	{
		"success":"true"
	}

#### 请求失败
	{
		"error_code":"10000",
		"error_message":"XXXXX"
	}	
	
---
##<a id="4">4.设置用户申请的贴钱记录的贴文ID</a>

### URL
/tie/apply/settid.json

### 请求方式
POST

### Header
Content-Type : application/json

### 请求参数
     参数      | 必选 	    | 类型及范围     |说明
-------------  | ---------- | -------------  |---------- 
applyid        | true 	    | long(20)       |申请ID
tieid          | true 	    | long(20)       |贴文的ID

### 请求Json示例
	{       
	    "applyid" : 300007,
	    "tieid" : 230004
	}

### 返回Json示例
#### 请求成功
	{
		"success":"true"
	}

#### 请求失败
	{
		"error_code":"10000",
		"error_message":"XXXXX"
	}		

---
##<a id="5">5.通过贴的ID查询贴的内容</a>

### URL
/tie/findById.json

### 请求方式
POST

### Header
Content-Type : application/json

### 请求参数
     参数      | 必选 	    | 类型及范围     |说明
-------------  | ---------- | -------------  |---------- 
tieid          | true 	    | long(20)       |贴文的ID

### 请求Json示例
	{
		"success" : "true",
		"data": {       
		    "id" : 1000001,
		    "uid" : 230004,
		    "title" : "贴的标题",
		    "startTime" : 34234345435,
		    "expireTime" : 231243235445,
		    "img" : "贴的缩略图",
		    "brief" : "简要描述",
		    "html" : 10000034,
		    "status" : 1,
		    "level" : 0,
		    "invited" : 1,
		    "type" : 123，
		    "readQuantity" : 0,
		    "hasDetail" : 1,
		    "createTime" : 242342333,
		    "updateTime" : 0,
		    "isDeleted" :０
		}
	}

### 返回Json示例
#### 请求成功
	{
		"success":"true"
	}

#### 请求失败
	{
		"error_code":"10000",
		"error_message":"XXXXX"
	}			
[错误码详见错误码对照表](错误码对照表.md)
