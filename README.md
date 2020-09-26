# parse-sqlserver
sql server解析服务


#### 协议解析流程: ####

消息体:
	消息头 package header 8字节:type 操作类型;length 消息体;id;version 协议版本;window未使用;state 请求状态;
	请求体:不同操作模型不一样;sql patch;login;rpc请求 所有操作都是rpc,server解析时内置存储过程,调用sql类似存储过程调用;

	问题:
		1 golang实现包看的有点吃力;
		2 主要面对sql适配,不是解析;解析未外部暴露,外部无法调用;
		3 TDS是应用层协议,在应用层解析
		
	16进制的数据数组;
		
	
#### 需求: ####

客户端抓包了解sql server请求内容即可

1 数据包解析:sql常用操作;rpc select update操作;统计延迟;响应结果结构,定义数据包拆分后包关联,响应状态;
2 tcp拆包和组装如何实现:拆包有两次tds协议和tcp协议;

#### 抓包工具及原理: ####

libpcap(package capture library):unix/linux平台下的网络数据包捕获函数包;windows下类似函数包是winpcap;
 
libpcap主要功能包括:数据包捕获,发送,流量采集与统计,规则过滤等;

原理:libpcap主要由三部分组成:网络分接头,数据包过滤器,用户api;它通过网络分接头监听和复制链路层网卡数据包;通过数据包过滤器过来中间层数据,匹配目标数据;用户api实现功能调用;


gopackage 支持libpcap解析 https://cloud.tencent.com/developer/article/1478203