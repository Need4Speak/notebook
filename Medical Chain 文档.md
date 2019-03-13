---
title: Medical Chain 文档 
tags: 新建,模板,小书匠
grammar_cjkRuby: true
---


1. build项目jar包：
	`mvn -Dmaven.test.skip=true  assembly:assembly`
	
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