# Install Chi

```
go get github.com/go-chi/chi/v5
go get github.com/go-chi/chi/v5/middleware
go get github.com/go-chi/cors
```

# Install PostgreSql

```
go get github.com/jackc/pgconn
go get github.com/jackc/pgx/v4
go get github.com/jackc/pgx/stdlib
```

# Install MongoDB

~~~
go get go.mongodb.org/mongo-driver/mongo
go get go.mongodb.org/mongo-driver/mongo/options
~~~
- URL CONNECTION MONGDB COMPASS
~~~
mongodb://admin:password@localhost:27020/logs?authSource=admin
~~~

# Install Mail
~~~
go get github.com/vanng822/go-premailer/premailer
go get github.com/xhit/go-simple-mail/v2
~~~

# Install RabbitMQ
~~~
go get github.com/rabbitmq/amqp091-go
~~~

# Install gRPC
~~~
go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.27
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.2
~~~
# Docker

```
docker exec -it <postgres-container-id-or-name> psql -U postgres
\c users
```

# Docker SWARM
- Docker Push All Microservice
~~~
docker build -f logger-service.dockerfile -t phuctapcode/logger-service:1.0.0 .
docker push phuctapcode/logger-service:1.0.0

docker build -f authentication-service.dockerfile -t phuctapcode/authentication-service:1.0.0 .
docker push phuctapcode/authentication-service:1.0.0

docker build -f broker-service.dockerfile -t phuctapcode/broker-service:1.0.0 .
docker push phuctapcode/broker-service:1.0.0

docker build -f listener-service.dockerfile -t phuctapcode/listener-service:1.0.0 .
docker push phuctapcode/listener-service:1.0.0

docker build -f mail-service.dockerfile -t phuctapcode/mail-service:1.0.0 .
docker push phuctapcode/mail-service:1.0.0

docker swarm init
docker stack deploy -c swarm.yml myapp
docker service ls

docker service scale myapp_listener-service=3
~~~
- Ví dụ logger-service thay đổi và update lên swarm
~~~
docker build -f logger-service.dockerfile -t phuctapcode/logger-service:1.0.1 .
docker push phuctapcode/logger-service:1.0.1

Hãy Scale lên 3 để tránh ngừng hoạt động, nó sẽ nâng cấp từng phiên bản
docker service update --image phuctapcode/logger-service:1.0.1 myapp_logger-service
~~~
- Stop Swarm
~~~
docker service scale myapp_broker-service=0
~~~
- Remove Swarm
~~~
docker stack rm myapp
docker swarm leave --force
~~~
