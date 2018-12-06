# 4.0版本扩容教程

#### 由于4.0版本缩小了镜像，所以刷完之后可用空间只有100多mb，本扩容教程理论上支持大部分linux系统。<br>
_______
## 注意！！！
### `本方法必须使用另外一个linux机器进行操作`
______
### 首先对TF卡重新进行一次分区。<br>
1.在终端运行 cat /sys/block/mmcblk0/mmcblk0p2/start<br>
2.记下返回的数字<br>
3.sudo fdisk /dev/mmcblk0<br>
* 输入d 回车<br>
* 2 回车<br>
* n 回车<br>
* p 回车<br>
* 2 回车<br>
* 将刚才数字打上 回车<br>
* 再按一次回车<br>
* w 回车<br>
_____
### 此时应该显示:
### The partition table has been altered.Calling ioctl() to re-read partition table.Re-reading the partition table failed.: Device or resource busyThe kernel still uses the old table. The new table will be used at the next reboot or after you run partprobe(8) or kpartx(8).<br>
#### `如果没有显示也不要紧,步骤可以继续`<br>
_______
4.sudo reboot 重新启动<br>
5.重启之后运行 sudo resize2fs /dev/mmcblk0p2<br>
#### `至此扩容完毕 可以运行df -h 查看一下`
_____
## `分区扩容过程如果出现需要删除签名的情况，输入y或者n都是可以的，然后步骤继续就可以了。`
