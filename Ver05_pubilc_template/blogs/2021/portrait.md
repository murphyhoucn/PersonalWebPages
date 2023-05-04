# 关于项目

## 起因

举国同庆盛世中华！2021年的国庆节即将到来，国庆的氛围也逐渐上来了。2019年的时候，微信出来一个带国旗的头像的功能，今天看公众号的时候发现今年又有公众号在做国旗头像了，国旗渐变色与头像叠加效果，感觉效果还不错，不过关注公众号什么的太麻烦了，那就自己手撸代码写一个吧！



## 资料查阅

Python简单的图像出来PIL库就够了，好像也不需要其他什么东西了！

国旗下载地址：[中华人民共和国国旗_中国政府网 (www.gov.cn)](http://www.gov.cn/guoqing/guoqi/index.htm)

# 项目解析

- 总共涉及到的是三张图片，一张是五星红旗的图片，一张是自己的头像，还有一张是程序生成的图片；
- 图像格式无非是png或者jpg，两者用什么没有特别要求，差别不大；
- 比较棘手的问题是国旗和头像的比例问题，微信或QQ等社交平台的头像一般都是正方形的，那就需要把国旗做裁切，裁切为正方形，不能简单地把国旗图像变成正方形，比例变化会导致国旗变形的；
- 裁切成方形的国旗与图像不能直接叠加，因为图像本身大小不一样，必须先让两者大小一样的时候才能做叠加，至于将国旗变为头像大小还是头像变成国旗大小，其实效果应该差不多，但是我考虑到了，国旗图像裁切后的大小比头像的大小是要大的，把大的缩放为小的清晰的不会下降，但是将小的图像缩放为大的图像，清晰度是会下降的，因此最后采用了将国旗大小重整为头像大小，然后进行叠加；
- 另一个需要处理的问题是，渐变效果的实现，其实做一个嵌套的循环遍历整个图像，然后把颜色变淡应该可以实现渐渐效果；
- 最后一步是将两者做叠加，然后保存图像。

# 项目完整代码

``` python
from PIL import Image

# 读取图片

name=input("请输入头像名称：")
form=input("请输入文件格式（jpg/png）：")
portrait = Image.open(str(name)+'.'+str(form))

The_flag_of_China = Image.open('国旗.png')

# 获取国旗的尺寸
x,y = The_flag_of_China.size

# 关于裁切尺寸的问题具体看下文的关于cut方法的坐标图示。
cut=(50, 30, 550, 530)
area = The_flag_of_China.crop(cut)


# 测试代码：生成裁切后的图像，看一下效果，如果裁切效果不好的话，重新修改上面的cut尺寸（类似反馈doge）！
# cut_name='flag.png'
# area.save(cut_name)

# 头像的尺寸
w,h = portrait.size

# 国旗尺寸变成头像尺寸
area = area.resize((w,h))

# 渐变色设置
for i in range(w):
    for j in range(h):
        pixelcolor = area.getpixel((i, j))
        parameter = 260-i//3   #参数都是多次运行程序测试出来的，可以根据需要进行更改
        if parameter < 0:
            parameter=0
        pixelcolor = pixelcolor[:-1] + (parameter,)
        area.putpixel((i, j), pixelcolor)  
# //：向下取整做除法
# getpixel函数是用来获取图像中某一点的像素的RGB颜色值，getpixel的参数是一个坐标点（x,y）;
#putpixel函数是用来在指定位置画一像素，其中(x,y)是坐标，pixelcolor是像素的颜色.


# 粘贴到头像并保存 
portrait.paste(area,(0,0),area)
portrait.save(str(name)+'_flag.png',quality=100, subsampling=0)
```



PS：关于裁切尺寸的问题具体看下文的关于cut方法的坐标图示

![图示](https://gitee.com/murphyhou/picgo/raw/master/image/%E5%9B%BE%E7%A4%BA.png)



生成头像效果

![Murphy](https://gitee.com/murphyhou/picgo/raw/master/image/Murphy.png)

# 关于项目的思考

- 使用APP等生成带有国旗的头像应该是一件非常容易的事情，但是如果运行python程序来做这件事的话，让人感觉就是非常复杂了，并且不是所有人都有一个带有python开发环境的电脑，所以，用这段程序用的人应该不会有多少；

- 程序本身没有图像化操作界面，这让使用的人会更少了；
- 程序功能单一，应用范围太窄了，且如果图像格式方面有什么问题的话，估计程序运行的效果不会很好！