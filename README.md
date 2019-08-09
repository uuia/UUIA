
<p align="center">
    <a href="https://uuia.cheelem.com/">
        <img src="https://ww2.sinaimg.cn/large/006tNc79ly1g5sh8jofiuj30sg0sg0uo.jpg" alt="UUIA logo" width="200" style="border-radius:50%" />
    </a>
</p>

<h3 align="center">快速部署基于微信生态的高校信息服务</h3>


***
😋 **UUIA** [官方网站](https://uuia.cheelem.com/) 与 [开放平台](https://uuia.cheelem.com/dev) 现已开放，欢迎您的使用！
***


[![](https://img.shields.io/website/http/uuia.info.svg?style=flat-square)](http://uuia.info)
![GitHub stars](https://img.shields.io/github/stars/uuia/UUIA?style=flat-square)
<a href="https://github.com/uuia/UUIA/blob/master/UUIA-LICENSE.md">![GitHub stars](https://img.shields.io/badge/license-UUIA-yellow?style=flat-square)</a>



# UUIA 概述
**统一大学信息聚合开放服务框架** (Unified University Information Aggregation (UUIA)) 是一套基于微信生态的校园信息服务框架，我们将帮助各高校的开发者迅速地搭建起自己学校的移动端校园信息服务，开发者只需要编写本校各信息网站的信息获取代码即可，UUIA负责处理微信端繁杂的交互逻辑并提供界面优美的客户端。


 ## 起源  
UUIA起源于UUIA的开发者在对自己学校线上信息服务平台的思考，我们发现大部分学校的信息化系统都存在共同的问题：
- 信息分散(教务处、图书馆、一卡通、新闻等分属不同的网站)
- 不适配移动端(无法在手机上得到好的使用体验)
- 没有主动推送通知(人找信息而非信息找人)
- 信息价值没有被进一步挖掘(可以利用校内信息做更多事情)

所以我们利用爬虫的方式为我们学校开发了一套移动端的信息服务平台，同学们可以通过微信服务号或微信小程序的方式在手机上查询自己的课表/成绩/校卡余额/图书借阅记录等信息，另外我们还通过微信服务号的形式定期推送给同学明日课表/余额不足提醒/借阅到期提醒等。  

 **思考**：我们在开发本校的校园信息服务时发现，**将代码简单修改后也可以迅速适配其他学校的信息系统**，所以我们决定将我们的服务抽离出一套高校信息服务框架，其他开发者只需要按照对应的 API 调用规范编写少量后端代码即可利用 UUIA 框架迅速开发。


 ## UUIA服务框架
 由此我们便设计出了一套将数据获取逻辑和前端用户交互逻辑解耦的一个框架。其示意图如下图所示。
 
<p align="center">
    <img src="https://github.com/uuia/UUIA/blob/master/images/SystemDesign.png?raw=true" alt="UUIA Framwork" width="600px" />
</p>


 ## UUIA开发者社区
我们提供此框架，并依靠开源社群之力量构建 UUIA 开发者社区，这是UUIA的另一个重要组成部分。  

我们发现，在大学校园这一应用场景下，有诸如“失物招领”、“二手交易”、“校内交流社区”等应用具有“局域适用”、“可复制性高”的特点，即这些校内应用的用户仅限于一所学校，一款好用的校内应用可以迅速部署到其他学校，这契合 UUIA “**帮助开发者快速部署基于微信生态的高校信息服务**” 之主旨。  

故我们搭建 UUIA 开发者社区，各高校开发者可以组件的形式将好用实用易用的且与校园内部特定数据无关的校内应用 （如 失物招领、表白墙等应用） 开源，依托UUIA的身份认证提供用户凭据识别，同时向社区内开发者提供部署指南，帮助其他开发者迅速部署。

**人人为我，我为人人** 是UUIA开发者社区核心之理念。

 ## 总结
UUIA 包括
- UUIA 服务框架
- UUIA 开发者社区

我们将提供以下服务：
- 一套完整的校园信息和身份鉴权 API 规范
- 多语言版本 SDK
- 小程序客户端开源代码
- 服务号网页端一键部署
- 丰富的社区插件
- 实用的开发者工具

<img src="https://github.com/uuia/UUIA/blob/master/images/composition.png?raw=true" alt="composition" width="600px" />

 ## 愿景
**依托开源社群之力用技术推动国内高校信息化统合化发展建设，并用创意让每位高校师生感到快乐。**

# 快速上手指南

## 1. 了解UUIA，阅读开发规范
- [UUIA 官网](http://uuia.info)
- [UUIA License](https://github.com/uuia/UUIA/blob/master/UUIA-LICENSE.md)

## 2. 注册开发者身份
- [UUIA 开放平台注册](https://uuia.cheelem.com/dev)
- 加入QQ群（UUIA开发者交流群 | 小程序校园运营）：**985877354**

## 3. 安装SDK编写少量后端代码

**Java 版本 SDK**

```bash
git clone https://github.com/uuia/java-sdk.git
```

>目前提供 Java 与 Python 两个版本 SDK, 其他语言 SDK 在全力制作中。
- [UUIA Java SDK 使用指南](https://github.com/uuia/UUIA-Java-SDK)
- [UUIA API 规范文档](https://github.com/uuia/UUIA/blob/master/API.md)

<!-- ***
我们推荐您直接下载Java脚手架项目，脚手架本身已经引入了上面的uuia依赖以及springboot、mybatis依赖。
*** -->

## 4. 安装微信小程序客制化本校小程序

**基础小程序源码**

```bash
git clone https://github.com/uuia/UUIA-Mini-APP.git
```

- [小程序部署指南](https://github.com/uuia/UUIA-Mini-APP)
- [微信小程序开发者文档](https://developers.weixin.qq.com/miniprogram/dev/api/)
- [QQ小程序开发者文档](https://q.qq.com/wiki/develop/miniprogram/frame/)


## 5. 完成部署
- [UUIA 开发者中心](https://uuia.cheelem.com/dev)

# 试用

## 微信小程序(东北大学版)
<img src="https://github.com/uuia/UUIA/blob/master/images/weneu_qrcode.jpg?raw=true" alt="weneu qrcode" width="150" />

## 微信服务号
<img src="https://github.com/uuia/UUIA/blob/master/images/hulu_qrcode.jpg?raw=true" alt="hulu qrcode" width="150" />

# UUIA 在中国
<!-- 以下高校已利用或部分利用 UUIA 服务框架完成本校校园信息服务的部署  
<img src="https://github.com/uuia/UUIA/blob/master/images/university/dongbeidaxue.png?raw=true" alt="东北大学" width="100" />
<img src="https://github.com/uuia/UUIA/blob/master/images/university/daliankejixueyuan.jpg?raw=true" alt="湖北工业大学" width="100" />
<img src="https://github.com/uuia/UUIA/blob/master/images/university/hubeigongyedaxue.jpg?raw=true" alt="重庆电子工程职业学院" width="100" />
<img src="https://github.com/uuia/UUIA/blob/master/images/university/hubeigongyedaxue.jpg?raw=true" alt="扬州大学" width="100" />
<img src="https://github.com/uuia/UUIA/blob/master/images/university/hubeigongyedaxue.jpg?raw=true" alt="湖南科技大学" width="100" />
<img src="https://github.com/uuia/UUIA/blob/master/images/university/hubeigongyedaxue.jpg?raw=true" alt="大连科技学院" width="100" />
<img src="https://github.com/uuia/UUIA/blob/master/images/university/hubeigongyedaxue.jpg?raw=true" alt="山西大学" width="100" /> -->

有超过35+款校园小程序已加入 UUIA 开放平台，更多伙伴，更多机会。

# 如何贡献？

您可以通过以下三种方式为UUIA助力。

## 帮助UUIA服务框架变得更好
如果您对UUIA框架设计有好的想法，欢迎与我们联系或提交[PR](https://github.com/uuia/UUIA/compare)，为优化 UUIA 贡献力量！

## 丰富 UUIA 开发者社区，让全国大学生都用上您开发的组件
- [UUIA 开放平台](https://uuia.info) 静候您好玩实用的开源应用
- [UUIA 插件开发规范](https://github.com/uuia/UUIA-Java-SDK/blob/master/PLUGIN.md)

## 好的意见与建议
如果您对 UUIA 的现状与未来发展有好的意见或建议抑或是对我们的工作有任何的疑问，欢迎提出 [Issue](https://github.com/uuia/UUIA/issues)。 

# 社群联络方式

UUIA 开发者 QQ 交流群：

<img src="http://ww2.sinaimg.cn/large/006tNc79gy1g5sjuwl46dj30f00kk40y.jpg" alt="UUIA交流QQ群" width="150" />

# UUIA+

UUIA+ 旨在探索除技术外跨校协同共享的可能性，我们将致力于整合校园优秀运营活动与模式，社科研究等数据利用方式以及相关法律法规政策等信息，为校园开发者的产品发展及个人能力提升进一步助力。

- 运营推广
- 数据研究
- 法律法规