### record ###


remote procedure call (RPC): A communication protocol used primarily between client and server. The term has three definitions that are often used interchangeably: a runtime environment providing for communication facilities between computers (the RPC runtime); a set of request-and-response message exchanges between computers (the RPC exchange); and the single message from an RPC exchange (the RPC message).  For more information, see [C706]. 


TDS includes facilities for authentication and identification, channel encryption negotiation, issuing of SQL batches, stored procedure calls, returning data, and transaction manager requests. Returned data is self-describing and record-oriented. The data streams describe the names, types and optional descriptions of the rows being returned. The following diagram depicts a (simplified) typical flow of communication in the TDS Protocol. 

Figure 1: Communication flow in the TDS protocol

client连接认证成功
 Client:SQL statement



服务响应消息
 Server:COLMETADATAdata stream 
 ROWdata stream 
 . 
 . 
 ROWdata stream 
 DONEdata stream 


#### TDS和其他协议的关系: ####



#### 客户端访问服务端类型: ####

Pre-Login 
Login 
Federated Authentication Token 
SQL Batch 
Bulk Load 
Remote Procedure Call 
Attention 
Transaction Manager Request 


