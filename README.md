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
# Docker

```
docker exec -it <postgres-container-id-or-name> psql -U postgres
\c users
```
