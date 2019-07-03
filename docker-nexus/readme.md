## 构建docker-nexus
Dockerfile  nexus.war  server.xml

## 运行

docker run -d -p 8081:8081 --name my-nexus --restart always -v /usr/local/nexus-storage:/usr/local/nexus-storage nexus:latest

## maven pom.xml

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


