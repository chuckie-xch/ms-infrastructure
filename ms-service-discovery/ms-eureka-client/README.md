在本工程中引入 eureka 依赖（前提是已经配置父级管理依赖，见ms-eureka-server 的 README）：
```xml
<dependencies>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
        </dependency>

    </dependencies>
```

添加启动类：

```java
package com.bestcode.pandora.eureka;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.client.discovery.EnableDiscoveryClient;


@EnableDiscoveryClient
@SpringBootApplication
public class EurekaClientApplication {

    public static void main(String[] args) {
        SpringApplication.run(EurekaClientApplication.class, args);
    }
}
```

增加 application.properties 配置：

```properties
server.port=8081

spring.application.name=ms-eureka-client

eureka.client.service-url.defaultZone=http://localhost:8761/eureka/

```

访问 http://localhost:8761/ 查看服务状态