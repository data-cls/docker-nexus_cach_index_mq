## 空间控制 修改原 /var/lib/docker  到 /home/docker/lib 目录

	#cd etc/docker
	#vim daemon.json

	{
	    "graph": "/data/docker"
	}

	# systemctl daemon-reload

	# systemctl restart docker

	# docker info



## 1. 构建docker-nexus
~~~bash
进入/usr/local 目录 解压build-nexus.zip 把 Dockerfile  nexus.war  server.xml 三个文件整理好执行

docker build -t my-nexus:latest .  
~~~
## 2. 运行 my-nexus
~~~bash
docker run -d -p 8081:8081 --name my-nexus --restart always \
-v /usr/local/nexus-storage:/usr/local/nexus-storage nexus:latest
~~~
## 3. 访问   http://localhost:8081    默认用户和密码  admin |  admin123

## 4. maven中的 pom.xml 配置

	<repositories>
		<repository>
			<id>dpt-Releases</id>
			<url>http://192.168.11.32:8081/nexus/content/repositories/dpt-Releases/</url>
			<releases>
				<enabled>true</enabled>
			</releases>
			<snapshots>
				<enabled>true</enabled>
			</snapshots>
		</repository>
	</repositories>


### 获取更多的私服信息请联系我
<img src="my.jpg" height="50%" width="50%"/>
