# 题库API  
## 列出所有知识点  
### Request 
|  属性   | 值  |
|  ----  | ----  |  
| 请求URL | https://weneu.neuyan.com/quiz |  
| 请求方法 | POST |  
| 请求JSON | {"action":"list"} |  
### Response  
```JSON
{
	"code": 200,
	"message": "OK",
	"data": {
		"updateTime": 1573971324553,
		"questions": [{
			"chapterList": [{
					"chapterName": "第1章 复变函数与解析函数(301题)",
					"knowledgeList": [
						"复数的概念、表示及运算(27题)",
						"乘幂与方根(51题)",
						"平面点集(51题)",
						"函数的连续、导数和解析(13题)",
						"函数可导的充要条件(83题)",
						"初等解析函数(76题)"
					]
				}
			]
		}]
	}
}
```

## 查找对应知识点的问题  
### Request
|  属性   | 值  |
|  ----  | ----  |  
| 请求URL | https://weneu.neuyan.com/quiz |  
| 请求方法 | POST |  
| 请求JSON | {"action":"getQuestion", "knowledgeList":["初等解析函数(76题)","平面点集(51题)"]} |  
### Response  
```JSON
{
  "code":200,
  "message":"OK",
  "data":{
    "size": 1,
    "questions": [
      {
        "answerDetail": "gs/de43b68db36e4b2d9d9862a81c8dfcb4_Averge_ba4be3b53af948ceb92aa4ddb1b46532_fe3c.png",
        "questionId": 12270,
        "question": "gs/de43b68db36e4b2d9d9862a81c8dfcb4_Averge_ba4be3b53af948ceb92aa4ddb1b46532_0.png",
        "answer": 2
      }
    ]
  }
}
```
### 说明  
测验全部为选择题，测验题干为question字段，四个选项分别只需将question的最后的"_0"改为"_1"、"_2"、"_3"、"_4"即可，答案为answer，解析为answerDetail  
### Tips  
图片的完整链接需要加上`https://math.neuyan.com/`
