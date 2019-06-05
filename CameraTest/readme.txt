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

写成了一个脚本webcamstart.sh
用树莓派做实时影像流服务器，目前只能在局域网用
>>> 派上输入如下命令行：
sudo apt-get update
sudo apt-get install vlc
sudo raspivid -o - -t 0 -w 640 -h 360 -fps 25|cvlc -vvv stream:///dev/stdin --sout '#standard{access=http,mux=ts,dst=:8090}' :demux=h264

[注意demux和=之间不能有空格 -_-!]

然后在局域网其他设备上安装VLC客户端，打开客户端--》媒体--》网络串流--》 输入http://树莓派IP:8090 即可
