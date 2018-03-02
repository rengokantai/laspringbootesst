# laspringbootesst


### 6
@EnableAutoConfiguration
- Allows for configuration classes to be scanned dynamically
- Usually based off jars loaded on classpath
- Driven off of spring.factories
- AutoConfiguraionBefore AutoConfigurationAfter


###### 01:40
Conditional Loading
- @ConditionalOnClass
- @ConditionalOnBean
- @ConditionalOnProperty
- @ConditionOnMissingBean

Properties
- Preconfigured default properties for AutoConfiguration class
- @EnableConfigurationProperties specifies the default property set
- Can always be overriden


### Configuring Spring
application.properties

Bean Configuration
- Adding beans to the default application class
- Adding beans to seperate configuration classes
- Importing XML-based configurations
- Component scanning

```
@RequestMapping
@GetMapping
```

### Profiles in Spring Boot
application.yml
```
spring:
  profiles: dev
server:
  port: 8000
---
spring:
  profiles: test
server:
  port:9000
```

mvn
```
mvn clean package
```
```
java -jar -Dspring.profiles.active=dev target/initial.jar
```

### Spring Boot Actuator
add secority to false
```
management:
  security:
    enabled: false
---
```
/env /health /mapping


### Web Starter
JSON Marshaller
- With Spring Web you get the Jackson JSON marshaller
- Automatic marshalling and unmarshalling in web flows

Logging Frameworks
- Slf4j
- Levering properties to modify Loglevels
- Logback and JBoss


### Configuring Embedded Tomcat
Servlets, Filters, Listeners
- Spring Boot autoconfigures the default servlet for all responses at "/"
- Any class of these types that are beans (config or component scanned) will be registered to the embedded container


Compression
- ```server.compression.enabled=true```
- Response must be 2048 bytes to compress by default

TLS/SSL
- native support
- requires a Java Keystore that contains the certificate
- Properties used to configure

```
keytool -genkey -keyalg RSA 0alias ke -keystore keystore.jks -storepass pass -validity 40000 -keysize 2048
```
add in application.yml
```
server:
  ssl:
    key-store: classpath:keystore.jks
    key-store-password: pass
    key-store-type: JKS
    key-alias: ke
    key-password: pass
```
```
http --verify=no https://localhost:8080/api/greeting
```


### Spring Boot WebApps
```
<tr th:each="room: ${rooms}">
  <td th:text="${room.number}"></td>
  <td th:text="${room.name}"></td>
</tr>
```

create a site.css at
```
/resources/static/css/site.css
```
in html
```
<link th:href="@{/css/site.css}" rel="stylesheet"/>
```


### Spring Boot Web Services

###### 03:20
Autowired should use in constructor
```
@Autowired
public RoomController(RoomService roomService){
  super();
  this.roomService = roomService;
}
```

###### 05:46
xml format
```
http http"// Accept:application/xml
```

add jackson
```
<dependency>
  <groupId>com.fasterxml.jaskcon.dataformat</groupId>
  <aritfactId>jackson-dataformat-xml</artifactId>
</dependency>
```


### Spring Boot Devtools
add
```
<dependency>
  <groupId>org.springframework.boot</groupId>
  <aritfactId>spring-boot-devtools</artifactId>
</dependency>
```
preference-> compiler->build project automaticcally

### Packaging a Spring Boot Application

### Running a Spring Boot Application

### Implementing CommandLineRunner
```
<dependency>
  <groupId>org.springframework</groupId>
  <aritfactId>spring-web</artifactId>
</dependency>
<dependency>
  <groupId>org.fasterxml.jackson.core</groupId>
  <aritfactId>jackson-core</artifactId>
</dependency>
```
override run method
```
@Override
public void run(String... string) throws Exception {
  
}
```
