### Run Zuul with different configs

#### With serviceId
```shell
# Run API Gateway with default weather service pointing to serviceId weather-service on 8080
java -jar api-gateway/target/api-gateway-1.0.0-SNAPSHOT.jar

# Run Weather Service on 8080
java -jar weather-service/target/weather-service-1.0.0-SNAPSHOT.jar

# Run Weather Service 2 on 8081
java -jar weather-service2/target/weather-service2-1.0.0-SNAPSHOT.jar
```

#### Test
```shell
curl --location --request GET 'http://localhost:7070/weather/today'

# Response: It's a bright sunny day today!
```

#### With url
```shell
# Run API Gateway
java -jar api-gateway/target/api-gateway-1.0.0-SNAPSHOT.jar --zuul.routes.weather-service.url=http://localhost:8081

# Run Weather Service on 8080
java -jar weather-service/target/weather-service-1.0.0-SNAPSHOT.jar

# Run Weather Service 2 on 8081
java -jar weather-service2/target/weather-service2-1.0.0-SNAPSHOT.jar
```

#### Test
```shell
curl --location --request GET 'http://localhost:7070/weather/today'

# Response: It's a rainy day
```