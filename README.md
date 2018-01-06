# YHHB
    
HomeBridge方便多开的脚本。
startup multiple homebridge linux shell script.
   
## 感谢   
这个脚本最初是自用的，后来发现很多人需要，便分享出来，希望能帮到大家。    
因为众口难调，所以脚本在自用的基础上加了很多配置，大家可以按照自己的使用喜好配置。    
最后老规矩，一颗感恩的心，感谢每一位开发者和测试者。    

## 配置说明    
编辑YHHB文件，如下部分：
```
# config ###########################################

# 指定启动用户 空为不指定
#STARTUP_USER="pi"
STARTUP_USER=""


# 日志文件打印路径
# "${basepath}/logs/" 为脚本所在目录下logs文件
# "/home/pi/YHHB_logs/" 为记录日志到/home/pi/YHHB_logs/目录下
# "" 为不保存
LOG_FILE_PATH="${basepath}/logs/"
#LOG_FILE_PATH="/home/pi/YHHB_logs/"
#LOG_FILE_PATH=""


# 插件目录 不移动插件指明插件所在路径 移动插件设备空
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
STARTUP_USER为启动HomeBridge使用用户，留空使用当前用户。    
LOG_FILE_PATH为保留日志文件路径。可以使用绝对路径，也可以使用相对路径，如："${basepath}/logs/"为脚本目录下logs文件，空为不保存日志。    
PLUGIN_FILE_PATH插件位置，设为空时在每个子目录里plugin找插件，设为某个目录是，均到该目录内找插件。    
hbPaths每个HomeBridge的配置目录，注意：最终的config.json是在每一个配置目录下config内查找。    
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
# 启动HomeBridge
```
bash YHHB start
```
# 关闭HomeBridge
```
bash YHHB stop
```
# 重启HomeBridge
```
bash YHHB restart
```
# 查看当前脚本版本
```
bash YHHB version
```
# 查看当前运行状态
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

