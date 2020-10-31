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
 
 program arguments: 
 --spring.profiles.active=production -> its gonna override the defualt dev values.
 
 ===============================================================
 application.properties
 spring.profiles.active=development
 
 class DataSource {
  
   String server;
   String port;
  
  //empty constructor
  //settter getter
  //toString() to print
 }
 
 @Configuration
 class DataSourceConfig {
 
    @Bean("dataSource")
    @Profile("development")
    DataSource development(){
      return new DataSource("my-dev-url", 9999);
    }
    
    @Bean("dataSource")
    @Profile("production")
    DataSource production(){
      return new DataSource("my-prod-url", 8000);
    }
    
 }
 
 @SpringBootApplication
 class App {
   psvm(String []args){
      ApplicationContext ctx= SpringApplication.run(App.class, args);
      sout(ctx.getBean("dataSource").toString());
   }
 
 }
 
 PRINT-> DataSource(server='my-dev-url',port=9999)

 ==============================================================================================
 
 with --debug option in program arguments, you can see which configuration got included in autoconfiguration and which got excluded from that
