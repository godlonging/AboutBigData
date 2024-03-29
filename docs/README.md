# Data Process
## Architecture of data process
## Data process software installation
### Kafka
1. 到官網下載kafka
2. 解壓到`/usr/local`目錄並添加權限
```shell script
sudo tar -zxf kafka_2.11-0.10.1.0.tgz -C /usr/local
cd /usr/local
sudo mv kafka_2.11-0.10.1.0/ ./kafka
sudo chown -R root ./kafka
```
3. 簡單測試Kafka
    1. 開啟zookeeper服務
    ```shell script
    cd /usr/local/kafka
    bin/zookeeper-server-start.sh config/zookeeper.properties
    ```
    2. 開啟kafka服務
    ```shell script
    cd /usr/local/kafka
    bin/kafka-server-start.sh config/server.properties
    ```
    3. 建立kafka-topic名為test
    ```shell script
    bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test
    ```
    4. 使用kafka-producer發送消息
    ```shell script
    bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test
    ```
   5. 使用kafka-consumer接受消息
   ```shell script
    bin/kafka-console-consumer.sh ----bootstrap-server localhost:9092 --topic test --from-beginning
    ```
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
1. 下載Spark,解壓到`/usr/local/`並修改文件權限
```shell script
sudo tar -zxf ./spark-2.1.0-bin-without-hadoop.tgz -C /usr/local/
cd /usr/local
sudo mv ./spark-2.1.0-bin-without-hadoop/ ./spark
sudo chown -R root:root ./spark
```
2. 修改spark配置文件spark-env.sh
```shell script
cd /usr/local/spark
sudo cp ./conf/spark-env.sh.template ./conf/spark-env.sh
```
添加一下配置：
```
export SPARK_DIST_CLASSPATH=$(/usr/local/hadoop/bin/hadoop classpath)
```
3. 修改環境變量
```sudo vim ~/.bashrc```
添加以下配置：
```
export JAVA_HOME=/usr/lib/jvm/default-java
export HADOOP_HOME=/usr/local/hadoop
export SPARK_HOME=/usr/local/spark
export PYTHONPATH=$SPARK_HOME/python:$SPARK_HOME/python/lib/py4j-0.10.4-src.zip:$PYTHONPATH
export PYSPARK_PYTHON=python3
export PATH=$HADOOP_HOME/bin:$SPARK_HOME/bin:$PATH
```
生效配置文件
```shell script
source ~/.bashrc
```
4. 檢查spark是否安裝成功
```shell script
cd /usr/local/spark
bin/run-example SparkPi
```
### Cassandra
1.下載Cassandra安裝包並解壓
```shell script
tar -zxvf apache-cassandra-2.1.2-bin.tar.gz -C /usr/local/
sudo mv ./apache-cassandra-2.1.2 ./cassandra
```
2. 創建默認設置目錄並賦予權限
```shell script
sudo mkdir "/var/lib/cassandra"
sudo mkdir "/var/log/cassandra"
sudo chmod 777 /var/lib/cassandra
sudo chmod 777 /var/log/cassandra
```
3. 修改環境變量
```sudo vim ~/.bashrc```
添加以下配置：
```
export CASSANDRA_HOME = /usr/local/cassandra
export PATH = $PATH:$CASSANDRA_HOME/bin
```
4. 啟動Cassandra服務
```shell script
cd /usr/local/cassandra
./bin/cassandra -f
```
### MySQL
1. 更新軟件源並安裝mysql
```shell script
sudo apt-get update
sudo apt-get install mysql-server
```
2. 配置mysql
```shell script
sudo mysql_secure_installation
```
3.檢查mysql服務狀態
```shell script
systemctl status mysql.service
```
### Grafana
1. 下載Grafana安裝包並安裝
```shell script
wget https://dl.grafana.com/oss/release/grafana_6.5.0_amd64.deb
sudo dpkg -i grafana_6.5.0_amd64.deb
```
2. 啟動Grafana服務
```shell script
service grafana-server start
```
3. 使用瀏覽器進入127.0.0.1:3000默認用戶名和密碼均為admin.


