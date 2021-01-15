# mysql_cach_index_mq_elk



    cat <<EOF >docker-compose.yml

    version: '3'
    services:
      mysql:
        image: registry.cn-shanghai.aliyuncs.com/caiyc/mysql:5.6
        container_name: mysql
        command: mysqld --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
        restart: always
        environment:
          MYSQL_ROOT_PASSWORD: 123456
        ports:
          - 3306:3306
        volumes:
          - /mydata/mysql/data/db:/var/lib/mysql 
          - /mydata/mysql/data/conf:/etc/mysql/conf.d
          - /mydata/mysql/log:/var/log/mysql
      redis:
        image: registry.cn-shanghai.aliyuncs.com/caiyc/redis:latest
        container_name: redis
        command: redis-server --appendonly yes
        volumes:
          - /mydata/redis/data:/data
        ports:
          - 6379:6379
      rabbitmq:
        image: registry.cn-shanghai.aliyuncs.com/caiyc/rabbitmq:3-management
        container_name: rabbitmq
        volumes:
          - /mydata/rabbitmq/data:/var/lib/rabbitmq
          - /mydata/rabbitmq/log:/var/log/rabbitmq
        ports:
          - 5672:5672
          - 15672:15672
      nginx:
        image: nginx:1.10
        container_name: nginx
        volumes:
          - /mydata/nginx/nginx.conf:/etc/nginx/nginx.conf
          - /mydata/nginx/html:/usr/share/nginx/html
          - /mydata/nginx/log:/var/log/nginx
        ports:
          - 80:80
      elasticsearch:
        image: elasticsearch:7.6.2
        container_name: elasticsearch
        environment:
          - "cluster.name=elasticsearch" 
          - "discovery.type=single-node" 
          - "ES_JAVA_OPTS=-Xms512m -Xmx512m"
        volumes:
          - /mydata/elasticsearch/plugins:/usr/share/elasticsearch/plugins
          - /mydata/elasticsearch/data:/usr/share/elasticsearch/data
        ports:
          - 9200:9200
          - 9300:9300
      logstash:
        image: logstash:7.6.2
        container_name: logstash
        environment:
          - TZ=Asia/Shanghai
        volumes:
          - /mydata/logstash/logstash.conf:/usr/share/logstash/pipeline/logstash.conf
        depends_on:
          - elasticsearch 
        links:
          - elasticsearch:es
        ports:
          - 4560:4560
          - 4561:4561
          - 4562:4562
          - 4563:4563
      kibana:
        image: kibana:7.6.2
        container_name: kibana
        links:
          - elasticsearch:es
        depends_on:
          - elasticsearch
        environment:
          - "elasticsearch.hosts=http://es:9200"
        ports:
          - 5601:5601
      mongo:
        image: mongo:4.2.5
        container_name: mongo
        volumes:
          - /mydata/mongo/db:/data/db
        ports:
          - 27017:27017  




    EOF





