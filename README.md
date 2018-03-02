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
