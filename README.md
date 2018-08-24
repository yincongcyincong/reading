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
//     description: 注册单个用户： {"confId":"${会议id}","creater":"${创建人}","InviterList":"${邀请人}"}
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
