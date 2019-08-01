
# UUIA API 文档

本文阐述了 UUIA 子节点和中心服务器的通信规约， UUIA SDK 和脚手架项目已经为您封装好此规约，无需您实现。

> 现提供 Java 版本和 Python 版本的脚手架项目。您可以 [转到UUIA开源组织查看](https://github.com/uuia)。

> 您仅需补全脚手架项目代码中repository包中类所包含的 TODO 语句所在的方法，实现数据获取逻辑 和 凭据提取/存储逻辑，并按照需要返回的数据类填充所有必要属性即可。

# API 文档介绍
## 独有标记
- UUID: 在一个学校内唯一标识一个用户的身份标识（以后请求只通过uuid进行标识，请保存此标识）
  
- group: API所属组标识
- action: 组内API唯一标识
- extraData: 额外数据是考虑到不同学校系统间的差异性推出的自定义字段，灵活使用

## 设计特点
UUIA API 设计具有三个特点
1. 路径唯一: 全局有且仅有一个路径即为uuia，子节点的路由地址为 https://yoursite/uuia
2. 请求方法唯一: 皆为POST请求
3. 请求体返回体格式唯一: 皆为JSONObject

如此设计便于 UUIA 良好的延展性，便于子节点快速使用社区组件。

## 响应状态码定义
|编码|信息|中文解释
-|-|-
|200|OK|成功
|401|Unauthorized|
|500|Internal Server Error|
|504|Gateway Timeout|

# 基础组接口 (group="base")
基础组即UUIA默认的子节点与中心节点通信的一组接口，通过实现这组接口，您可以迅速拥有适配良好的小程序客户端以及服务号的丰富能力。

## 1. 获取需要绑定的账户类型
### 1.1 说明
获得需要的密码说明及对应编号

### 1.2 请求体
#### 参数说明
属性 | 类型 | 值 | 说明
-|-|-|-
group | String | base | 固定值
action | String | bindType | 固定值

### 1.3 返回体
#### 参数说明
属性 | 类型 | 必填 | 说明
-|-|-|-
code|int|是|返回请求状态编码
message|String|是|返回请求状态信息
data|JSONObject|是|返回请求的内容

#### 返回data说明
属性 | 类型 | 必填 | 说明
-|-|-|-
accountTypes | JsonArray | 是 | 多组账户类型与编号 
-- accountType|JsonObject|是|一组账户类型与编号
---- comment|String|是|备注
---- code|String|是|编号，将主账号作为 "001"
---- ref|String|是|前置账号（相同账号的凭据），如没有则为 "000"
---- isSkip|boolean|是|可否跳过

### 示例
#####
```json
{
	"accountTypes": [{
			"comment": "教务处",
			"code": "001",
			"ref": "000",
			"isSkip": false
		},
		{
			"comment": "一卡通",
			"code": "002",
			"ref": "001",
			"isSkip": true
		}
	]
}
```

## 2. 验证用户身份
### 2.1 说明
验证用户身份接口

### 2.2 请求体
#### 参数说明
属性 | 类型 | 值 | 说明
-|-|-|-
group | String | base | 固定值
action | String | bind | 固定值
uuid | String |  | 身份标识
data | JSONObject |  | 账号凭据信息

#### 请求data说明
属性 | 类型 | 说明
-|-|-
-- account|JsonObject|一组用户名与密码
---- username|String|用户名
---- password|String|密码
---- code|int|账号密码对应编号

#### 示例
```json
{
	"action": "bind",
	"uuid": "foo",
	"data": {
		"account": {
			"username": "20161234",
			"password": "mypassword",
			"code": "001"
		}
	}
}
```

### 2.3 返回体
#### 参数说明
属性 | 类型 | 必填 | 说明
-|-|-|-
code|int|是|返回请求状态编码
message|String|是|返回请求状态信息
data|JSONObject|是|返回请求的内容

#### 返回data说明
属性 | 类型 |必填| 说明
-|-|-|-
uuid|String|是|身份标识
isSuccess|boolean|是|是否成功
errorMsg|String|否|错误信息描述（如用户名不存在，密码错误等）

#### 示例

绑定成功情况

```json
{
	"uuid": "walndlng932klfnal",
	"vaild": true
}
```

绑定错误情况

```json
{
	"uuid": "walndlng932klfnal",
	"vaild": false,
	"errorMsg": "密码错误"
}
```

## 3. 用户信息
### 3.1 说明
获取用户身份信息

### 3.2 请求体
#### 参数说明
属性 | 类型 | 值 | 说明
-|-|-|-
group | String | base | 固定值
action | String | userInfo | 固定值
uuid | String |  | 身份标识

### 3.3 返回体
#### 参数说明
属性 | 类型 | 必填 | 说明
-|-|-|-
code|int|是|返回请求状态编码
message|String|是|返回请求状态信息
data|JsonArray|是|返回请求的内容

#### 返回data说明
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
studentType|String|否|学生类型

#### 示例

```json
{
	"uuid": "fdfg32fgfe12ff#!v",
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

##  4.课程表
### 4.1 说明
获取用户课程表

### 4.2 请求参数
#### 参数说明
属性 | 类型 | 值 | 说明
-|-|-|-
group | String | base | 固定值
action | String | coursetable | 固定值
uuid | String |  | 身份标识
data | JSONObject |  | 学期信息（可选，默认本学期）

#### 请求data说明
属性 | 类型 | 说明
-|-|-
semester | String | 学期编号

### 4.3 返回参数
#### 参数说明
属性 | 类型 | 必填 | 说明
-|-|-|-
code|int|是|返回请求状态编码
message|String|是|返回请求状态信息
data|JsonArray|是|返回请求的内容

#### 返回data说明
属性 | 类型 | 必填 | 说明
-|-|-|-
uuid|String|是|身份标识
courses|JsonArray|是|学期课表
-- course|JsonObject|是|课
---- name|String|是|课程名称
---- code|String|是|课程编号
---- teachers|String[]|是|课程授课老师
---- schedules|JsonArray|是|课程安排
------ schedule|JsonObject|是|课程安排
-------- weeks|int[]|是|课程上课周数
-------- day|int|是|课程上课天(星期日至星期六 0-6)
-------- sections|int[]|是|课程上课节
-------- classroom|String|否|课程上课地点

#### 示例

```json
{
	"uuid": "fdfg32fgfe12ff#!v",
	"courses": [{
		"name": "高等数学1",
		"code": "A001341490081",
		"teachers": ["张三", "李四"],
		"schedules": [{
			"weeks": [1, 2, 3, 4, 6, 7, 8],
			"day": 2,
			"section": [1, 2],
			"classroom": "信息A101"
		}, {
			"weeks": [1, 2, 3, 4, 5, 6, 7, 8],
			"day": 4,
			"section": [3, 4],
			"classroom": "一号A101"
		}, {
			"weeks": [9],
			"day": 5,
			"section": [7, 8],
			"classroom": "一号B203"
		}]
	}]
}
```

## 5. 成绩
### 5.1 说明
获取用户成绩信息

### 5.2 请求体
#### 参数说明
属性 | 类型 | 值 | 说明
-|-|-|-
group | String | base | 固定值
action | String | score | 固定值
uuid | String |  | 身份标识
data | JSONObject |  | 学期信息（可选，默认本学期）

#### 请求data说明
属性 | 类型 | 说明
-|-|-
semester | String | 学期编号

### 5.3 返回体
#### 参数说明
属性 | 类型 | 必填 | 说明
-|-|-|-
code|int|是|返回请求状态编码
message|String|是|返回请求状态信息
data|JsonArray|是|返回请求的内容

#### 返回data说明
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

#### 示例

```json
{
	"uuid": "fdfg32fgfe12ff#!v",
	"gpa": "3.75",
	"courses": [{
		"name": "高等数学1",
		"courseCode": "A001231451542010",
		"credit": 2.0,
		"grade": 99,
		"extraData": [{
			"key": "期中成绩",
			"value": "96"
		}, {
			"key": "平时成绩",
			"value": "93"
		}]
	}]
}
```

## 6. 考试日程
### 6.1 说明
获取用户考试安排

### 6.2 请求体
#### 参数说明
属性 | 类型 | 值 | 说明
-|-|-|-
group | String | base | 固定值
action | String | exam | 固定值
uuid | String |  | 身份标识
data | JSONObject |  | 学期信息（可选，默认本学期）

#### 请求data说明
属性 | 类型 | 说明
-|-|-
semester | String | 学期编号

### 6.3 返回体
#### 参数说明
属性 | 类型 | 必填 | 说明
-|-|-|-
code|int|是|返回请求状态编码
message|String|是|返回请求状态信息
data|JSONObject|是|返回请求的内容

#### 返回data说明
属性 | 类型 | 必填 | 说明
-|-|-|-
uuid|String|是|身份标识
courses|JsonArray|是|考试课程组
-- name|String|是|课程名称
-- courseCode|String|否|课程代码
-- time|String|是|考试时间
-- place|String|否|考试教学楼及教室
-- extraData|JsonArray|是|课程其他信息

#### 示例

```json
{
	"uuid": "fdfg32fgfe12ff#!v",
	"courses": [{
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
}
```

## 7. 校园卡
### 7.1 说明
获取用户一卡通信息

### 7.2 请求体
#### 参数说明
属性 | 类型 | 值 | 说明
-|-|-|-
group | String | base | 固定值
action | String | campusCard | 固定值
uuid | String |  | 身份标识

### 7.3 返回体
#### 参数说明
属性 | 类型 | 必填 | 说明
-|-|-|-
code|int|是|返回请求状态编码
message|String|是|返回请求状态信息
data|JsonObject|是|返回请求的内容

#### 返回data说明
属性 | 类型 | 必填 | 说明
-|-|-|-
uuid|String|是|身份标识
studentId|String|否|学号
name|String|是|学生姓名
balance|String|是|一卡通余额
extraData|JsonArray|是|一卡通其他信息


#### 示例
```json
{
	"studentId": "20161234",
	"name": "小明",
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
