
<p align="center">
    <a href="http://uuia.info">
        <img src="https://github.com/uuia/UUIA/blob/master/images/UUIA_logo.png?raw=true" alt="UUIA logo" width="200" style="border-radius:50%" />
    </a>
</p>
<p align="center" style="font-size:20px; font-weight:bold;">
    快速部署基于微信生态的高校信息服务
</p>

# 概述
**统一大学信息聚合开放服务框架** (Unified University Information Aggregation (UUIA)) 是一套基于微信生态的校园信息服务框架，我们将帮助各高校的开发者迅速地搭建起自己学校的移动端校园信息服务，开发者只需要编写本校各信息网站的信息获取代码即可，UUIA负责处理微信端冗余的交互逻辑并提供界面优美的客户端。
## 起源  
UUIA起源于UUIA的开发者在对自己学校线上信息服务平台的思考，我们发现大部分学校的信息化系统都存在共同的问题：
- 信息分散(教务处、图书馆、一卡通、新闻等分属不同的网站)
- 不适配移动端(无法在手机上得到好的使用体验)
- 没有主动推送通知(人找信息而非信息找人)
- 信息价值没有被进一步挖掘(可以利用校内信息做更多事情)

所以我们利用爬虫的方式为我们学校开发了一套移动端的信息服务平台，同学们可以通过微信服务号或微信小程序的方式在手机上查询自己的课表/成绩/卡余额/借阅记录等信息，另外我们还通过微信服务号的形式定期推送给同学明日课表/余额不足提醒/借阅到期提醒等。  
## 思考
我们开发完我们本校的校园信息服务后我们发现将代码简单修改后也可以迅速适配其他学校的信息系统，所以我们决定将我们的服务抽离出一套高校信息服务框架，其他开发者只需要按照对应的API调用规范编写少量后端代码即可利用UUIA框架迅速开发。
## 服务框架
<p align="center">
    <img src="https://github.com/uuia/UUIA/blob/master/images/SystemDesign.png?raw=true" alt="UUIA Framwork" width="600" />
</p>

## 我们提供什么？
- 一套完整的校园信息API规范
- 多语言版本SDK
- 小程序客户端开源代码
- 丰富的社区插件
- 实用的开发者工具

# 快速上手
## 1. 阅读开发规范
- [UUIA开发者中心](http://uuia.info)
## 2. 注册开发者身份
- [UUIA开发平台注册](http://uuia.info)
- 加入QQ交流群：
## 3. 安装SDK编写少量后端代码
### Gradle
```
compile 'info.uuia:uuia-java-sdk:1.0.+'
```
### Maven
```
<dependency>
    <groupId>info.uuia</groupId>
    <version>[1.0.0, 1.0.99]</version>
</dependency>
  ```
  >目前仅提供Java SDK，其他语言SDK在全力制作中。
- [UUIA API规范文档](http://uuia.info)
- [UUIA开发者工具](http://uuia.info)
## 4. 安装微信小程序客制化本校小程序
```
git clone 
```
- [小程序部署指南](http://uuia.info)
- [小程序社区插件](http://uuia.info)
- [微信小程序API文档](https://developers.weixin.qq.com/miniprogram/dev/api/)
## 5. 联系我们进行部署
- [UUIA开发者中心](http://uuia.info)
- [用户使用教程](http://uuia.info)

# 试用
## 微信服务号
<img src="https://github.com/uuia/UUIA/blob/master/images/hulu_qrcode.jpg" alt="hulu qrcode" width="150" />

## 微信小程序(东北大学版)
<img src="https://github.com/uuia/UUIA/blob/master/images/weneu_qrcode.jpg?raw=true" alt="weneu qrcode" width="150" />

# UUIA在中国
以下高校已利用UUIA服务框架完成了本校校园信息服务的部署：  
<img src="https://ws4.sinaimg.cn/large/006tNc79ly1g1vanat1rvj30ct0bx77f.jpg" alt="neu" width="100" />

# 链接
- [UUIA官网](http://uuia.info)
- [意见反馈]()
- QQ群：

# 开源协议
本项目基于 [MIT](https://zh.wikipedia.org/wiki/MIT%E8%A8%B1%E5%8F%AF%E8%AD%89) 协议，请自由地享受和参与开源。

# 贡献
如果你有好的意见或建议，欢迎给我们提 [Issue](https://github.com/uuia/UUIA/issues) 或 [PR](https://github.com/uuia/UUIA/compare)，为优化 UUIA 贡献力量！