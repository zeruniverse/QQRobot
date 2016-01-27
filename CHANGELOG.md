Changelog
=========
  
##2015-04-14
+ 项目COPY自[SmartQQ](https://github.com/Yinzo/SmartQQBot)
+ 移除命令行输入
+ 将follow群列表写入QQBot.py
+ 从文件读取follow群列表
+ 从AI网站拉取小黄鸡回复
+ 私聊从AI网站拉取
+ 群聊写入一个DATABASE
+ 把全部的PRINT输入LOG文件
+ 修改PROTOCOL,去除LOGIN_SIG必要性。即没有获取LOGIN_SIG不报错
  
##2015-04-15
+ 添加来自群或讨论组的私聊回复
+ 方法为先获取group_sig:  
```json.loads(HttpClient_Ist.Get('http://d.web2.qq.com/channel/get_c2cmsg_sig2?id={0}&to_uin={1}&clientid={2}&psessionid={3}&service_type={4}&t={5}'.format(myid, tuin, ClientID, PSessionID, service_type, ts), Referer))```
+ 然后POST消息 
``` 
		reqURL = "http://d.web2.qq.com/channel/send_sess_msg2"
        data = (
            ('r', '{{"to":{0}, "face":594, "content":"[\\"{4}\\", [\\"font\\", {{\\"name\\":\\"Arial\\", \\"size\\":\\"10\\", \\"style\\":[0, 0, 0], \\"color\\":\\"000000\\"}}]]", "clientid":"{1}", "msg_id":{2}, "psessionid":"{3}", "group_sig":"{5}", "service_type":{6}}}'.format(tuin, ClientID, msgId, PSessionID, str(content), group_sig, service_type)),
            ('clientid', ClientID),
            ('psessionid', PSessionID),
            ('group_sig', group_sig),
            ('service_type',service_type)
        )
        rsp = HttpClient_Ist.Post(reqURL, data, Referer)         
```		
  
##2015-04-16
+ 加入消息ID核对，避免重复处理私聊
+ 替换AI的换行符与<主人>，使其对应QQ协议
+ 优化线程管理
+ 群聊限制3秒回复一条信息，若不足3秒则放弃回复此信息。 （防止被封）
+ FIRST RELEASE


##2015-07-23
+ 加入about命令  
+ 登陆失败直接终止线程  
+ 新增WINDOWS版本  

##2015-07-25
+ 加入deleteall命令，删除所有学习内容   
  
##2016-01-26
+ TX在12月底进行了协议更新，修复协议错误造成的无法登陆/发消息问题。临时消息貌似已被TX屏蔽。   
