@ConfigurationProperties -> will map properties file to pojo

@Component
@ConfigurationProperties(prefix="myconfig")
class myclass{
String appName;
String appDesc;
String appFirstName;
}

application.yml

myconfig:
   app-name: My application Name
   appDesc: some app
   app-first-name: my first name
  
 include some dependecy for this:
 spring-boot-configuration-processor
 
 ===============================================================
