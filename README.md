QQ小黄鸡VPS挂机版
=========  
[![Build Status](https://travis-ci.org/zeruniverse/QQRobot.svg?branch=master)](https://travis-ci.org/zeruniverse/QQRobot)  
***该项目修改自[SmartQQBOT](https://github.com/Yinzo/SmartQQBot)这一项目***，支持在VPS下nohup命令挂机。QQ协议说明请参考原项目。

登陆时采用QQ安全中心的二维码做为登陆条件, 不需要在程序里输入QQ号码及QQ密码。QQ自动回复私聊（无群聊功能）版本请看[这里](https://github.com/zeruniverse/QQParking)  
  
由于第一次不知道如何配置travis-ci导致了大量垃圾commit...请忽略...  

##如何使用
+ 从http://www.tuling123.com/openapi/ 申请一个API KEY(免费，5000次/天)， 贴到```QQBot.py```的第34行 (测试KEY：c7c5abbc9ec9cad3a63bde71d17e3c2c)  
+ 修改groupfollow.txt,将需要小黄鸡回复的群的群号写入(小黄鸡必须为群成员),用逗号隔开
+ ```nohup python2 QQBot.py >qbot.log&```
+ ```ls```
+ 若出现v.jpg则用QQ安全中心扫描，否则继续```ls```。
+ ```cat log.log```可以输出运行LOG
+ 强烈建议使用小号挂小黄鸡，已知QQ会临时封禁机器人的临时对话回复和群回复，原理未知，每次封禁约为10分钟。表现为发送消息返回值retcode 为 0 但其他人无法看到。长时间挂机会导致QQ被冻结错误，QQ安全中心提示发布不良信息
+ 据反馈此AI平台回复中带有少量广告。。。(如问iphone6价格回复小米799)


##功能
<small>注：以下命令皆是在qq中发送，群聊命令发送到所在群中</small>

+ 群聊智能回复，小黄鸡，在群中通过发送```!ai 问题```语句，则机器人向AI平台请求```问题```的回复并回复到群，带有!ai关键字时优先触发此功能

+ 私聊智能回复，小黄鸡，对于收到的私聊，机器人向AI平台请求该聊天记录的回复并回复给消息发送者

+ 群聊学习功能，类似于小黄鸡，在群中通过发送```!learn {ha}{哈哈}```语句，则机器人检测到发言中包含“ha”时将自动回复“哈哈”。```!delete {ha}{哈哈}```可以删除该内容。学习内容会自动储存在```groupReplys```目录中群号.save文件

+ 群聊复读功能，检测到群聊中***连续两个***回复内容相同，将自动复读该内容1次。

+ 群聊关注功能，使用命令```!follow qq号```可以使机器人复读此人所有发言（除命令外）使用命令```!unfollow qq号```解除关注。qq号处可使用"me"来快速关注与解除关注自己，例：```!follow me```
