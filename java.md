1. 测试环境启动
* 安装java17和maven,google 找教程
* 修改maven配置 Java in iCoding
* 执行：mvn -U clean package -DskipTests -Ptest，打成tar包
* 进入output进行解压
* 使用：java -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:8200 -jar lib/lingjing-plugin-market-api-app.jar 进行调试模式启动

2. java在使用> 或者 <, 必须判断是否为null

3. starlight 远程调用，更新版本，更新maven，有无本地更新版本？？？？
4. 生命周期
