# YHHB
    
HomeBridge方便多开的脚本。    
startup multiple homebridge linux shell script.    
   
## 感谢   
这个脚本最初是为了方便自己开多个homebridge使用的，后来发现很多人需要，便整理了下代码并分享出来，希望能帮到大家。    
因为众口难调，所以脚本在自用的基础上加了些配置项，方便大家可以按照自己的实际使用情况及喜好配置。    
最后老规矩，一颗感恩的心，感谢每一位开发者和测试者。    
使用中如果有什么问题，可以加QQ群(群号：107927710)讨论。    

## 部署说明
将YHHB文件夹复制到设备中。    
进入YHHB文件夹，执行如下命令给脚本增加执行权限：    
```
chmod +x ./YHHB ./homebridge
```

## 配置说明    
编辑YHHB文件，找到并且根据自己的情况修改如下部分：
```
# config ###########################################

# 日志文件打印路径
# "${basepath}/logs/" 为脚本所在目录下logs文件
# "/home/pi/YHHB_logs/" 为记录日志到/home/pi/YHHB_logs/目录下
# "" 为不保存
LOG_FILE_PATH="${basepath}/logs/"
#LOG_FILE_PATH="/home/pi/YHHB_logs/"
#LOG_FILE_PATH=""


# 插件目录 不移动插件指明插件所在路径 移动插件设为空
PLUGIN_FILE_PATH=""
#PLUGIN_FILE_PATH="/usr/local/lib/node_modules/"


# 多HomeBridge位置 
# 目录结构例：
# '/home/pi/YHHB/hbs/MiAqaraPlatform/' 配置在该位置的路径
#   '/home/pi/YHHB/hbs/MiAqaraPlatform/config' HomeBridge配置文件路径
#   '/home/pi/YHHB/hbs/MiAqaraPlatform/plugin' HomeBridge插件文件路径 PLUGIN_FILE_PATH为空时有效
# '/home/pi/YHHB/hbs/MiPhilipsLightPlatform/' 配置在该位置的路径
#   '/home/pi/YHHB/hbs/MiPhilipsLightPlatform/config' HomeBridge配置文件路径
#   '/home/pi/YHHB/hbs/MiPhilipsLightPlatform/plugin' HomeBridge插件文件路径 PLUGIN_FILE_PATH为空时有效
hbPaths=(
'/home/pi/YHHB/hbs/BroadlinkRM/'
'/home/pi/YHHB/hbs/YeeLight/'
'/home/pi/YHHB/hbs/MiAqaraPlatform/'
'/home/pi/YHHB/hbs/RaspberryPi/'
'/home/pi/YHHB/hbs/Others/'
'/home/pi/YHHB/hbs/MiOutletPlatform/'
'/home/pi/YHHB/hbs/MiRobotVacuumPlatform/'
'/home/pi/YHHB/hbs/IkonkeOutletPlatform/'
'/home/pi/YHHB/hbs/IkonkeLightPlatform/'
'/home/pi/YHHB/hbs/MiPhilipsLightPlatform/'
'/home/pi/YHHB/hbs/MiFanPlatform/'
);

####################################################
```
**LOG_FILE_PATH**为保留日志文件路径。可以使用绝对路径，也可以使用相对路径，如："${basepath}/logs/"为脚本目录下logs文件，空为不保存日志。    
**PLUGIN_FILE_PATH**插件位置，设为空时在每个子目录里plugin找插件，设为某个目录是，均到该目录内找插件。    
**hbPaths**每个HomeBridge的配置目录，注意：最终的config.json是在每一个配置目录下config内查找。    
推荐目录结构如下：
```
./YHHB/
./YHHB/hbs/
./YHHB/hbs/HomeBridge1/
./YHHB/hbs/HomeBridge1/config/
./YHHB/hbs/HomeBridge1/config/config.json
./YHHB/hbs/HomeBridge1/plugin/
./YHHB/hbs/HomeBridge1/plugin/插件1/
./YHHB/hbs/HomeBridge1/plugin/插件2/
./YHHB/hbs/HomeBridge2/
./YHHB/hbs/HomeBridge2/config/
./YHHB/hbs/HomeBridge2/config/config.json
./YHHB/hbs/HomeBridge2/plugin/
./YHHB/hbs/HomeBridge2/plugin/插件3/
./YHHB/hbs/HomeBridge3/
./YHHB/hbs/HomeBridge3/config/
./YHHB/hbs/HomeBridge3/config/config.json
./YHHB/hbs/HomeBridge3/plugin/
./YHHB/hbs/HomeBridge3/plugin/插件4/
./YHHB/YHHB
./YHHB/homebridge
```

## 参数说明
### 启动
```
bash YHHB start
```
### 关闭
```
bash YHHB stop
```
### 重启
```
bash YHHB restart
```
### 查看版本
```
bash YHHB version
```
### 查看运行状态
```
bash YHHB status
```
示例如下：    
```
pi@raspberrypi:~/hb_dev$ 
pi@raspberrypi:~/hb_dev$ bash YHHB status
[Running] 13299 /home/pi/YHHB/BroadlinkRM/
[Running] 13300 /home/pi/YHHB/YeeLight/
[Running] 13301 /home/pi/YHHB/MiAqaraPlatform/
[Running] 13302 /home/pi/YHHB/RaspberryPi/
[Running] 13303 /home/pi/YHHB/Others/
[Running] 13304 /home/pi/YHHB/MiOutletPlatform/
[Running] 13305 /home/pi/YHHB/MiRobotVacuumPlatform/
[Running] 13306 /home/pi/YHHB/IkonkeOutletPlatform/
[Running] 13310 /home/pi/YHHB/IkonkeLightPlatform/
[Running] 13313 /home/pi/YHHB/MiPhilipsLightPlatform/
[Running] 13319 /home/pi/YHHB/MiFanPlatform/
pi@raspberrypi:~/hb_dev$ 
```

## 开机自启动
脚本自带后台启动功能，自带防止重复启动功能。    
编辑/etc/rc.local文件，加入如下命令：    
```
bash /home/pi/YHHB/YHHB start
```
或    
```
sudo -i -u pi bash /home/pi/YHHB/YHHB start
```
注：sudo -i -u pi为使用pi用户执行脚本，根据自己装的插件是否需要某用户环境决定是否需要加。不加的话是已root用户启动。    
/etc/rc.local文件示例如下：
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Print the IP address
_IP=$(hostname -I) || true
if [ "$_IP" ]; then
  printf "My IP address is %s\n" "$_IP"
fi

if [ -z "`ps -eaf | grep "hass --open-ui" | grep -v grep`" ]; then
    sudo nohup hass --open-ui >> /dev/null 2>&1 &
fi

sudo -i -u pi bash /home/pi/YHHB/YHHB start

exit 0
```
## 版本更新记录
### 0.1.0 (2018年1月6日)
1.提供HomeBridge多开功能，支持是否移动插件，是否记录日志等配置。   