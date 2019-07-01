## 构建docker-nexus
Dockerfile  nexus.war  server.xml

## 运行

docker run -d -p 8081:8081 --name my-nexus --restart always -v /usr/local/nexus-storage:/usr/local/nexus-storage nexus:latest




