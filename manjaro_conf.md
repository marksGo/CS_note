# your manjaro configuration

[toc]

## 中文输入法

我们使用Fcitx5(小企鹅)来解决输入法：

1. 首先，删除fcitx4相关的包：

   ~~~shell
   sudo pacman -Rs $(pacman -Qsq fcitx)
   ~~~

2. 然后，安装fcitx5及其相应的插件：

   ~~~shell
   sudo pacman -S fcitx5 fcitx5-configtool fcitx5-qt fcitx5-gtk fcitx5-chinese-addons
   fcitx5-material-color fcitx-rime
   ~~~

3. 添加环境变量以及默认启动

   - 修改输入法环境变量，使应用可以调用Fcitx5输入法
   - 将下面的内容粘贴到`~/.pam_environment`

   ```
   GTK_IM_MODULE DEFAULT=fcitx
   QT_IM_MODULE DEFAULT=fcitx
   XMODIFIERS  DEFAULT=@im=fcitx
   ```

   - 将下面的内容粘贴到 `~/.xprofile`(每次使用gdm等图形登录时读取并运用里面的设定)

   ```
   fcitx5 &
   ```

4. 配置主题

   - 使用`fcitx5-material-color`这个主题,可以参照: https://github.com/hosxy/Fcitx5-Material-Color

   修改 `~/.config/fcitx5/conf/classicui.conf`

   ```
   # 垂直候选列表
   Vertical Candidate List=False`
   
   # 按屏幕 DPI 使用
   PerScreenDPI=True
   
   # Font (设置成你喜欢的字体)
   Font="思源黑体 CN Medium 13"
   
   #主题
   Theme=Material-Color-DeepPurple
   ```

   

5. 之后,打开System setting--->Virtual KeyBoard:点选Fcitx5。

   ![](/home/minxy/Pictures/Screenshots/Screenshot_20250329_225829.png)

6. 最后，reboot,然后会发现下方状态栏右侧有个键盘图标，鼠标右键可以看到一些东西。

   ![](/home/minxy/Pictures/Screenshots/1.png)

7. system setting --->input method:点击小加号，创建输入法组；然后，点击add input method,

   ![](/home/minxy/Pictures/Screenshots/4.png)

   ​	

8. 然后你最好把那个`only show current langu`取消勾选,找到你的理想输入法（search一下找rime)

   ![](/home/minxy/Pictures/Screenshots/5.png)

   然后Config global configuration
   
   ![](/home/minxy/Pictures/Screenshots/6.png)

## VPN





