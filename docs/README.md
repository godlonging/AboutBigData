# Data Process
## Architecture of data process
## Data process software installation
### Kakfa
### Hadoop
**安裝Java環境:**
1. 到官網下載Java-JDK
2. 解壓到`/usr/lib/jvm`目錄
```shell
cd /usr/lib
sudo mkdir jvm
sudo tar -zxvf ./jdk-8u162-linux-x64.tar.gz -C /usr/lib/jvm
```
3. 設置環境變量
```shell
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
```
source ~/.bashrc
```
6. 檢查Java是否安裝成功
```
java -version
```
**安裝Hadoop:**



### Spark
### Cassandra
### MySQL
### Grafana
