# Cloud189Checkin

天翼云盘每日签到一次，抽奖2次<br>
使用方法<br>
1.测试环境为python3.7.6,自行安装python3<br>
2.requirements.txt 是所需第三方模块，执行 `pip install -r requirements.txt` 安装模块<br>
3.可在脚本内直接填写账号密码<br>
4.Python 和需要模块都装好了直接在目录 cmd 运行所要运行的脚本。<br>
<br>
<br>

登录看的以下项目：
> [Cloud189](https://github.com/Dawnnnnnn/Cloud189)
> [cloud189](https://github.com/Aruelius/cloud189)

# 在Docker中使用

1.获取文件到本地
----

```zsh
git clone https://github.com/L-Trump/Cloud189Checkin.git
cd Cloud189Checkin
```

2.构造镜像
-----

```zsh
docker build -t yourname/cloud189checkin .
```

最后有一个点别忘了

3.运行容器
-----

```zsh
docker run -e USERNAME="你的账号" -e PASSWORD="你的密码" -e SCKEY="你的Server酱KEY" -it yourname/cloud189checkin
```

注：如果不需要推送可以忽略`-e SCKEY="你的Server酱KEY"`

使用群晖任务计划实现定时每日定时签到
-----

首先使用ssh连接到群晖，键入`sudo su`并输入密码获取root权限，随后***找一个合适的目录***执行步骤1、2、3，**例**：

```zsh
sudo su
mkdir /volume2/myfiles/docker && cd /volume2/myfiles/docker
git clone https://github.com/L-Trump/Cloud189Checkin.git
cd Cloud189Checkin
docker build -t yourname/cloud189checkin .
docker run -e USERNAME="你的账号" -e PASSWORD="你的密码" -e SCKEY="你的Server酱KEY" -it yourname/cloud189checkin
```

使用`docker ps -a`查找刚刚运行的docker的id，结果如图

![Snipaste_2020-07-16_09-22-46.png](https://xqhma.oss-cn-hangzhou.aliyuncs.com/image/Snipaste_2020-07-16_09-22-46.png)

在这里id为eea2738600f9，记录下后进入群晖的管理页面-控制面板-任务计划-新增-用户定义的脚本

随后在任务设置的运行命令中填入`docker start 你的Dockerid -i`即可：

![Snipaste_2020-07-16_09-27-35.png](https://xqhma.oss-cn-hangzhou.aliyuncs.com/image/Snipaste_2020-07-16_09-27-35.png)

**注：由于该docker在签到完后就会停止运行，群晖在消息里提示意外停止，忽略就好，如果有知道怎么解决的大神欢迎联系我**

# 使用Server酱的推送服务

使用`-e SCKEY="你的KEY"`即可，关于Server酱详见其[官网](https://sc.ftqq.com/3.version)

