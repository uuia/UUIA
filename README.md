
<p align="center">
    <a href="http://uuia.info">
        <img src="https://github.com/uuia/UUIA/blob/master/images/UUIA_logo.png?raw=true" alt="UUIA logo" width="200" style="border-radius:50%" />
    </a>
</p>

<h3 align="center">快速部署基于微信生态的高校信息服务</h3>

[![](https://img.shields.io/github/license/uuia/UUIA.svg?style=flat-square)](http://uuia.info)
[![](https://img.shields.io/maven-central/v/uuia/java-sdk.svg?style=flat-square)](http://uuia.info)
[![](https://img.shields.io/website/http/uuia.info.svg?style=flat-square)](http://uuia.info)
[![](https://img.shields.io/github/contributors/uuia/UUIA.svg?style=flat-square)](https://github.com/uuia/UUIA)

***
⚠️**UUIA**基础框架正在全力搭建中，UUIA官方网站预计**5月下旬**正式开放，敬请期待。
***

# 概述
**统一大学信息聚合开放服务框架** (Unified University Information Aggregation (UUIA)) 是一套基于微信生态的校园信息服务框架，我们将帮助各高校的开发者迅速地搭建起自己学校的移动端校园信息服务，开发者只需要编写本校各信息网站的信息获取代码即可，UUIA负责处理微信端繁杂的交互逻辑并提供界面优美的客户端。
## 起源  
UUIA起源于UUIA的开发者在对自己学校线上信息服务平台的思考，我们发现大部分学校的信息化系统都存在共同的问题：
- 信息分散(教务处、图书馆、一卡通、新闻等分属不同的网站)
- 不适配移动端(无法在手机上得到好的使用体验)
- 没有主动推送通知(人找信息而非信息找人)
- 信息价值没有被进一步挖掘(可以利用校内信息做更多事情)

所以我们利用爬虫的方式为我们学校开发了一套移动端的信息服务平台，同学们可以通过微信服务号或微信小程序的方式在手机上查询自己的课表/成绩/校卡余额/图书借阅记录等信息，另外我们还通过微信服务号的形式定期推送给同学明日课表/余额不足提醒/借阅到期提醒等。  
## 思考
我们在开发本校的校园信息服务时发现，将代码简单修改后也可以迅速适配其他学校的信息系统，所以我们决定将我们的服务抽离出一套高校信息服务框架，其他开发者只需要按照对应的API调用规范编写少量后端代码即可利用UUIA框架迅速开发。
## UUIA服务框架
<p align="center">
    <img src="https://github.com/uuia/UUIA/blob/master/images/SystemDesign.png?raw=true" alt="UUIA Framwork" width="600px" />
</p>

## UUIA开发者社区
UUIA开发者社区是UUIA的另一个重要组成部分。  

我们发现，在大学校园这一应用场景下，有诸如“失物招领”、“二手交易”、“校内交流社区”等应用具有“局域适用”、“可复制性高”的特点，即这些校内应用的用户仅限于一所学校，一款好用的校内应用可以迅速部署到其他学校，这契合UUIA“**帮助开发者快速部署基于微信生态的高校信息服务**”的使命。  

所以我们搭建了UUIA开发者社区，各位高校开发者可以以组件的形式将好用实用易用的校内应用开源并提供部署指南，帮助其他开发者迅速部署，**人人为我，我为人人**是UUIA开发者社区的核心理念。

## 总结
UUIA包括
- UUIA服务框架
- UUIA开发者社区

我们将提供以下服务：
- 一套完整的校园信息API规范
- 多语言版本SDK
- 小程序客户端开源代码
- 服务号网页端一键部署
- 丰富的社区插件
- 实用的开发者工具

## 愿景
**用技术推动中国高校发展建设，用创意让每位高校师生感到快乐**

# 快速上手
## 1. 阅读开发规范
- [UUIA开发者中心](http://uuia.info)
## 2. 注册开发者身份
- [UUIA开发平台注册](http://uuia.info)
- 加入QQ交流群：985877354
## 3. 安装SDK编写少量后端代码
### Maven
```xml
<dependency>
    <groupId>info.uuia</groupId>
    <version>1.0.0</version>
</dependency>
```
>目前仅提供Java SDK，其他语言SDK在全力制作中。
- [UUIA API规范文档](http://uuia.info)
- [UUIA开发者工具](http://uuia.info)
## 4. 安装微信小程序客制化本校小程序
```bash
git clone https://github.com/uuia/java-sdk.git
```
- [小程序部署指南](http://uuia.info)
- [小程序社区插件](http://uuia.info)
- [微信小程序API文档](https://developers.weixin.qq.com/miniprogram/dev/api/)
## 5. 联系我们进行部署
- [UUIA开发者中心](http://uuia.info)
- [用户使用教程](http://uuia.info)

# 试用
## 微信服务号
<img src="https://github.com/uuia/UUIA/blob/master/images/hulu_qrcode.jpg?raw=true" alt="hulu qrcode" width="150" />

## 微信小程序(东北大学版)
<img src="https://github.com/uuia/UUIA/blob/master/images/weneu_qrcode.jpg?raw=true" alt="weneu qrcode" width="150" />

# UUIA在中国
以下高校已利用或正在利用UUIA服务框架完成本校校园信息服务的部署  
<img src="https://github.com/uuia/UUIA/blob/master/images/university/dongbeidaxue.png?raw=true" alt="东北大学" width="100" />
<img src="https://github.com/uuia/UUIA/blob/master/images/university/daliankejixueyuan.jpg?raw=true" alt="大连科技学院" width="100" />
<img src="https://github.com/uuia/UUIA/blob/master/images/university/hubeigongyedaxue.jpg?raw=true" alt="湖北工业大学" width="100" />

# 贡献
您可以通过以下三种方式为UUIA助力
## 帮助UUIA服务框架变得更好
如果您对UUIA框架设计有好的想法，欢迎与我们联系后提交[PR](https://github.com/uuia/UUIA/compare)，为优化 UUIA 贡献力量！

## 丰富UUIA开发者社区
[UUIA开发者社区](http://uuia.info) 静候您好玩实用的开源应用。

## 好的意见与建议
如果您对UUIA的现状与未来发展有好的意见或建议，欢迎给我们提 [Issue](https://github.com/uuia/UUIA/issues)。 

# 联系我们
<img src="https://github.com/uuia/UUIA/blob/master/images/qqgroup.jpg?raw=true" alt="UUIA交流QQ群" width="150" />
