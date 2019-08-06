## 1.docker 运行

~~~bash
docker run -p 6333:6379 -d --name redis \
--restart=always registry.cn-shanghai.aliyuncs.com/caiyc/redis:latest
~~~

## 2.配置注意点
~~~bash
1. 客户端 redis-desktop-manager-0.8.8.384.exe 连接测试

2. 安全方面 控制授权密码 、 暴露端口 6333 

3. 集群方案
~~~

