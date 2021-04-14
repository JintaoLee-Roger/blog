# 界面美化

修改top bar的字体大小等
默认的  sudo vim /usr/share/gnome-shell/theme/ubuntu.css
/* GLOBALS */
stage {
   font-family: Cantarell, Sans-Serif;
   font-size: 18pt; /* here */
   color: #eeeeec; }
此处修改的是全局字体，菜单栏图标下的字体也放大了

修改chrome地址栏字体大小
暂时无法单独修改，可以整体调整chrome的scale factor
sudo vim /usr/share/applications/google-chrome.desktop
在所有的 Exec= 后面加上 --force-device-scale-factor=n %U
n自己设置，我用的是1.5

安装youcompleteme
需要安装 clang>7.0 cmake new inversion
使用bundle 安装youcompleteme
然后进入 ~/.vim/bundle/YouCompleteMe/ 运行
git submodule update --init --recursive
python3 install.py --clang-completer

