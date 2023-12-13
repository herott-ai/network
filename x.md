> 假设主机A要发送**多播帧**给该**多播地址**。将该**多播地址**的左起第一个字节写成8个比特，第一个字节的最低比特位是1，这就表明该地址是**多播地址**。
>
> 快速判断地址是不是**多播地址**，就是上图所示箭头所指的第十六进制数不能整除2（1,3,5,7,9,B,D,F），则该地址是**多播地址**
>
> 假设主机B，C和D支持多播，各用户给自己的主机配置多播组列表**如下所示**



![img](https:////upload-images.jianshu.io/upload_images/24878825-f274d401c24ad4d4.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

image-20201015001243584

> 主机B属于两个多播组，主机C也属于两个多播组，而主机D不属于任何多播组



![img](https:////upload-images.jianshu.io/upload_images/24878825-1d6c26260c21ba6a.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

image-20201015001535528

> 主机A首先要构建该**多播帧**，**在帧首部中的目的地址字段填入该多播地址**，源地址点填入自己的MAC地址，再加上帧首部中的其他字段、数据载荷以及帧尾部，就构成了该**多播帧**



![img](https:////upload-images.jianshu.io/upload_images/24878825-70e6e705d20e5c20.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

image-20201015002054876

> 主机A将该**多播帧**发送出去，主机B、C、D都会收到该**多播帧**
>
> **主机B和C发现该多播帧的目的MAC地址在自己的多播组列表中**，主机B和C都会接受该帧
>
> 主机D发现该**多播帧**的目的MAC地址不在自己得多播组列表中，则丢弃该**多播帧**

> 给主机配置多播组列表进行私有应用时，不得使用公有的标准多播地址

## IP地址

IP地址属于网络层的范畴，不属于数据链路层的范畴

下面内容讲的是IP地址的使用，详细的IP地址内容在网络层中介绍

### 基本概念



![img](https:////upload-images.jianshu.io/upload_images/24878825-597f8c69867e595b.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

image-20201015104441580

### 从网络体系结构看IP地址与MAC地址



![img](https:////upload-images.jianshu.io/upload_images/24878825-407cbc74e63b0e50.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

image-20201015104913755

### 数据包转发过程中IP地址与MAC地址的变化情况

图上各主机和路由器各接口的IP地址和MAC地址用简单的标识符来表示



![img](https:////upload-images.jianshu.io/upload_images/24878825-77c204bc8181b3ed.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

image-20201015105455043



![img](https:////upload-images.jianshu.io/upload_images/24878825-f12548de1d3cebe1.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

image-20210103212224961.png

> 如何从IP地址找出其对应的MAC地址？
>
> ARP协议

## ARP协议

如何从IP地址找出其对应的MAC地址？

ARP（地址解析协议）

### 流程