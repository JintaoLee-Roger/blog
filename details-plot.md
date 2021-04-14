# matplotlib 科研画图细节

### 1. 安装字体
在linux系统中可能缺少某些字体，而matplotlib自带的字体非常少，画图的时候经常会遇到缺少字体的情况。
以`Times New Roman`为例，简述如何安装字体。

**方法一**

1. 下载字体相关的`.ttf`文件，可以到(Download Free Fonts)[https://www.download-free-fonts.com/]网站
下载相关的字体文件。

2. 将`.ttf`文件移动到 `anaconda3/lib/python3.6/site-packages/matplotlib/mpl-data/fonts/ttf/` 目录下。

3. 删除`.cache/matplotlib`目录，windows系统为`Users\username\.matplotlib`目录。

这种方法只能保证一个虚拟环境下可以使用这种字体，如果想所有虚拟环境都可以使用，则需在相应的虚拟环境下的matplotlib
对应的ttf目录下加入`.ttf`文件，只需将`lib/`改为`env/envname/lib`即可，envname是虚拟环境的名称。


**方法二**

1. 同上，下载字体。

2. 将`.ttf`文件移动到 `~/.local/share/fonts/` 目录下，没有该目录就创建。

3. 在终端执行 `fc-cache -vf` 刷新系统字体缓存。

4. 删除`.cache/matplotlib`目录，windows系统为`Users\username\.matplotlib`目录。

这种方法会为当前用户安装字体，所有的虚拟环境，以及该用户其他的软件都可以使用新字体。

### 2. 保存去掉多余空白区域的图片

```python
plt.savefig('filename', bbox_inches='tight',dpi=600,pad_inches=0.0)
```

`dpi`是图片的分辨率， 如果画的是曲线等可以生成矢量图的图片，尽量保存为矢量图，如`pdf`和`svg`格式。

### 3. 刻度，标题，图例名称 的字体、字体大小
```python
# 标题
fontdict = {'family' : 'Times New Roman', 'weight' : 'normal', 'size' : 18}
plt.xlabel('Ampitude', fontdict=fontdict)

# 刻度
plt.xticks(fontproperties='Times New Roman', size=16)

# 图例名称
plt.legend(['raw', 'output'], prop=fontdict)
```

### 4. subplot 图的大小，子图的间距
```python
# 整张图的大小
plt.figure(figsize=(10, 5)) 

# 子图间距 wspace为水平间隔，hspace为垂直间隔
plt.subplots_adjust(wspace=0.2, hspace=0.2)
```

### 5. 曲线的颜色、线宽、形状
```python
# c为颜色，lw为线宽，label为曲线的legend, marker为点的形状
# linestyle为线的形状
plt.plot(x, y, c='blue', lw=0.8, label='line1', marker='o', 
            linestyle='-', markersize=12)

# 等价于
plt.plot(x, y, 'bo-', lw=0.8, label='line1', markersize=12)
```

