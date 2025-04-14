# 上传包到npx库
创建npx账号,https://www.npmjs.com/    
![image](https://github.com/user-attachments/assets/3be3948a-066a-4f9e-8b97-cd4425e44c6d)
创建access token, Type 选择 publish    
vim ~/.npmrc,增加：     
```
registry=https://registry.npmjs.org/
//registry.npmjs.org/:_authToken=xxxxxx
```
npm publish 
