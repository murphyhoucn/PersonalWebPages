# 关于项目

## 起因

- 人工神经网络与深度学习基础通识课课程展式



## 资料查阅

- Dlib

``` markdown
一个机器学习的开源库，包含了机器学习的很多算法，使用起来很方便，直接包含头文件即可，并且不依赖于其他库（自带图像编解码库源码）。Dlib可以帮助您创建很多复杂的机器学习方面的软件来帮助解决实际问题。目前Dlib已经被广泛的用在行业和学术领域,包括机器人,嵌入式设备,移动电话和大型高性能计算环境。

```

- PaddlePaddle百度飞桨

``` markdown
PaddleHub 是基于 PaddlePaddle 开发的预训练模型管理工具，可以借助预训练模型更便捷地开展迁移学习工作，PaddleHub 目前的预训练模型覆盖了图像分类、目标检测、词法分析、Transformer、情感分析五大类别。未来会持续开放更多类型的深度学习模型，如语言模型、视频分类、图像生成等预训练模型。
```

- DeepLabv3+

``` markdown
DeepLabv3+ 是Google DeepLab语义分割系列网络，通过encoder-decoder进行多尺度信息的融合，同时保留了原来的空洞卷积和ASSP层， 其骨干网络使用了Xception模型，提高了语义分割的健壮性和运行速率。
```



# 项目解析

- 对比分析使用DLib和DeepLabV3两种方法对人像的处理效果
- 其实两种算法没有什么交集，至少我目前只了解过这两中简单的人像处理方法，于是设计实验对比分析

# 项目完整代码

crawler.py

```python
# -*- coding : utf-8 -*-
# Time      : 2021/3/31 21:09
# Author    : MurphyHou
# Proj_Name : crawler_pic
# File_Name : crawler_test1.py
# Software  : PyCharm
# Here We Go!


from urllib import request
import re
import ssl

file_path = input("请输入保存图片的地址(eg:D:/crawler/):")
# file_path='D:/crawler/'

uid=input("请输入uid:")
# fid=input("请输入fid：")
# url=input("请输入url：")

a=int(input("请输入爬取图片的起始页数:"))
b=int(input("请输入爬取图片的结束页数:"))


#需要将下面url里面的  uid&value=后面的数字换成所要爬取用户的uid，，还需要将containerid=这个替换成所要爬取用的的fid
base_url = 'https://m.weibo.cn/api/container/getIndex?is_hot[]=1&is_hot[]=1&jumpfrom=weibocom&type=uid&value='+uid+'&containerid=107603'+uid+'&page='
# print(base_url)
# base_url = 'https://m.weibo.cn/api/container/getIndex?is_hot[]=1&is_hot[]=1&jumpfrom=weibocom&type=uid&value=6391766227&containerid=1076036391766227&page='

header = \
    {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.3497.100 Safari/537.36Mozilla/5.0 (iPhone; CPU iPhone OS 11_0 like Mac OS X) AppleWebKit/604.1.38 (KHTML, like Gecko) Version/11.0 Mobile/15A372 Safari/604.1',
    'Accept': 'application/json, text/plain, */*',
    'Referer': 'https://m.weibo.cn/u/' + uid
    # 'Referer': 'https://m.weibo.cn/u/6391766227'  # 这个需要改成所要爬取用户主页的手机版本下的url
    }

context = ssl._create_unverified_context()

for i in range(a, b+1):
    try:
        realurl = base_url + str(i)
        req = request.Request(url=realurl, headers=header)
        # resp = requests.get(realurl, headers=header)
        resp = request.urlopen(req, context=context).read().decode()
        print('***************正在下载第' + str(i) + '页的图片***************')
        # 先获取所有的large里面的url，注意观察，大图的url中都包含/large,那么我们获取所有的url然后过虐掉不包含/large的url就行了
        pat = '"url":"(.*?)"'
        list1 = re.compile(pat).findall(resp)
        list2 = filter(lambda url: url.find('/large') != -1, list1)
        list2 = list(list2)
        for j in range(0, len(list2) - 1):
            pic_url = list2[j].replace('\/', '/')
            request.urlretrieve(pic_url, file_path + str(i) + str(j) + '.jpg')
        print('###############第' + str(i) + '页的图片下载完成###############')

    except Exception as error:
        print(error)
```

rename.py

