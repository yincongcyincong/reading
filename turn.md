# AllocateRequest
开始是AllocateRequest，先是返回404，其实是需要realm和nonce，    
再发一次带有realm，nonce，username，password的数据，返回成功，    
自己（turnclient）的外网ip地址和中继的外网地址   

# CreatePermissionRequest
创建对某个ip的创建打洞许可    

# SendIndication
client给server发送数据，并指定peer的地址，peer的地址是外网地址，peer通过stun获取到    
server收到数据发送个peer，可表示洞已经打通

下面就是建立通道，主要是省去健权的那些数据帧

# 后面就是client收集连接，处理各种业务逻辑实现
