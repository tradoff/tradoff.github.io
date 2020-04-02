# 终端快捷操作
## 重复上一条命令
### !!
## 使用上一条命令的所有参数
### !*
## 使用上一条命令的最后一个参数
### !$
### ALT + .
### ESC + .


# 为网络接口添加网关(gateway)
## route add default gw 192.168.1.1(网关ip) dev eth0(网络接口)
# 添加DNS
## vi /etc/resolv.conf
### nameserver 8.8.8.8



# arm连wifi
## 扫描
### iwlist wlan0 scan | grep ESSID
## 配置
### vi /etc/wpa_supplicant.conf
#### ctrl_interface=/var/run/wpa_supplicant
#### network={
#### 	ssid="wifi_name"
#### 	psk="password"	#如果没有密码则此项改为key_mgmt=NONE
#### }
## 连接
### wpa_supplicant -B(ackgroud，后台运行) -D(river，驱动：nl80211,wext) wext -i(nterface，网络接口) wlan0 -c(onfigure，配置文件) /etc/wpa_supplicant.conf -d(ebugging verbosity，调试详细程度，-dd更详细)
## 检查
### wap_cli -i wlan0 status
#### 若wpa_state=COMPLETED则为连接成功
## 设置IP、掩码(ifconfig)、网关(route add)或者动态获取IP(udhcpc -i wlan0)



# 命令行修改文件
## sed -i 's/source/destination/g' file.txt


# 调整屏幕亮度(backlight)
## echo 100 > /sys/class/backlight/intel_backlight/brightness


# 开机脚本(startup)
## /etc/rc.local


# 缺失文件，查找对应安装包
## apt-file find filename


# 解压img文件
## cpio -idmv < filename.img


# 解压RPM文件
## rpm2cpio filename.rpm | cpio -idm


# dns配置
## /etc/resolv.conf 
### nameserver 8.8.8.8


# 清除dns缓存
## sudo /etc/init.d/dns-clean start

# 开机运行程序
## /etc/rc.local

# 撤销unzip
## zipinfo -l1 filename.zip > filenameinfo
## sed -i "s/^/{unzip_dir}/g" filenameinfo
## cat filenameinfo | xargs -d "\n" rm -rf
## rm filenameinfo 

# 删除内核版本 boot kernel
## uname -a
### 确认当前内核版本
## dpkg --get-selections | grep linux
### 列出所有内核版本
## sudo apt-get purge linux-*[版本号]*
### 删除指定版本，通常会自动更新grub文件，若否，手动更新：
## sudo update-grub

# 更改apt源
## sudo vim /etc/apt/sources.list

# 唤出ubuntu更新
## sudo update-manager -cd

# 解决vim缺少lua
## sudo dpkg --configure -a
## sudo apt install vim-nox

# 重启输入法 restart inputmethod
## pidof fcitx | sudo xargs kill
## pidof sogou-qimpanel | sudo xargs kill
## fcitx &
## sogou-qimpanel &

# vim非贪婪匹配
## .\{-}可以实现.*的非贪婪匹配，.\{-1,}可以实现.+的非贪婪匹配

# 热点wifi编辑
## nm-connection-editor

# 命令行配置代理network proxy
## gsettings
