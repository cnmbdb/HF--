# HF-Epay-易支付
HF-聚合支付-易支付

声明：禁止使用本软件（系统）用于任何违法违规业务或项目,造成的任何法律后果允由使用者（或运营者）承担全部责任

作者：呆呆
TG群：https://t.me/HFZChat

----------------------------------------------------------------------------

Nginx ：1.20.1（版本都可以）

MySQL：5.6.50（兼容该版本其他不知道）

简单优化服务器（可不安装，看要求）

PHP安装扩展名称：fileinfo | opcache | imagemagick

1、直接域名访问转跳自动安装页面（安装路径）（可以二级域名）

2、至此网站搭建完毕，请访问后自行修改配置信息！默认管理员账号和密码
     账户：admin
     密码：admin
3、按照成功后可以到【config.php】修改你的配置信息

----------------------------------------------------------------------------

监控端app替换域名教程

然后把app反编译，反编译操作就是搜索这个域名：geren.shoquan.xyz|10.10.80.17（不是第一个就是第二个）
替换成你自己的【监控域名】，然后在打包，把打包好的app
不会操作加群下载教程

----------------------------------------------------------------------------

通道监控（计划任务）两种系统

监控链接示范：http://127.0.0.1/cehsald?user=admin

最好使用宝塔监控
温馨提示：监控最好不要设置太快，不然会出现限制问题

宝塔Windows面板计划任务安装教程 （填写您的监控信息）

计划任务-任务类型：访问URl
任务名称：随便取
执行周期：N分钟：1分钟
URL地址：http://监控域名/cehsald?user=管理员账号

宝塔Linux面板计划任务安装教程 （填写您的监控信息）

计划任务-任务类型：Shell脚本
任务名称：随便取
执行周期：N分钟：1分钟
脚本内容：

有两种指令自己选择一个

----------------------------------------------------------------------------

step=10 #间隔的秒数，不能大于60
for (( i = 0; i < 60; i=(i+step) )); do
php /www/wwwroot/根目录路径/think SendMessage #填写您的根目录路径
sleep $step    
done    
exit 0

----------------------------------------------------------------------------

step=10 #间隔的秒数，不能大于60      
for (( i = 0; i < 60; i=(i+step) )); do    
    curl  -sS --connect-timeout 10 -m 60 'http://监控域名/cehsald?user=管理员账号'   #填写您的监控信息
echo "" 
endDate=`date +"%Y-%m-%d %H:%M:%S"`    
echo "[$endDate] Successful"    
echo "------------------------------------------------" 
sleep $step    
done    
exit 0
