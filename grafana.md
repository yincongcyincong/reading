grafana 升级后升级各种插件    
7.0以后compare panel不能使用    
share里面有render图片的东西    
render插件需要依赖    

sudo apt-get install -y gconf-service libasound2 libatk1.0-0 libc6 libcairo2 libcups2 libdbus-1-3 libexpat1 libfontconfig1 libgcc1 libgconf-2-4 libgdk-pixbuf2.0-0 libglib2.0-0 libgtk-3-0 libnspr4 libpango-1.0-0 libpangocairo-1.0-0 libstdc++6 libx11-6 libx11-xcb1 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxext6 libxfixes3 libxi6 libxrandr2 libxrender1 libxss1 libxtst6 ca-certificates fonts-liberation libappindicator1 libnss3 lsb-release xdg-utils wget
sudo apt-get install unifont 中文依赖

### 安装plugin命令    
./bin/grafana cli --pluginsDir="./data/plugins" plugins  install gapit-htmlgraphics-panel

### 安装vm-plugin教程


### 完成远程调用编译
在build.go -> cmd.go 中，把 `ldflags`函数中，-w参数去除    
~/go/bin/dlv --listen=:8200 --headless=true --api-version=2 --accept-multiclient  exec ./bin/darwin-arm64/grafana -- server    

### 编译
后端：
make gen-go    
make build-backend    

前端：
yarn install    
yarn build    

### inpect组件
PanelEditor（activateInActiveParents）-》激活plugin    
PanelInspectDrawer显示inspect    
DashboardSceneUrlSync 组件panelRef注册    
util.ts 获取组件    


### 清理cache
yarn cache clean

### 前端router
public/app/routes/toutes.tsx    

