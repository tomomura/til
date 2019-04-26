## docker-compose.yml

```
version: '3'
services:
  swagger-ui:
    image: swaggerapi/swagger-ui
    volumes:
      - ./swagger.json:/app/swagger.json
    ports:
      - "8080:8080"
```

`SWAGGER_JSON` に指定された json が表示されるようになっている。
デフォルトで、 `ENV SWAGGER_JSON "/app/swagger.json"` になっているので、
volumes で上書きしてやれば [localhost:8080](http://localhost:8080) で確認できる。

## 参考
- https://github.com/swagger-api/swagger-ui/blob/master/Dockerfile
