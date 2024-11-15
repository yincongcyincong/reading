# docker   
run 只能run系统命令   
docker run -d -p 48080:7081 -v /mnt/im_web/log/:/mnt/log/ im_web_2.0:lastest /mnt/im_user_2.0 /bin/sh   
-v 挂载目录，前一个实体机目录 ，后一个docker目录

# docker启动nginx
docker pull nginx:1.25    
docker run -d --restart=always --network=host --name nginx -p 80:80 nginx:1.25    
apt-get update 更新依赖
apt-get install xxx 安装
使用机器ip，一般是172开头
