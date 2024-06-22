Docker compose file for a go project
```yaml
services:
  go-app:
    container_name: go-app
    image: francescoxx/go-app:1.0.0
    build: .
    environment:
      DATABASE_URL: "host=go_db user=postgres password=postgres dbname=postgres sslmode=disable"
    ports:
      - "8000:8000"
    depends_on:
      - go_db
  go_db:
    container_name: go_db
    image: postgres:12
    environment:
      POSTGRES_PASSWORD: postgres
      POSTGRES_USER: postgres
      POSTGRES_DB: postgres
    ports:
      - "5432:5432"
    volumes:
      - pgdata:/var/lib/postgresql/data

volumes:  
  pgdata: {}
```

- Docker Compose file for a Node JS microservice
```yaml
version: '3.9'
services:
  app:
    build: .
    ports:
      - '8081:80'
    depends_on:
      - mongo
    volumes:
      - './configs/docker.env:/app/configs/.env'
      - 'logs:/app/logs:rw'
  mongo:
    image: 'mongo:5'
    restart: always
    ports:
      - '27017:27017'
    volumes:
      - 'mongodata:/data/db'
    healthcheck:
      test: 'echo ''db.runCommand("ping").ok'' | mongo localhost:27017/test --quiet'
      interval: 10s
      timeout: 2s
      retries: 5
      start_period: 5s
  loki:
    image: 'grafana/loki:2.9.0'
    expose:
      - 3100
    command: '-config.file=/etc/loki/local-config.yaml'
  promtail:
    image: 'grafana/promtail:2.9.0'
    volumes:
      - 'logs:/var/log:rw'
      - './infrastructure/promtail.yml:/etc/promtail/config.yml'
    command: '-config.file=/etc/promtail/config.yml'
  prometheus:
    image: 'prom/prometheus:latest'
    volumes:
      - './infrastructure/prometheus.yml:/etc/prometheus/prometheus.yml'
    command:
      - '--config.file=/etc/prometheus/prometheus.yml'
    expose:
      - 9090
  grafana:
    image: 'grafana/grafana:latest'
    volumes:
      - 'grafanadata:/var/lib/grafana'
    environment:
      - GF_PATHS_PROVISIONING=/etc/grafana/provisioning
      - GF_AUTH_ANONYMOUS_ENABLED=true
      - GF_AUTH_ANONYMOUS_ORG_ROLE=Admin
    ports:
      - '3000:3000'
volumes:
  mongodata: null
  grafanadata: null
  logs: null

```


```yaml
services:
  hono-auth-service:
    build:
      context: ./
    image: hono-auth-service:latest
    container_name: hono-auth-service
    ports:
      - "3000:3000"
    entrypoint: ["bun", "run", "src/index.ts"]
    networks:
      - hono-application-network
    environment:
      - DATABASE_URL=postgresql://${DB_USER}:${DB_PASSWORD}@${DB_HOST}:${DB_PORT}/${DB_NAME}?pgbouncer=true
    depends_on:
      - hono-auth-service-db
  hono-auth-service-db:
    image: postgres:16
    restart: always
    container_name: hono-auth-service-db
    networks:
      - hono-application-network
    environment:
      - POSTGRES_USER=${DB_USER}
      - POSTGRES_PASSWORD=${DB_PASSWORD}
      - POSTGRES_DB=${DB_NAME}
    ports:
      - '${DB_PORT}:5432'
    volumes:
      - hono-auth-service-db:/var/lib/postgresql/data
volumes:
  hono-auth-service-db:

networks:
  hono-application-network:
    driver: bridge
```


```yaml
version: '3.9'

services:
  service1:
    build:
      context: ./service1
    depends_on:
      - postgres
      - redis
    environment:
      - DATABASE_URL=postgres://postgres:postgres@postgres:5432/service1db
      - REDIS_URL=redis://redis:6379

  service2:
    build:
      context: ./service2
    depends_on:
      - postgres
    environment:
      - DATABASE_URL=postgres://postgres:postgres@postgres:5432/service2db

  service3:
    build:
      context: ./service3
    depends_on:
      - mongodb
    environment:
      - MONGODB_URL=mongodb://mongodb:27017/service3db

  postgres:
    image: postgres:13
    restart: always
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
    volumes:
      - postgres_data:/var/lib/postgresql/data

  mongodb:
    image: mongo:4.4
    restart: always
    volumes:
      - mongo_data:/data/db

  redis:
    image: redis:6
    restart: always
    volumes:
      - redis_data:/data

volumes:
  postgres_data:
  mongo_data:
  redis_data:

```