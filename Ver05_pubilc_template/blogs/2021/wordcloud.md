# 关于项目
## 起因
- 寒假的某一天，我躺在沙发上看手机，突然想到了数据分析这个东西，然后我就想，哪里有比较大量的数据，做一做简单的数据分析？
- 看这手里的手机，我想到了——聊天数据！
- 对于学生来说，比较有把握的说，每个人每天都会打开QQ，微信等社交软件，每天都会产生大量的聊天数据，有没有什么方式，可以做一个东西，分析统计一下聊天数据，将结果比较直观地呈现出来，然后我就想到了——词云。
- 确定好做什么东西之后，接下来就是编程语言的选择：这还需要思考吗？当然是Python啦，Python自带了第三方库wordcloud。

## 准备

- 总的来说这个项目还是非常简单的，主要处理两个问题：
  - 一个是怎么获取QQ（微信？）的聊天记录；
  - 词云的使用
    - jieba：jieba库是优秀的中文分词第三方库；
    - wordcloud：wordcloud是优秀的词云展示第三方库，以词语为基本单位，通过图形可视化的方式，更加直观和艺术的展示文本；
    - PIL：Python Imaging Library，已经是Python平台事实上的图像处理标准库了；词云的图像需要我们自己输入，涉及到图像处理，因此也需要该库；

## 资料查阅

- 主要查阅一下消息记录怎么导出为txt文件和词云的基本使用方法；

- 词云已经是一个非常成熟且简单的项目了，网上的资源一大堆，简单看一下，**开整**！！！！

# 项目解析

