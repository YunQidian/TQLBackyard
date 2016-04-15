#用户模块 

[1.通过ID查找用户信息](#1)

---
##<a id="1">1.通过ID查找用户信息</a>

### URL
/user/findById.json

### 请求方式
POST

### Header
Content-Type : application/json

### 请求参数
     参数      | 必选 	    | 类型及范围     |说明
-------------  | ---------- | -------------  |---------- 
id             | true 	    | long(20)       |用户ID


### 请求Json示例
	{       
	    "id" : 300007
	}

### 返回Json示例
#### 请求成功
	{
		"success":"true",
		"data" : {
		  "id" : 300007,
		  "phone" : "",
		  "username" : "",
		  "nickname" : "",
		  "email" : "",
		  "qq" : 0,
		  "sex" : 1,
		  "country" : "",
		  "province" : "",
		  "city" : "",
		  "portrait" : "",
		  "createTime" : 123243324,
		  "updateTime" : 123123123,
		  "isDeleted" : 0
		}
	}

#### 请求失败
	{
		"error_code":"10000",
		"error_message":"XXXXX"
	}
	
[错误码详见错误码对照表](错误码对照表.md)
