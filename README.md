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
