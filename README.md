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

# 启动参数 可以附加HomeBridge的启动参数
STARTUP_PARAM=""
#STARTUP_PARAM="-D"
#STARTUP_PARAM="-I"
#STARTUP_PARAM="-D -I"

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
**STARTUP_PARAM**可以为启动HomeBridge附加启动参数。    
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
启动全部homebridge，命令如下：
```
bash YHHB start
```
如果想单独启动某个homebridge，可指定具体要启动的homebridge编号，命令如下：
```
bash YHHB start 2
```
如果想单独启动某些homebridge，可通过逗号作为分割指定具体要启动的homebridge编号，命令如下：
```
bash YHHB start 1,2,3,4
```
### 关闭
关闭全部homebridge，命令如下：
```
bash YHHB stop
```
如果想单独关闭某个homebridge，可指定具体要关闭的homebridge编号，命令如下：
```
bash YHHB stop 2
```
如果想单独关闭某些homebridge，可通过逗号作为分割指定具体要关闭的homebridge编号，命令如下：
```
bash YHHB stop 1,3
```
### 重启
重启全部homebridge，命令如下：
```
bash YHHB restart
```
如果想单独重启某个homebridge，可指定具体要重启的homebridge编号，命令如下：
```
bash YHHB restart 3
```
如果想单独重启某些homebridge，可通过逗号作为分割指定具体要重启的homebridge编号，命令如下：
```
bash YHHB restart 1,3
```
### 查看运行状态
查看全部homebridge运行状态，命令如下：
```
bash YHHB status
```
如果想单独查看某个homebridge运行状态，可指定具体要查看的homebridge编号，命令如下：
```
bash YHHB status 3
```
如果想单独查看某些homebridge运行状态，可通过逗号作为分割指定具体要查看运行状态的homebridge编号，命令如下：
```
bash YHHB status 1,3
```
示例如下：    
```
pi@raspberrypi:~/hb_dev$ 
pi@raspberrypi:~/hb_dev$ bash YHHB status
  [1] [Running]     23125      0-00:01:49   /home/pi/YHHB/hbs/BroadlinkRM/
  [2] [Running]     23139      0-00:01:50   /home/pi/YHHB/hbs/YeeLight/
  [3] [Running]     23856      0-00:00:02   /home/pi/YHHB/hbs/MiAqaraPlatform/
  [4] [Running]     23167      0-00:01:50   /home/pi/YHHB/hbs/RaspberryPi/
  [5] [Running]     23870      0-00:00:02   /home/pi/YHHB/hbs/Others/
  [6] [Running]     23195      0-00:01:50   /home/pi/YHHB/hbs/MiOutletPlatform/
  [7] [Running]     23209      0-00:01:50   /home/pi/YHHB/hbs/MiRobotVacuumPlatform/
  [8] [Running]     23223      0-00:01:49   /home/pi/YHHB/hbs/IkonkeOutletPlatform/
  [9] [Running]     23237      0-00:01:49   /home/pi/YHHB/hbs/IkonkeLightPlatform/
 [10] [Running]     23251      0-00:01:49   /home/pi/YHHB/hbs/MiPhilipsLightPlatform/
 [11] [Running]     23265      0-00:01:50   /home/pi/YHHB/hbs/MiFanPlatform/
pi@raspberrypi:~/hb_dev$ 
```
### 查看配置信息
查看全部homebridge配置信息，命令如下：
```
bash YHHB config
```
如果想单独查看某个homebridge配置信息，可指定具体要查看的homebridge编号，命令如下：
```
bash YHHB config 3
```
如果想单独查看某些homebridge配置信息，可通过逗号作为分割指定具体要查看配置信息的homebridge编号，命令如下：
```
bash YHHB config 1,3
```
示例如下：
```
pi@raspberrypi:~/hb_dev$ 
pi@raspberrypi:~/hb_dev$ bash YHHB config
  [1] HomeBridge_BroadlinkRM                   [000-01-001]    34:EA:34:C7:3F:C8    58001    /home/pi/YHHB/hbs/BroadlinkRM//config/config.json
  [2] HomeBridge_YeeLight                      [000-01-002]    F8:24:41:E3:BE:FF    58002    /home/pi/YHHB/hbs/YeeLight//config/config.json
  [3] HomeBridge_MiAqaraPlatform               [000-01-003]    34:CE:00:88:C5:17    58003    /home/pi/YHHB/hbs/MiAqaraPlatform//config/config.json
  [4] HomeBridge_RaspberryPi                   [000-02-001]    B8:27:EB:EE:AF:1B    58004    /home/pi/YHHB/hbs/RaspberryPi//config/config.json
  [5] HomeBridge_Others                        [000-02-002]    8E:BE:BE:44:91:34    58005    /home/pi/YHHB/hbs/Others//config/config.json
  [6] HomeBridge_MiOutletPlatform              [000-01-004]    34:CE:00:FC:4D:F5    58006    /home/pi/YHHB/hbs/MiOutletPlatform//config/config.json
  [7] HomeBridge_MiRobotVacuumPlatform         [000-01-005]    28:6C:07:23:6E:11    58007    /home/pi/YHHB/hbs/MiRobotVacuumPlatform//config/config.json
  [8] HomeBridge_IkonkeOutletPlatform          [000-01-006]    28:D9:8A:08:35:6D    58008    /home/pi/YHHB/hbs/IkonkeOutletPlatform//config/config.json
  [9] HomeBridge_IkonkeLightPlatform           [000-01-007]    18:FE:34:D1:5A:B4    58009    /home/pi/YHHB/hbs/IkonkeLightPlatform//config/config.json
 [10] HomeBridge_MiPhilipsLightPlatform        [000-01-008]    F0:B4:29:C4:C6:D4    58010    /home/pi/YHHB/hbs/MiPhilipsLightPlatform//config/config.json
 [11] HomeBridge_MiFanPlatform                 [000-01-009]    34:CE:00:F8:C5:20    58011    /home/pi/YHHB/hbs/MiFanPlatform//config/config.json
pi@raspberrypi:~/hb_dev$ 
```
### 查看版本
```
bash YHHB version
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

## 任意路径使用
软连接到$PATH中的某个路径下即可。
```
ln -s /home/pi/YHHB/YHHB /usr/local/bin/YHHB
```

## 版本更新记录
### 0.1.3 (2018-03-13)
1.修复软连接脚本时路径计算问题。    
### 0.1.2 (2018-01-11)
1.运行状态和配置信息拆分为两个查看命令。    
2.配置信息增加显示内容，目前显示序号，名称，端口号，mac地址，ping码，配置文件路径。    
3.运行状态增加已运行时间和序号的显示。    
4.启动，关闭，重启，查看运行状态，查看配置信息全部增加针对某个HomeBridge单独执行的支持。     
### 0.1.1 (2018-01-07)
1.查看状态中增加每个配置的pin码和name显示，方便统一查看。    
2.增加附加参数启动功能，方便通过附加-D -I等参数启动HomeBridge。    
### 0.1.0 (2018-01-06)
1.提供HomeBridge多开功能，支持是否移动插件，是否记录日志等配置。   