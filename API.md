# 停车管理接口文档
### url：https://car.iweizhu.com.cn/app/

**[AUTH](#AUTH)**
* [获取openid](#获取openid)
* [注册](#注册)
* [登录](#登录)
* [发送短信](#发送短信)
* [添加车辆](#添加车辆)
* [显示账单](#显示账单)
* [选择车辆](#选择车辆)
* [车辆管理](#车辆管理)
* [车辆绑定](#车辆绑定)
* [车辆切换](#车辆切换)
* [编辑车辆](#编辑车辆)
* [我的信息](#我的信息)
* [绑定手机](#绑定手机)


**[首页](#首页)**

**[我的](#我的)**



## 接口说明

##### 请求方式

| POST/GET | encrypt | formate |
| -------- | --------| --------|
| post     | n       |  json   |

#### 接口返回

**data**: 相关请求数据

**message**: 接口返回信息

**code**: 

**auth_token**:拼接在url

**公共模块错误**: 

* 10001  参数缺失
* 10002  参数错误
* 10003  实体不存在
* 10004  系统故障
* 10005  操作失败
* 10006  底层验证抛出的错误
* 10007  第三方接口返回错误
* 10008  实体已存在
* 10009  无权限
* 10010  请求方法错误
* 10011  未知错误
* 10012  参数不能为空

**用户模块错误**: 

* 20001  账号或密码错误',
* 20002  验证码错误',
* 20003  token失效',
* 20004  短信验证码发送失败',
* 20005  信息修改失败





## AUTH


#### 获取openid

##### URL

```
/auth/get-openid
```



##### 请求参数

|       参数名       |        必填        |      类型    |     说明       |
| ----------------- | ------------------ | ----------- | -------------- |
| code               |  y                 |  string     |    微信昵称    |

##### 输出参数

###### 成功

```
{
    "message": "success",
    "code": 200,
    "data": []
}
```



#### 注册

##### URL

```
/auth/register
```



##### 请求参数

|       参数名       |        必填        |      类型    |     说明       |
| ----------------- | ------------------ | ----------- | -------------- |
| nick_name         |  y                 |  string     |    微信昵称    |
| wx_unique_id     	|  y                 |  string     |    微信openid    |

##### 输出参数

###### 成功

```
{
    "message": "success",
    "code": 200,
    "data": {
        "openId" : ''
    }
}
```




#### 登录

##### URL

```
/auth/login
```



##### 请求参数

|       参数名       |        必填        |      类型   	|     说明       	|
| ----------------- | ------------------ | ----------- 	| -------------- |
| nick_name         |  y                 |  string     	|    微信昵称    	|
| wx_unique_id     	|  y                 |  string     	|    微信openid  	|

##### 输出参数

###### 成功

```
{
    "message": "success",
    "code": 200,
    "data": {
        "id": 4,
        "true_name": "",
        "nick_name": "老噪音1",
        "password": null,
        "telphone": null,
        "auth_token": "Z6UrBNF0lfkp6LVIahUldiZzh_afdFeJ",
        "wx_unique_id": "fdafd78979f4656766676576",
        "head_img_url": null,
        "channel": null,
        "status": 1,
        "created_at": 1530525254,
        "updated_at": 1530525359,
        "default_car": 0
    }
}
```

##CAR

#### 添加车辆

##### URL

```
/car/add
```



##### 请求参数

|       参数名       |        必填        |      类型   	|     说明       	|
| ----------------- | ------------------ | ----------- 	| -------------- 	|
| car_num      	    |  y                 |  string     	|    车牌号码    	|
| type     			|  y                 |  string     	| 1-普通车 2-新能源车 |
| is_default     	|  y                 |  string     	|    是否默认  		|
| auth_token     	|  y                 |  string     	|    token  		|

##### 输出参数

###### 成功

```
{
    "message": "添加成功",
    "code": 200,
    "data": []
}
```




#### 显示账单

##### URL

```
/car/car-bill
```



##### 请求参数

|       参数名       |        必填        |      类型   	|     说明       	|
| ----------------- | ------------------ | ----------- 	| -------------- 	|
| auth_token     	|  y                 |  string     	|    token  		|

##### 输出参数

###### 成功

```
{
    "message": "暂未查询到该车的停车信息",
    "code": 200,
    "data": []
}
```
```
{
    "message": "success",
    "code": 200,
    "data": {
		"car_num" => "车牌号",
        "in_time" => "进入时间",
        "out_time" => "出去时间",
        "park_time" => "停车时间",
        "money" => '0.00'
	}
}
```


#### 选择车辆

##### URL

```
/car/car-list
```



##### 请求参数

|       参数名       |        必填        |      类型   	|     说明       	|
| ----------------- | ------------------ | ----------- 	| -------------- 	|
| auth_token     	|  y                 |  string     	|    token  		|

##### 输出参数

###### 成功


```
{
    "message": "success",
    "code": 200,
    "data": [
        {
            "id": "2",
            "user_id": "4",
            "car_num": "闽D45678",
            "car_type": "1",
            "auth_status": "1",//认证状态 1-等待认证 2-已认证 3-认证审核中 4-认证失败
            "auth": null,
            "default": true //是否默认
        }
    ]
}
```


#### 车辆管理

##### URL

```
/car/car-manage
```



##### 请求参数

|       参数名       |        必填        |      类型   	|     说明       	|
| ----------------- | ------------------ | ----------- 	| -------------- 	|
| auth_token     	|  y                 |  string     	|    token  		|

##### 输出参数

###### 成功


```
{
    "message": "success",
    "code": 200,
    "data": [
        {
            "id": "2",
            "user_id": "4",
            "car_num": "闽D45678",
            "car_type": "1",
            "auth_status": "1",//认证状态 1-等待认证 2-已认证 3-认证审核中 4-认证失败
            "auth": null,
            "default": true //是否默认
        }
    ]
}
```


#### 车辆绑定

##### URL

```
/car/car-auth
```



##### 请求参数

|       参数名       |        必填        |      类型   	|     说明       	|
| ----------------- | ------------------ | ----------- 	| -------------- 	|
| auth_token     	|  y                 |  string     	|    token  		|
| car_num        	|  y                 |  string     	|    车牌号  		|
| img           	|  y                 |  string     	|    图片地址  		|

##### 输出参数

###### 成功


```
{
    "message": "提交成功，请等待审核",
    "code": 200,
    "data": []
}
```



#### 车辆切换

##### URL

```
/users/change-def-car
```



##### 请求参数

|       参数名       |        必填        |      类型      |     说明        |
| ----------------- | ------------------ | -----------  | --------------    |
| auth_token        |  y                 |  string      |    token          |
| id                |  y                 |  string      |    车辆id        |

##### 输出参数

###### 成功


```
{
    "message": "切换成功",
    "code": 200,
    "data": []
}
```



#### 编辑车辆

##### URL

```
/car/edit-car
```



##### 请求参数

|       参数名       |        必填        |      类型   	|     说明       	|
| ----------------- | ------------------ | ----------- 	| -------------- 	|
| auth_token     	|  y                 |  string     	|    token  		|
| car_num        	|  y                 |  string     	|    新车牌号  		|
| old_car_num      	|  y                 |  string     	|    旧图片地址  		|
| type      	    |  y                 |  string     	|    类型 1-普通车 2-新能源车  		|
| is_default      	|  y                 |  string     	|    是否默认  		|

##### 输出参数

###### 成功


```
{
    "message": "修改成功",
    "code": 200,
    "data": []
}
```


---


##sms

#### 发送短信

##### URL

```
/sms/send-sms
```



##### 请求参数

|       参数名       |        必填        |      类型   	|     说明       	|
| ----------------- | ------------------ | ----------- 	| -------------- 	|
| phone      	    |  y                 |  string     	|    手机号码    	|
| auth_token     	|  y                 |  string     	|    token  		|

##### 输出参数

###### 成功

```
{
    "message": "发送成功",
    "code": 200,
    "data": []
}
```

---


##users

#### 我的信息

##### URL

```
/users/mine
```



##### 请求参数

|       参数名       |        必填        |      类型   	|     说明       	|
| ----------------- | ------------------ | ----------- 	| -------------- 	|
| auth_token     	|  y                 |  string     	|    token  		|

##### 输出参数

###### 成功

```
{
    "message": "success",
    "code": 200,
    "data": {
        "id": "4",
        "true_name": "",
        "nick_name": "老噪音1",
        "password": null,
        "telphone": null,
        "auth_token": "Z6UrBNF0lfkp6LVIahUldiZzh_afdFeJ",
        "wx_unique_id": "fdafd78979f4656766676576",
        "head_img_url": null,
        "channel": null,
        "status": "1",
        "created_at": "1530525254",
        "updated_at": "1530525856",
        "default_car": "2",
        "car": [
            {
                "id": "2",
                "user_id": "4",
                "car_num": "闽D45678",
                "car_type": "1",
                "auth_status": "1",
                "auth": null
            }
        ],
        "defaultCar": {
            "id": "2",
            "user_id": "4",
            "car_num": "闽D45678",
            "car_type": "1",
            "auth_status": "1"
        }
    }
}
```


#### 绑定手机

##### URL

```
/users/bind-phone
```



##### 请求参数

|       参数名       |        必填        |      类型   	|     说明       	|
| ----------------- | ------------------ | ----------- 	| -------------- 	|
| auth_token     	|  y                 |  string     	|    token  		|
| phone     		|  y                 |  string     	|    手机号码  		|
| sms     			|  y                 |  string     	|    短信  			|

##### 输出参数

###### 成功

```
{
    "message": "绑定成功",
    "code": 200,
    "data": []
}
```



















 