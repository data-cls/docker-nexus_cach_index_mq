## elasticsearch 运行
~~~bash
docker run -d --name elasticsearch \
-p 9200:9200 -p 9300:9300 \
-e "discovery.type=single-node" registry.cn-shanghai.aliyuncs.com/caiyc/elasticsearch:6.5.0
~~~

## 配置注意点

## 了解更多请联系我
<img src="my.jpg" height="50%" width="50%" />
