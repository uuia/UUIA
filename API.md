
# UUIA API 文档

下文阐述了 UUIA 子节点和中心服务器的通信规约， UUIA SDK 和脚手架项目已经为您封装好此规约，无需您实现。

现提供 Java 版本和 Python 版本的脚手架项目。您可以 [转到UUIA开源组织查看](https://github.com/uuia)。

您仅需补全代码中repository包中类所包含的 TODO 语句所在的方法，实现数据获取逻辑 和 凭据提取/存储逻辑，并按照需要返回的数据类填充所有必要属性即可。

## 基础组接口 (group="base")
### 1. 获取需要绑定的帐户类型
#### 说明
获得需要的密码说明及对应编号
#### 类型
POST
#### 请求参数
JsonObject object

属性 | 类型 | 说明
-|-|-
group|String|group="base"
action|String|action="bindType" 获取需要的帐户信息

#### 返回参数
JsonObject object

属性 | 类型 | 必填 | 说明
-|-|-|-
code|int|是|返回请求状态编码
message|String|是|返回请求状态信息
data|JsonArray|是|返回请求的内容
JsonArray data
属性 | 类型 | 必填 | 说明
-|-|-|-
accountTypes | JsonArray | 是 | 多组帐户类型与编号 
-- accountType|JsonObject|是|一组帐户类型与编号
---- comment|String|是|备注
---- code|int|是|编号

#### 示例
```javascript
[
	{
		"comment": "教务处",
		"code": "001"
	},
	{
		"comment": "一卡通",
		"code": "002"
	}
]
```

### 2. 验证用户身份
#### 说明
验证用户身份接口
#### 类型
POST
#### 请求参数
JsonObject object

属性 | 类型 | 说明
-|-|-
group|String|group="base"
action|String|action="bind" 绑定用户信息
uuid|String|在一个学校内唯一标识一个用户的身份标识（以后请求只通过uuid进行标识，请保存此标识）
accounts|JsonArray|多组用户名与密码
-- account|JsonObject|一组用户名与密码
---- username|String|用户名
---- password|String|密码
---- code|int|账号密码对应编号

#### 示例
```javascript
{
	"action": "bind",
	"uuid": "foo",
	"accounts": [{
			"username": "20164930",
			"password": "bar",
			"code": "001"
		},
		{
			"username": "20164930",
			"password": "foo",
			"code": "002"
		},
		{
			"username": "20164930",
			"password": "bar",
			"code": "003"
		}
	]
}
```

#### 返回参数
JsonObject object

属性 | 类型 | 必填 | 说明
-|-|-|-
code|int|是|返回请求状态编码
message|String|是|返回请求状态信息
data|JsonArray|是|返回请求的内容

JsonObject data

属性 | 类型 |必填| 说明
-|-|-|-
uuid|String|是|身份标识
vaild|boolean|是|所有组的用户名及密码是否均有效
invalidAccountType|JsonArray|否|未通过的用户名与密码
-- code|int|是|编号

#### 示例

绑定成功情况

```javascript
{
	"uuid": "walndlng932klfnal",
	"vaild": true
}
```

绑定错误情况

```javascript
{  
	"uuid":"walndlng932klfnal",  
	"vaild":false,  
	"invaildAccountTypes": ["001","003"]  
}
```

### 3. 用户信息
#### 说明
获取用户身份信息
#### 类型
POST
#### 请求参数
JsonObject object

属性 | 类型 | 说明
-|-|-
group|String|group="base"
action|String|action="userinfo" 获取用户信息
uuid|String|身份标识
#### 返回参数
JsonObject object

属性 | 类型 | 必填 | 说明
-|-|-|-
code|int|是|返回请求状态编码
message|String|是|返回请求状态信息
data|JsonArray|是|返回请求的内容

JsonObject data

属性 | 类型 | 必填 | 说明
-|-|-|-
uuid|String|是|身份标识
name|String|是|学生姓名
gender|String|否|性别
college|String|否|所在学院
major|String|否|学生专业
grade|String|否|年级
studentClass|String|否|班级
studentID|String|否|学号
studentType|否|学生类型

#### 示例

```javascript
{
	"name": "张三",
	"gender": 0,
	"college": "软件学院",
	"major": "软件工程",
	"grade": "2016",
	"studentClass": "软英1601",
	"studentId": "20165241",
	"studentType": "本科生"
}
```

### 4. 校园卡
#### 说明
获取用户一卡通信息
#### 类型
POST
#### 请求参数
JsonObject object

属性 | 类型 | 说明
-|-|-
group|String|group="base"
action|String|action="ecard" 获取一卡通信息
uuid|String|身份标识

#### 返回参数
JsonObject object

属性 | 类型 | 必填 | 说明
-|-|-|-
code|int|是|返回请求状态编码
message|String|是|返回请求状态信息
data|JsonObject|是|返回请求的内容

JsonObject data

属性 | 类型 | 必填 | 说明
-|-|-|-
uuid|String|是|身份标识
studentId|String|否|学号
name|String|是|学生姓名
balance|String|是|一卡通余额
-- extraData|JsonArray|是|一卡通其他信息
---- extraDataInfo|JsonObject|否|一卡通其他信息
------  key|String|是|其他信息名称
------  value|String|是|其他信息值

#### 示例
```javascript
{
	"studentId": "20165213",
	"name": "张三",
	"balance": 102.98,
	"extraData": [{
		"key": "补助金额",
		"value": "20"
	}, {
		"key": "校卡状态",
		"value": "已激活"
	}]
}
```

### 5. 成绩
#### 说明
获取用户成绩信息
#### 类型
POST
#### 请求参数
JsonObject object

属性 | 类型 | 说明
-|-|-
group|String|group="base"
action|String|action="score" 获取成绩
uuid|String|身份标识

#### 返回参数
JsonObject object

属性 | 类型 | 必填 | 说明
-|-|-|-
code|int|是|返回请求状态编码
message|String|是|返回请求状态信息
data|JsonArray|是|返回请求的内容

JsonObject data

属性 | 类型 | 必填 | 说明
-|-|-|-
uuid|String|是|身份标识
gpa|String|是|绩点
courses|JsonArray|是|成绩课程组
-- course|JsonObject|是|一科课程成绩
---- name|String|是|课程名称
---- courseCode|String|是|课程编号
---- credit|String|是|课程学分
---- grade|float|是|课程成绩
---- extraData|JsonArray|是|课程其他信息
------ extraDataInfo|JsonObject|否|课程其他信息
-------- key|String|是|其他信息名称
-------- value|String|是|其他信息值

#### 示例

```javascript
{
	"uuid": "wladlfd9a8732",
	"gpa": "3.55",
	"courses": [{
		"name": "高等数学1",
		"courseCode": "foobar(可选)",
		"credit": 2.0,
		"grade": 99,
		"extraData": [{
				"key": "期中成绩",
				"value": "96"
			},
			{
				"key": "平时成绩",
				"value": "93"
			}
		]
	}]
}
```

### 6. 考试日程
#### 说明
获取用户考试安排
#### 类型
POST
#### 请求参数
JsonObject object

属性 | 类型 | 说明
-|-|-
group|String|group="base"
action|String|action="exam" 获取考试日程
uuid|String|身份标识

#### 返回参数
JsonObject object

属性 | 类型 | 必填 | 说明
-|-|-|-
code|int|是|返回请求状态编码
message|String|是|返回请求状态信息
data|JsonArray|是|返回请求的内容

JsonObject data

属性 | 类型 | 必填 | 说明
-|-|-|-
uuid|String|是|身份标识
courses|JsonArray|是|考试课程组
-- name|String|是|课程名称
-- courseCode|String|否|课程代码
-- time|String|是|考试时间
-- place|String|否|考试教学楼及教室
---- extraData|JsonArray|是|课程其他信息
------ extraDataInfo|JsonObject|否|课程其他信息
-------- key|String|是|其他信息名称
-------- value|String|是|其他信息值

#### 示例

```javascript
[{
	"name": "高等数学",
	"courseCode": "课程代码(可选)",
	"time": "13:00",
	"place": "一号A101",
	"extraData": [{
		"key": "座位号",
		"value": "68"
	}, {
		"key": "考试类型",
		"value": "考查"
	}]
}]
```

###  7.课表
#### 说明
获取用户课程表
#### 类型
POST
#### 请求参数
JsonObject object

属性 | 类型 | 说明
-|-|-
group|String|group="base"
action|String|action="coursetable" 获取课表
uuid|String|身份标识

#### 返回参数
JsonObject object

属性 | 类型 | 必填 | 说明
-|-|-|-
code|int|是|返回请求状态编码
message|String|是|返回请求状态信息
data|JsonArray|是|返回请求的内容

JsonObject data

属性 | 类型 | 必填 | 说明
-|-|-|-
uuid|String|是|身份标识
courseTable|JsonArray|是|学期课表
-- course|JsonObject|是|课
---- courseName|String|是|课程名称
---- courseCode|String|是|课程编号
---- courseTeacher|String[]|是|课程授课老师
---- schedules|JsonArray|是|课程安排
------ schedule|JsonObject|是|课程安排
-------- weeks|int[]|是|课程上课周数
-------- days|int[]|是|课程上课天
-------- sections|int[]|是|课程上课节
-------- classroom|String|否|课程上课地点

#### 示例

```javascript
{
	"name": "高等数学1",
	"teachers": ["张三", "李四"],
	"schedules": [{
			"weeks": [1, 2, 3, 4, 6, 7, 8],
			"day": 2,
			"section": [1, 2],
			"classroom": "信息A101"
		},
		{
			"weeks": [1, 2, 3, 4, 5, 6, 7, 8],
			"day": 4,
			"section": [3, 4],
			"classroom": "一号A101"
		},
		{
			"weeks": [9],
			"day": 5,
			"section": [7, 8],
			"classroom": "一号B203"
		}
	]
}
```

## 响应状态码定义
|编码|信息|
-|-
|200|OK|
|401|Unauthorized|
|500|Internal Server Error|
|504|Gateway Timeout|
