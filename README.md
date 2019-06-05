# CVFX-HW6-17
## Take videos by yourselves
{%youtube 12ODHAw2cjM %}

## Make these visual effects with ORB-SLAM2
{%youtube PIeZHb3VFAs %}
## Make these visual effects with any post-production software
{%youtube ZtHPBMFWa18 %}
## Compare above methods
| metric | ORB-SLAM2 | AE |
| -----| ------| ------ |
|與原影片符合程度   |  lose  | win |
|相機移動模擬精準度   |  lose  | win |
|擬真程度   |  lose  | win |
|方便程度   |  lose  | win |
|潛力   |  win  | lose |
## ORB-SLAM2 method process
會先將用手機拍的video, 藉由opencv拆成一個個frame, 來配合ORB-SLAM2的輸入格式
![](https://i.imgur.com/tbjpxuY.png)

得到ORB-SLAM2 output 的 trajectory file, 會發現並不是每一個frame都可以成功的抓到
camera 移動方向, 因此我們用內插法補齊
![](https://i.imgur.com/yJGfevH.png)

接著我們使用unity parse 補齊後的trajectory file,
創一個canvas播放原影片, 並透過parse後的結果來移動camera 和 canvas
來製造出visual effects
![](https://i.imgur.com/A6BPkR3.png)

## AE method process
使用After Effect內建的3D Camera Tracker功能來分析影片，分析完畢後可以得到影片中的特徵點，因此顏色較一致的地方(如一片白的牆壁和光線太亮的地板)較無法抓到特徵點，主要抓取到的是角點。將三個特徵點相連可以建立平面，再把目標的物件放上平面微調即可。

![](https://i.imgur.com/T7ne5fP.png)

![](https://i.imgur.com/5TcHfqg.png)

從Cinema4D可以看到3D空間的樣子，比較類似Unity呈現的方式，能夠看到透過特徵點運算得出的Camera移動軌跡以及我們另外加入的物件(皮卡丘影片)，原理也和上面的做法類似，是將另外加入的物件擺放在虛擬3D空間中並且移動攝影機達成AR的效果。3D Camera Tracker算出的Camera軌跡精確度非常高，包括走路造成的上下晃動都有偵測到，因此效果更為逼真。

![](https://i.imgur.com/S4zsZYH.png)

從上往下看可以看出，攝影機呈現一直往前移動的軌跡。

![](https://i.imgur.com/FcrQU23.png)

## Make some special effects based on the pose information, such as rotating, zooming in or out && Insert a 3D model to your video

如最上面的兩個影片內容
我們成功將3D model 放入影片中並達到旋轉的效果


