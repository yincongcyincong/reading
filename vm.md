###  前端编译
vm： npm run build  && rm -rf ../../../vmselect/vmui/*   && mv ./build/* ../../../vmselect/vmui    
vmlog: npm run build:logs && rm -rf ../../../vlselect/vmui/*   && mv ./build/* ../../../vlselect/vmui    

### vm-grafana plugin
yarn install    
yarn dev    
yarn build    

make victoriametrics-datasource-plugin-build