``` python
# -*- coding : utf-8 -*-
# Time       : 2021/5/24 19:53
# Author     : MurphyHou
# Proj_Name  : Python_Project
# File_Name  : rename_no_function.py
# Software   : PyCharm
# =======Here We Go!=======

import os
# os 顾名思义，就是与操作系统相关的标准库。如：文件，目录，执行系统命令等。
import numpy as  np
# NumPy(Numerical Python) 是 Python 语言的一个扩展程序库，支持大量的维度数组与矩阵运算，此外也针对数组运算提供大量的数学函数库。

print("该程序会把某一个路径下的所有的某一种文件格式重命名为相同类型的命名格式！")

# 求路径的集合
c = input("请输入需要重命名的文件分布的文件夹在多个还是一个（D/S）：")
c=c.upper()


if c == 'S':
    num_file=1
    # 如果无需要命名的文件都在同一个文件夹中
    path = input("请输入文件的地址:")
    # print(path)   #字符串
    path = [path]
    # print(path)   #以字符串为元素的列表

elif c == "D":
    # 如果我需要命名的文件分布在不同文件夹中
    num_file = eval(input("请输入需要重命名的文件分布的文件夹的个数："))
    path = []
    for i in range(num_file):
        path.append(input("请输入文件的地址:"))
    # print(path)
else:
    print("!!!!!!!error")
    exit()


# 这一部分是重命名文件
rename_style = input("请输入你需要的文件的重命名的前缀（例如：5_20_s）:")
file_format = input("请输入你想要修改的文件的格式(例如：.jpg):")

for j in range(num_file):
    filelist = os.listdir(path[j])
    total_num = len(filelist)
    # print(total_num)
    i = 0
    for item in filelist:
        if item.endswith(file_format):
            src = os.path.join(os.path.abspath(path[j]), item)
            dst = os.path.join(os.path.abspath(path[j]), rename_style + str(i) + file_format)
            try:
                os.rename(src, dst)
                print('converting %s to %s ...' % (src, dst))
                i = i + 1
            except:
                continue

    print('total %d to rename & converted %d %s' % (total_num, i, file_format))
    # print('i = %d'%(i))
```

DeepLabv3.py

``` python
# -*- coding : utf-8 -*-
# Time      : 2021/3/31 19:50
# Author    : MurphyHou
# Proj_Name : handle_pic
# File_Name : handle.py
# Software  : PyCharm
# Here We Go!

import os
import cv2
import numpy as np
import paddlehub as hub


# 计算黑白图像中的白色区域面积
def 计算白色区域面积(im):
    bodyArea = 0
    h, w = im.shape
    for col in range(w):
        for row in range(h):
            if im[row, col] != 0:
                bodyArea += 1
    return bodyArea


# 提取特定颜色区域
def 提取特定颜色区域(hsv_img, lower_hsv, high_hsv):
    lowerb = np.array(lower_hsv)                                    #提取颜色的低阈值
    upperb = np.array(high_hsv)                                     #提取颜色的高阈值
    return cv2.inRange(hsv_img, lowerb, upperb)


# 从彩色图片中提取皮肤区域
def 提取皮肤区域(imColor, imMask):
    hsv_img = cv2.cvtColor(imColor, cv2.COLOR_BGR2HSV)
    color_area = 提取特定颜色区域(hsv_img, [5, 0, 0], [20, 255, 255])
    return cv2.bitwise_and(color_area, imMask)


if __name__ == "__main__":
    # 当前文件夹
    base_dir = os.path.abspath(os.path.dirname(__file__))

    # 加载模型
    human_seg = hub.Module(name='deeplabv3p_xception65_humanseg')

    print('1) 正在提取人体轮廓...')

    # 获取当前文件目录
    model_path = os.path.join(base_dir, 'models/')
    # 获取文件列表
    lst_image = [model_path + f for f in os.listdir(model_path)]

    # 人像抠图并放在自动生成的humanseg_output文件夹中
    results = human_seg.segmentation(data={'image': lst_image})

    print('2) 正在计算皮肤区域面积...')
    # 去除背景后的文件目录
    human_body_path = os.path.join(base_dir, 'humanseg_output/')
    # 获取文件列表
    lst_human_body = [human_body_path + f for f in os.listdir(human_body_path)]

    for f in lst_human_body:
        imColorful = cv2.imread(f, cv2.IMREAD_UNCHANGED)
        # a) 提取alpha通道(人体部分为白，其余为黑),计算人体部分的面积
        _, _, _, a_channel = cv2.split(imColorful)
        bodyArea = 计算白色区域面积(a_channel)
        bodyArea+=0.00001
        # b) 计算彩色图片中皮肤的面积.imSkin中白色部分代表皮肤区域
        imSkin = 提取皮肤区域(imColorful, a_channel)
        skinArea = 计算白色区域面积(imSkin)

        # c) 计算皮肤占身体的比例并通过阈值做判断
        skinPercent = int(100*skinArea/bodyArea)

        # d) 将models文件夹中的图片重命名，加skinPercent作为前缀
        folder, name_and_ext = os.path.split(f)
        name, extension = os.path.splitext(name_and_ext)
        os.rename(model_path + name + '.jpg', model_path + str(skinPercent) + '-' + name + '.jpg')
        print('\t{}.png 比例:{}'.format(name, skinPercent))

    print('3) 图片分析完成！')



imColorful = cv2.imread(f, cv2.IMREAD_UNCHANGED)
# a) 提取alpha通道(人体部分为白，其余为黑),计算人体部分的面积
_, _, _, a_channel = cv2.split(imColorful)
bodyArea = 计算白色区域面积(a_channel)
bodyArea += 0.00001
# b) 计算彩色图片中皮肤的面积.imSkin中白色部分代表皮肤区域
imSkin = 提取皮肤区域(imColorful, a_channel)
skinArea = 计算白色区域面积(imSkin)
# c) 计算皮肤占身体的比例并通过阈值做判断
skinPercent = int(100 * skinArea / bodyArea)
# d) 将models文件夹中的图片重命名，加skinPercent作为前缀
folder, name_and_ext = os.path.split(f)
name, extension = os.path.splitext(name_and_ext)
os.rename(model_path + name + '.jpg', model_path + str(skinPercent) + '-' + name + '.jpg')
print('\t{}.png 比例:{}'.format(name, skinPercent))
```

