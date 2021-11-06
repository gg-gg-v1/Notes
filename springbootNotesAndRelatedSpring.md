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

Security :

security.user.name=password
security.user.password=password

dependency:
spring-boot-starter-security

spring boot run with arguments
```
mvn spring-boot:run -Dspring-boot.run.arguments=-spring.profiles.active=production
```


OneToMany :
one customer can have many products

```
@Data
@AllArgsConstructor
@NoArgsConstructor
@ToString
@Entity
public class Customer {
    @Id
    @GeneratedValue
    private int id;
    private String name;
    private String email;
    private String gender;
    @OneToMany(targetEntity = Product.class,cascade = CascadeType.ALL)
    @JoinColumn(name ="cp_fk",referencedColumnName = "id")
    private List<Product> products;
}
```


```
@Data
@AllArgsConstructor
@NoArgsConstructor
@ToString
@Entity
public class Product {
    @Id
    private int pid;
    private String productName;
    private int qty;
    private int price;
}
```
```
import java.util.List;

@RestController
public class OrderController {
    @Autowired
    private CustomerRepository customerRepository;
    @Autowired
    private ProductRepository productRepository;

    @PostMapping("/placeOrder")
    public Customer placeOrder(@RequestBody OrderRequest request){
       return customerRepository.save(request.getCustomer());
    }

    @GetMapping("/findAllOrders")
    public List<Customer> findAllOrders(){
        return customerRepository.findAll();
    }

    @GetMapping("/getInfo")
    public List<OrderResponse> getJoinInformation(){
        return customerRepository.getJoinInformation();
    }
}
```
if we save customer info, then product info will also get saved...
