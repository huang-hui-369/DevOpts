# JMeter 分布式部署与配置

## JMeter 的原理图，Controller 可以 GUI 模式运行，也可以非 GUI 模式运行

![](img\2021-03-26-15-20-51.png)


## 1. install JMeter Controller in windows
https://jmeter.apache.org/download_jmeter.cgi下载

选择 apache-jmeter-5.4.1.zip
解压 apache-jmeter-5.4.1.zip 到d:/jemter
cd d:/jemter/apache-jmeter-5.4.1/bin
jmeter.bat

![](img\2021-03-26-15-02-38.png)

## 2. install jmeter-plugins-manager
1. 从https://jmeter-plugins.org/install/Install/页面下载 plugins-manager.jar，放到lib/ext目录下，然后重启Jmeter
2. 选项菜单底部可以看到 Plugins Manager
   ![](img\2021-03-26-15-07-17.png)

## 3. 安装配置 jmeter plugin PerfMon

jmeter plugin PerfMon 可以检测被测系统服务器性能

### 1. install jmeter plugin PerfMon in controller

1. 打开 Options --> plugins manager --> 切换到 Available Plugins标签 --> 搜索PerfMon(Servers Performance Monitoring) 并安装


![](img\2021-03-26-15-10-26.png)

2. 搜索jpgc - Standard Set 并安装

### 2. Jmeter配置PerfMon Metrics Collector
1. 右键测试计划 --> add --> listener ->jp@gc - PerfMon Metrics Collector

![](img\2021-03-26-15-32-09.png)

2. 点击jp@gc - PerfMon Metrics Collector，
   add row 添加服务器监听项，
   * CPU
   * Memory
   * swap
   * Disks I/O
   * Network I/O

   ![](img\2021-03-26-15-35-34.png)
   ![](img\2021-03-26-15-36-03.png)

3. 浏览本地文件，选择一个csv文件，用来保存被测服务器的性能信息

   ![](img\2021-03-26-15-37-55.png)

### 3. install PerfMon agent to 被测服务器
需要被测服务器安装java
1. 下载 PerfMon Server Agent: https://github.com/vitoi/perfmon-agent
2. 选择perfmon-serverAgent-2.2.3.zip下载到
   /home/user1/soft/perfmon-agent
3. 解压perfmon-serverAgent-2.2.3.zip
   cd /home/user1/soft/perfmon-agent
   unzpi perfmon-serverAgent-2.2.3.zip -d ./
4. 运行 perfmon-agent
   默认端口 4444
   ./startAgent.sh --udp-port 0 --auto-shutdown
   ```
   $ undera@undera-HP:/tmp/serverAgent$ ./startAgent.sh --udp-port 0 --auto-shutdown
   INFO    2011-11-25 19:48:59.321 [kg.apc.p] (): Agent will shutdown when all clients disconnected
   INFO    2011-11-25 19:48:59.424 [kg.apc.p] (): Binding TCP to 4444
    ```

## install jmeter in linux slave

## 需要jdk1.8

1. download jmeter
https://jmeter.apache.org/download_jmeter.cgiからダウンロード

wget -P /home/user1/jmeter https://ftp.yz.yamagata-u.ac.jp/pub/network/apache//jmeter/binaries/apache-jmeter-5.4.1.tgz

2. 解压 apache-jmeter-5.4.1.tgz
cd /home/user1/jmeter
tar -zxvf apache-jmeter-5.4.1.tgz
cd apache-jmeter-5.4.1/bin

运行命令：
./jmeter -v
如图显示就可以了
    _    ____   _    ____ _   _ _____       _ __  __ _____ _____ _____ ____
   / \  |  _ \ / \  / ___| | | | ____|     | |  \/  | ____|_   _| ____|  _ \
  / _ \ | |_) / _ \| |   | |_| |  _|    _  | | |\/| |  _|   | | |  _| | |_) |
 / ___ \|  __/ ___ \ |___|  _  | |___  | |_| | |  | | |___  | | | |___|  _ <
/_/   \_\_| /_/   \_\____|_| |_|_____|  \___/|_|  |_|_____| |_| |_____|_| \_\ 5.4.1


3. 配置jmter的环境变量
   配置文件/etc/profile 末尾添加一行如下

   export PATH=/home/user1/jmeter/apache-jmeter-5.4.1/bin/:$PATH

   反映环境变量
   source /etc/profile

