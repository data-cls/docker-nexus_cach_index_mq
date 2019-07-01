## docker rabbitmq 运行

docker run -d --hostname my-rabbit --name rabbit --restart=always -p 15671:15671 -p 4369:4369 -p 5671:5671 -p 5672:5672 -p 25672:25672 -p 15672:15672  rabbitmq:3-management


## 配置注意的地方



