# 加入集群
### 功能描述
使用cli指令将当前节点加入集群。


### 参数说明：

addr：集群中任意一个节点的地址

### 执行示例
```shell
./apinto join --addr=10.18.0.2:9400
```

**备注**：若两个单机节点组成集群，任意一个节点加入另外一个即可。