- QQ消息记录的导出

  - ![xxxxwordcloud_1](https://gitee.com/murphyhou/picgo/raw/master/image/xxxxwordcloud_1.png)
  - ![wordcloud_2](https://gitee.com/murphyhou/picgo/raw/master/image/wordcloud_2.png)
  - ![wordcloud_3](https://gitee.com/murphyhou/picgo/raw/master/image/wordcloud_3.png)

- 打开pycharm（或者其他），建好项目，新建好文件~~上号！冲冲冲！！！（doge~）

- 第三方库的导入

  ``` python
  import jieba
  import numpy as np
  from PIL import Image
  from wordcloud import WordCloud
  # import matplotlib.pyplot as plt
  ```

  

- 需要输入的变量

  ``` python
  txt_filename=input("输入导出的聊天记录的txt文件地址：")#聊天记录获取
  print()
  pic_filename=input("输入背景图片地址：")# 图片获取
  print()
  font_filename=input("输入字体的地址(如果不知道如何获取地址，可输入该地址:C:\Windows\Fonts\Dengb.ttf)：")# 字体获取
  #font_filename=r"C:\Windows\Fonts\Dengb.ttf"
  ```

- 聊天记录读入和词云外形读入

  ``` python
  #聊天记录获取
  with open (txt_filename,'r',encoding='utf-8') as f:
      com_record=f.read()
  # 图片获取
  ground=np.array(Image.open(pic_filename))
  ```

- jieba分词

  ``` python
  #用jieba函数实现文件的分词转换
  sep_list=jieba.lcut_for_search(com_record)##（结巴有三种方式，全模式、精确模式、搜索引擎模式）
  sep_list=" ".join(sep_list)
  ```

- 词云制作

  ``` python
  #词云制作部分
  wc=WordCloud\
  (
      scale=4,#调整图片大小
      font_path=font_filename,#使用的字体库
      
      max_words=500,  #词云显示的最大词数
      
      margin=2,#字体之间的间距
      mask=ground,#背景图片
      background_color='white', #背景颜色
  
      max_font_size=200,
      min_font_size=1,
  
      collocations=False, #避免重复单词
      width=1600,height=1200, #图像宽高，字间距
      
      stopwords=exclude#屏蔽的内容
  )
  wc.generate(sep_list) #制作词云
  ```

- 文件保存

  ``` python
  save_file_name=input("WordCloud将以PNG格式保存，请输入保存的名称：")
  print()
  save_file_name=save_file_name.lower()
  save_file_name=save_file_name+".png"
  wc.to_file(save_file_name) #保存到当地文件
  print()
  print("WordCloud制作完成！")
  print()
  fffff=input("输入任意字符+回车即可退出：")
  ```

- 因为聊天记录中有很多不需要的词语，我们可以将其屏蔽掉

  ``` python
  #用集合实现屏蔽某些单词
  exclude=set()
  flag=True
  print()
  ff=input("是否需要添加屏蔽的关键词？(Y/N):")
  ff=ff.upper()
  if ff=='Y':
      while flag:
          print()
          ex_in = input("请输入需要屏蔽的关键词（输入QUIT可停止添加屏蔽关键词）：")
          if ex_in == "QUIT":
              flag = False
          else:
              #exclude.update(ex_in)
              exclude.add(ex_in)
      print()
      print("屏蔽关键词集合:")
      print(exclude)
  else:
      print()
      print("屏蔽关键词集合为空")
  ```

- 另外，还可以通过pyinstaller将python程序转化成exe文件，通过打包生成的exe文件，包含里该python文件运行的所以第三方库，因此，对于没有python环境的计算机也可以下载使用，非常便利！
- 在资源管理器的带有该py文件的文件夹下，输入 pyinstaller -F 文件名.py,回车键，等待一段时间，会生成exe文件，该exe文件在本文件下的dist文件夹下
- <img src="https://gitee.com/murphyhou/picgo/raw/master/image/wordcloud_5.png" alt="wordcloud_5" style="zoom:50%;" />
- ![wordcloud_6](https://gitee.com/murphyhou/picgo/raw/master/image/wordcloud_6.png)

# 项目完整代码

``` python
# -*- coding : utf-8 -*-
# Time      : 2021/2/11 12:16
# Author    : MurphyHou
# Proj_Name : WordCloud
# File_Name : wordcloud_demo_1.py
# Software  : PyCharm
# Here We Go!

import jieba
import numpy as np
from PIL import Image
from wordcloud import WordCloud

print("tips：可以先将这个黑黑的框框全屏，然后按住ctrl+鼠标滚轮将文字放大到合适的尺寸")
print()
print()
print()

txt_filename=input("输入导出的聊天记录的txt文件地址：")#聊天记录获取
print()

pic_filename=input("输入背景图片地址：")# 图片获取
print()

font_filename=input("输入字体的地址(如果不知道如何获取地址，可输入该地址:C:\Windows\Fonts\Dengb.ttf)：")# 字体获取
#font_filename=r"C:\Windows\Fonts\Dengb.ttf"

#聊天记录获取
with open (txt_filename,'r',encoding='utf-8') as f:
    com_record=f.read()

# 图片获取
ground=np.array(Image.open(pic_filename))

#用集合实现屏蔽某些单词
exclude=set()
flag=True
print()

ff=input("是否需要添加屏蔽的关键词？(Y/N):")
ff=ff.upper()
if ff=='Y':
    while flag:
        print()
        ex_in = input("请输入需要屏蔽的关键词（输入QUIT可停止添加屏蔽关键词）：")
        if ex_in == "QUIT":
            flag = False
        else:
            #exclude.update(ex_in)
            exclude.add(ex_in)
    print()
    print("屏蔽关键词集合:")
    print(exclude)
else:
    print()
    print("屏蔽关键词集合为空")

#用jieba函数实现文件的分词转换
sep_list=jieba.lcut_for_search(com_record)##（结巴有三种方式，全模式、精确模式、搜索引擎模式）
sep_list=" ".join(sep_list)

#词云制作部分
wc=WordCloud\
(
    scale=4,#调整图片大小
    font_path=font_filename,#使用的字体库
    max_words=500,  #词云显示的最大词数
    margin=2,#字体之间的间距
    mask=ground,#背景图片
    background_color='white', #背景颜色

    max_font_size=200,
    min_font_size=1,

    collocations=False, #避免重复单词
    width=1600,height=1200, #图像宽高，字间距

    stopwords=exclude#屏蔽的内容
)

wc.generate(sep_list) #制作词云

save_file_name=input("WordCloud将以PNG格式保存，请输入保存的名称：")
print()

save_file_name=save_file_name.lower()
save_file_name=save_file_name+".png"
wc.to_file(save_file_name) #保存到当地文件

print()
print("WordCloud制作完成！")
print()
fffff=input("输入任意字符+回车即可退出：")
```

# 关于项目的思考

- 关于数据分析可不仅仅是做词云这么简单，大数据时代对数据的分析肯定是重要的，不能仅仅局限于表面上的分析，如果能根据数据做用户画像那就更好了；
- 孰能生巧，对于第三方库的使用第一次肯定是不熟悉的，经过多几次的使用会更加熟悉的！