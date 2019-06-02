使用原装的Camera
Step 1: 硬件连线
Step 2：打开Camera的设置
    $ sudo raspi-config
    选择 5 Interfacing Options -> P1 camera -> enable

拍一张照片,保存为image.jpg
$ raspistill -o image.jpg
[可以先执行 $ sudo apt-get install eom ，安装一个图片浏览软件，执行 $ eom image.jpg 查看图片]

raspivid -o 3.h264 -w 320 -h 240 -t 10000
播放视频
$ omxplayer *.*

参考《树莓派(Raspberry Pi)实战指南》一书的第11章的11.3编写了两个python程序实现照相和拍视频，主要利用了一个picamera包
