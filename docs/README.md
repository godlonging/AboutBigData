# Data Process
## Architecture of data process
## Data process software installation
### Kakfa
### Hadoop
**安裝Java環境:**
1. 到官網下載Java-JDK
2. 解壓到`/usr/lib/jvm`目錄
```shell script
cd /usr/lib
sudo mkdir jvm
sudo tar -zxvf ./jdk-8u162-linux-x64.tar.gz -C /usr/lib/jvm
```
3. 設置環境變量
```shell script
cd ~
vim ~/.bashrc
```
4. 寫入Java環境
```
export JAVA_HOME=/usr/lib/jvm/jdk1.8.0_162
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:$PATH
```
5. 使環境變量生效
```shell script
source ~/.bashrc
```
6. 檢查Java是否安裝成功
```shell script
java -version
```
**安裝Hadoop:**
1. 下載Hadoop,解壓到`/usr/local/`並修改文件權限
```shell script
sudo tar -zxf ./hadoop-3.1.2.tar.gz -C /usr/local/
sudo mv /usr/local/hadoop-3.1.2 /usr/local/hadoop
sudo chown -R root /usr/local/hadoop
```
2. 檢查Hadoop是否安裝成功
```shell script
cd /usr/local/hadoop
./bin/hadoop version
```
**至此單機版Hadoop已經安裝完畢。**



### Spark
### Cassandra
### MySQL
### Grafana
