# Kong的plugin
修改 kong-version.rockspec文件    
修改/usr/local/share/lua/5.1/kong/constants.lua文件    
写一个 /usr/local/share/lua/5.1/kong/plugin/完成插件   
完成plugin    

# 调用库
luarocks install + 库名
库下载到    /usr/local/share/lua/5.1/resty/ 里面    
代码里面使用：   
local redisCluster = require "resty.rediscluster"   

修改kong的配置文件  /usr/local/share/lua/5.1/kong/template/
