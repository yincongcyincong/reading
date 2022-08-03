## idea安装步骤
new project 选择android， 语言选择kotlin
![image](https://user-images.githubusercontent.com/24344673/181235704-d560d453-73e6-4c65-816a-caddec26af22.png)
perference -> appearance -> system setting -> android sdk -> sdk tools 下载如图所示
![image](https://user-images.githubusercontent.com/24344673/181236046-1290c282-e3cc-4f1b-ba6d-2f0a5b00731e.png)
cd /Users/yincong/Library/Android/sdk/cmdline-tools/latest/bin & ./sdkmanager --channel=3 emulator （这样就能设置测试桌面）

![image](https://user-images.githubusercontent.com/24344673/181236162-84630e91-4acb-421c-b199-d1ce9fef69ee.png)

编译崩溃 “Installed Build Tools revision 32.0.0 is corrupted. Remove and install again using the SDK Manager.”
cd /Users/yincong/Library/Android/sdk/build-tools/33.0.0 & cp d8 dx & cp d8.jar dx.jar    

### 自己安装镜像：
sdkmanager "system-images;android-28;default;x86"   
avdmanager create avd —n android28 —-package "system-images;android-28;default;x86"  (x86可能会有问题，可以安装amd64)   
emulator @test1   

