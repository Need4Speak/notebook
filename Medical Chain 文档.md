---
title: Medical Chain 文档 
tags:文档,配置,运行
grammar_cjkRuby: true
---


1. build项目jar包：
* 在`MedicalChain-MPBFT\`目录下执行`mvn -Dmaven.test.skip=true  assembly:assembly`命令，将会在`MedicalChain-MPBFT\target`下生成`MedicalChain-MPBFT-1.0-SNAPSHOT.jar`。
	
2. 自动生成json配置文件的方法
* 打开`MedicalChain-MPBFT\src\test\com\pancake\util\RunUtil.java`
* 修改函数`getNodes()`函数中的ip
```
    public NetAddress[] getNodes() {
        NetAddress[] nodes = {new NetAddress("203.195.231.164", 8000),
                new NetAddress("111.230.222.202", 8000),
                new NetAddress("139.199.18.78", 8000),
                new NetAddress("129.204.79.50", 8000)};
        return nodes;
    }
```
* 运行`generateConfigFile()`函数，生成四个配置文件，路径为`MedicalChain-MPBFT\nodeX.json`

3. 节点环境配置

* 每台机器所需的文件如下：

![节点所需文件](./images/1552459908725.png)

* `privateKey.txt`和`publicKey.txt`可以在`MedicalChain-MPBFT\src\main\resources\`中找到
* `MedicalChain-MPBFT-1.0-SNAPSHOT.jar`由`maven build` 生成

4. 系统启动流程

* 执行 `java -jar MedicalChain-MPBFT-1.0-SNAPSHOT.jar  -v node1.json`启动`Validator`
* 执行 `java -jar MedicalChain-MPBFT-1.0-SNAPSHOT.jar  -t node1.json`在节点1上启动`Transaction Transmitter`

5. mongodb dump 命令

```
mongoexport -d BlockChain -c 129.204.52.140:8000.CommitMsgCount -o export --type json -u blockchain -p zc-12332145

```
关闭mongodb打印的方法
```
Logger log = Logger.getLogger("org.mongodb.driver");   
log.setLevel(Level.OFF);   
```