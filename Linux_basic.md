
---
## 将软件添加到应用程序菜单
1. 创建一个`.desktop`文件
```shell
nano ~/.local/share/applications/<软件名>.desktop
``` 
2. 编辑`.desktop`文件
```shell
[Desktop Entry]
Name=XXX                    # 要显示的名字(可以设置成多语言)           
Exec=/usr/local/bin/XXXX    # 可执行程序的路径
Icon=/usr/local/bin/XXX.png # 显示在桌面的图标
Type=Application            # 应用类型
Terminal=false              # 打开的时候会弹出终端,使用false禁止弹出
```
3. 赋予快捷方式可执行权限
```shell
sudo chmod +x ~/.local/share/applications/<软件名>.desktop
``` 
