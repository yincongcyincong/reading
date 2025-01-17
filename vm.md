###  前端编译
vm： npm run build  && rm -rf ../../../vmselect/vmui/*   && mv ./build/* ../../../vmselect/vmui    
vmlog: npm run build:logs && rm -rf ../../../vlselect/vmui/*   && mv ./build/* ../../../vlselect/vmui    

### vm-grafana plugin
yarn install    
yarn dev    
yarn build    

make victoriametrics-datasource-plugin-build

### vl 插入数据curl

### vl优化展示
_time:5m | unpack_json from _msg
_time:5m | unpack_logfmt from _msg

### 前端报错
1.  Cannot find module 'react-scripts/package.json'    
  使用 npm i react-scripts    
 

