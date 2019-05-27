# reading

# mysql 线程和kps检测    
sysbench oltp_common --table-size=1000000 --db-driver=mysql --mysql-host=192.168.3.95 --mysql-db=test --mysql-user=root --mysql-password=cy2108cc prepare
sysbench oltp_insert --db-driver=mysql --mysql-host=192.168.3.95 --mysql-db=test --mysql-user=cy1 --mysql-password=cy2108cc --threads=8 --time=60  run  
sysbench oltp_read_only --db-driver=mysql --mysql-host=192.168.3.95 --mysql-db=test --mysql-user=root --mysql-password=cy2108cc --threads=10 --time=60  run
sysbench --test=oltp --mysql-db=test --oltp-table-name=sbtest --mysql-user=root --mysql-password=root  cleanup    

# redis 删除key   
redis-cli  -c -h 192.168.3.105 keys "1234_cc_*"  | xargs -I {} redis-cli  -c -h 192.168.3.105 del {}    


# swagger 生成swagger.json    
swagger generate spec -m -o ./swagger.json    

# swagger精髓
// swagger:operation POST /im/{xxx}/join_confer xxxx xxxxx    
//    
// xxx     
//    
// xxx    
//    
// ---    
// produces:    
// - application/json   
// parameters:    
//   - name: token    
//     in: header   
//     description: 用户token，token的值是"Bearer your_token"格式   
//     required: true   
//     format: string   
//   - name: company_id   
//     in: path   
//     description: 公司id    
//     required: true   
//     format: string   
//   - in: body   
//     name: group    
//     required: true   
//     description: xx： {"confId":"${id}","creater":"${xx}","InviterList":"${xx}"}    
//     schema:    
//       type: object   
//       properties:    
//         confId:    
//           type: string   
//         creater:     
//           type: object   
//           properties:    
//             userId:    
//               type: string   
//         InviterList:   
//	         type: array    
//	         items:   
//             type: object   
//             properties:    
//               userId:    
//                 type: string   
//   - name: role_type    
//     in: formData   
//     description: 角色类型    
//     required: true   
//     type: array    
//     items:   
//       type: string   
// responses:   
//   '200':   
//     description: success   
//     schema:    
//       type: object   
//       properties:    
//         data:    
//	         type: array    
//	         items:     
//             type: object   
//             properties:    
//               name:    
//                 type: string   


# docker精髓
进入docker查看，修改文件   
sudo docker exec -it 775c7c9ee1e1 /bin/bash   

dockerfile：：：    

FROM centos   

MAINTAINER 648588267@qq.com   

RUN mkdir /docker   
RUN mkdir /docker/im_user   

WORKDIR /docker/im_user   
COPY /im_user /docker/im_user   

ENTRYPOINT ["/docker/im_user/im_user"]    

EXPOSE 8081   

# docker
注意

run 只能run系统命令   

# sentry
1. 获取redis、postgres、sentry。sentry对redis和postgres的版本有要求，不能使用太低版本的。   

docker pull redis   
docker pull postgres    
docker pull sentry    

2.启动redis和postgres。   
docker run -d --name sentry-redis redis   
docker run -d --name sentry-postgres -e POSTGRES_PASSWORD=secret -e POSTGRES_USER=sentry postgres   
docker run --rm sentry config generate-secret-key   
#上一行得到secret-key，然后把key复制到下面四行的单引号中。    

3. 启动sentry。    
docker run -it --rm -e SENTRY_SECRET_KEY='secret-key' --link sentry-postgres:postgres --link sentry-redis:redis sentry upgrade    
docker run -d -p 9000:9000 --name my-sentry -e SENTRY_SECRET_KEY='secret-key' --link sentry-redis:redis --link sentry-postgres:postgres sentry    
docker run -d --name sentry-cron -e SENTRY_SECRET_KEY='secret-key' --link sentry-postgres:postgres --link sentry-redis:redis sentry run cron    
docker run -d --name sentry-worker-1 -e SENTRY_SECRET_KEY='secret-key' --link sentry-postgres:postgres --link sentry-redis:redis sentry run worker    
完成后，在浏览器中输入http://192.168.99.100:9000 即可访问。   

rooturl设置要注意    
完成后，在浏览器中输入http://192.168.99.100:9000 即可访问。   Url
完成后，在浏览器中输入http://192.168.99.100:9000 即可访问。   


kubectl delete pods --all --grace-period=0 --force    

kubectl  get pods --namespace kube-system  -o wide 查看pod的状态   
kubectl describe -n kube-system  pod coredns-77cd44d8df-k9sh4 看pod报错    

# 生成/etc/rhsm/ca/redhat-uep.pem文件
wget http://mirror.centos.org/centos/7/os/x86_64/Packages/python-rhsm-certificates-1.19.10-1.el7_4.x86_64.rpm
rpm2cpio python-rhsm-certificates-1.19.10-1.el7_4.x86_64.rpm | cpio -iv --to-stdout ./etc/rhsm/ca/redhat-uep.pem | tee /etc/rhsm/ca/redhat-uep.pem

获取所有的deployment   
kubectl get deployments --all-namespaces    

k8s介绍：https://blog.csdn.net/u011394397/article/details/54584819

docker的sock找不到：systemctl restart proc-sys-fs-binfmt_misc.automount



export http_proxy= socks5://www:32e@114.114.114.114:1080


# sysbench 基准测试
sysbench --db-driver=mysql --mysql-user=root --mysql-password=<pwd> \
  --mysql-socket=<mysql.sock path> --mysql-db=foo --range_size=100 \
  --table_size=10000 --tables=2 --threads=2 --events=0 --time=60 \
  --rand-type=uniform /usr/share/sysbench/oltp_read_only.lua prepare（准备）    

sysbench --db-driver=mysql --mysql-user=root --mysql-password=<pwd> \
  --mysql-socket=<mysql.sock path> --mysql-db=foo --range_size=100 \
  --table_size=10000 --tables=2 --threads=2 --events=0 --time=60 \
  --rand-type=uniform /usr/share/sysbench/oltp_read_only.lua run（查询测试）    

sysbench --db-driver=mysql --mysql-user=root --mysql-password=<pwd> \
  --mysql-socket=<mysql.sock path> --mysql-db=foo --range_size=100 \
  --table_size=10000 --tables=2 --threads=2 --events=0 --time=60 \
  --rand-type=uniform /usr/share/sysbench/oltp_read_only.lua cleanup（清理）    

top -H pid  losf -p进程
