## 构建docker-nexus
解压 Dockerfile  nexus.war  server.xml

docker build -t my-nexus:latest .  

## 运行 my-nexus

docker run -d -p 8081:8081 --name my-nexus --restart always -v /usr/local/nexus-storage:/usr/local/nexus-storage nexus:latest

## 默认用户和密码  admin |  admin123

## maven中的 pom.xml 配置

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


