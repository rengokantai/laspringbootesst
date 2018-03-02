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