dlib.py

```  python
# -*- coding : utf-8 -*-
# Time      : 2021/6/3 19:50
# Author    : MurphyHou
# Proj_Name : handle_pic
# File_Name : seperate_face.py
# Software  : PyCharm
# Here We Go!


import dlib         # 人脸识别的库dlib
import numpy as np  # 数据处理的库numpy
import cv2          # 图像处理的库OpenCv
import os

system_path=input("输入地址：")
system_path2=system_path+'/face'
pic_num=0;
for filename in os.listdir(system_path):
    # if filename.endswith("jpg") or filename.endswith("png"):
    if filename.endswith("jpg"):
        pic_num+=1

print(pic_num)

for count in range(pic_num):

    # 获取人脸检测器
    detector = dlib.get_frontal_face_detector()
    # 预测人脸关键点
    predictor = dlib.shape_predictor('shape_predictor_68_face_landmarks.dat')

    # 读取图像
    path = "pic/"
    path=path+str(count)+".jpg"
    print(path)
    # path="pic/0.jpg"
    img = cv2.imread(path)

    # Dlib 检测
    dets = detector(img, 1)

    print("pic {}.jpg have {} faces\n".format(count,len(dets)))

    # 记录人脸矩阵大小
    height_max = 0
    width_sum = 0

    # 计算要生成的图像 img_blank 大小
    for k, d in enumerate(dets):

        # 计算矩形大小
        # (x,y), (宽度width, 高度height)
        pos_start = tuple([d.left(), d.top()])
        pos_end = tuple([d.right(), d.bottom()])

        # 计算矩形框大小
        height = d.bottom()-d.top()
        width = d.right()-d.left()

        # 处理宽度
        width_sum += width

        # 处理高度
        if height > height_max:
            height_max = height
        else:
            height_max = height_max

    # 绘制用来显示人脸的图像的大小
    print("窗口大小："
          , '\n', "高度 / height:", height_max
          , '\n', "宽度 / width: ", width_sum)

    # 生成用来显示的图像
    if(height_max!=0 and width_sum!=0):
        img_blank = np.zeros((height_max, width_sum, 3), np.uint8)
    else:
        print("pic {}.jpg have {} faces\n".format(count, len(dets)))
        continue
    # 记录每次开始写入人脸像素的宽度位置
    blank_start = 0

    # 将人脸填充到img_blank
    for k, d in enumerate(dets):

        height = d.bottom()-d.top()
        width = d.right()-d.left()

        # 填充
        for i in range(height):
            for j in range(width):
                    img_blank[i][blank_start+j] = img[d.top()+i][d.left()+j]
        # 调整图像
        blank_start += width

    # cv2.namedWindow("img_faces")#, 2)
    # cv2.imshow("img_faces", img_blank)
    cv2.imwrite(os.path.join(system_path2 , str(count)+'_face.jpg'), img_blank)
    cv2.waitKey(0)
```

# 关于项目的思考

![image-20210713000055343](figure.assets/image-20210713000055343.png)
