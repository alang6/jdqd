前几天操作失误,导致配置文件重置 恢复方法:

打开控制面板，到定时设定，添加下行定时文件 ,待同步完成后，重新更新cookie

22 * * * * bash /root/jd/git_pull.sh >/dev/null 2>&1


保存后会自动更新,更新时间为每小时的第22分钟，根据网络情况同步需要一定时间，第一次定时任务同步后会被清空,再重新添加本定时文件即可恢复,恢复后添加cookie

或者  手动同步方法：
进入putty（没有可以下载） 登入网址端口22（默认192.168.1.1 视自己设定）
docker ps -a     //查看镜像名称 
docker exec -it jd bash   //bash 前面为镜像的名称 
bash git_pull.sh   //运行同步， 限于网络问题，通常需要多运行两次， 待完全同步成功， 出现添加定时任务完成

重新回浏览器打开 面板， 添加cookie， 保存。




找回之前的备份方法:

下载putty 登陆后输入  cd config/bak   然后输入 ls  察看最后的config.sh文件备份,如config.sh_2021-9-6-6-23-164
##然后输入命令：cp /root/jd/config/bak/config.sh_2021-9-6-6-23-164 /root/jd/config/config.sh -f 回车即可恢复

#####已经添加支持手机运行!!!! 可以用闲置的安卓手机安装App后添加面板设置脚本运行!
######### 安卓手机安装运行方法:[点击查看](https://github.com/hajiuhajiu/jdsign1112/blob/master/icon/Termux.md)


尽量不要用action跑， 否则github封号，如需要github action运行,请注册帐户后先复制或导入其它项目,等一周后再复制本脚本.

低调使用，不要fork！尽量第一时间同步更新脚本。防止失联请收藏gitee备份地址：https://gitee.com/xr2021/jdsign
复制仓库后可以用github action 运行 

Action 打开方式 setting--actions ......Actions permissions
.........Allow all actions...save 



docker 一键安装：

wget  https://gitee.com/xr2021/jd-shell/raw/v3/install_scripts/docker_install_jd.sh -O docker_install_jd.sh && chmod +x docker_install_jd.sh && bash docker_install_jd.sh

安装完成后输入docker设备地址如192.168.1.1:5678 用户名admin密码admin5678 添加cookie，可进入后扫码获得，自行设定各脚本运行时间即可。




青龙拉库命令:
ql repo https://ghproxy.com/https://github.com/hajiuhajiu/jdsign1112.git "jd_|jx_|gua_|jddj_|getJDCookie" "activity|backUp" "^jd[^_]|USER|utils|function|ql"

定时规则0 */4 * * *

一、青龙运行python脚本缺少requests模块，请按以下方式安装：
1、进入青龙容器：docker exec -it qinglong /bin/sh
2、安装requests模块
pip3 install requests
3、安装完成，退出容器
exit

二、青龙安装nodejs模块方法：
1、进入青龙容器：
docker exec -it qinglong /bin/sh
2、进入/ql/scripts目录
cd scripts
4、安装png-js模块
npm install -g png-js
安装jsdom模块
npm install -g jsdom
5、安装完成，退出容器
exit


