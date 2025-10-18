# DAO, DTO, Entity Class의 차이

## Goal
> DAO(Data Access Object)란 무엇인지 이해한다.   
> DTO(Data Transfer Object)란 무엇인지 이해한다.   
> Entity Class란 무엇인지 이해한다.   
> package 구조에 따른 흐름, 해당 package의 역할 및 기능을 이해한다.   

## DAO(Data Access Object) 란?
### repository package

   * 실제로 DB에 접근하는 객체이다.
     * Persistence Layer(DB에 data를 CRUD하는 계층)이다.
   * Service와 DB를 연결하는 고리의 역할을 한다.
   * SQL를 사용(개발자가 직접 코딩)하여 DB에 접근한 후 적절한 CRUD API를 제공한다.
     * JPA 대부분의 기본적인 CRUD method를 제공하고 있다.
     * extends JpaRepository<User, Long>
   * 예시(JPA 사용 시)
     ```
     public interface QuestionRepository extends CrudRepository<Question, Long> {
     }
     ```
## DTO(Data Transfer Object) 란?
### dto package
   * 계층간 데이터 교환을 위한 객체(Java Beans)이다.
     * DB에서 데이터를 얻어 Service나 Controller 등으터 보낼 때 사용하는 객체를 말한다.
     * 즉, DB의 데이터가 Presentation Logic Tier로 넘어오게 될 때는 DTO의 모습으로 바껴서 오고가는 것이다.
     * 로직을 갖고 있지 않는 순수한 데이터 객체이며, getter/setter 메서드만을 갖는다.
     * 하지만 DB에서 꺼낸 값을 임의로 변경할 필요가 없기 때문에 DTO클래스에는 setter가 없다. (대신 생성자에서 값을 할당한다.)
   * Request와 Response용 DTO는 View를 위한 클래스
     * 자주 변경이 필요한 클래스
     * Presentation Model
     * toEntity() 메서드를 통해서 DTO에서 필요한 부분을 이용하여 Entity로 만든다.
     * 또한 Controller Layer에서 Response DTO 형태로 Client에 전달한다.
   * 참고 VO(Value Object) vs DTO
     * VO는 DTO와 동일한 개념이지만 read only 속성을 갖는다.
     * VO는 특정한 비즈니스 값을 담는 객체이고, DTO는 Layer간의 통신 용도로 오고가는 객체를 말한다.
   * 예시
     ```
     @Getter
     @NoArgsConstructor
     @AllArgsConstructor
     public class UserDto {
         @NotBlank
         @Pattern(regexp = "^([\\w-]+(?:\\.[\\w-]+)*)@((?:[\\w-]+\\.)*\\w[\\w-]{0,66})\\.([a-z]{2,6}(?:\\.[a-z]{2})?)$")
         private String email;
	     
         @JsonIgnore
         @NotBlank
         @Size(min = 4, max = 15)
         private String password;
	     
         @NotBlank
         @Size(min = 6, max = 10)
         private String name;
	     
         public User toEntity() {
             return new User(email, password, name);
         }
	     
         public User toEntityWithPasswordEncode(PasswordEncoder bCryptPasswordEncoder) {
             return new User(email, bCryptPasswordEncoder.encode(password), name);
         }
     }
     ```
## 전체 구조 (package 기준)
![image](https://user-images.githubusercontent.com/108439363/230016836-36383af4-075c-4f0a-a5db-3013492b268d.png)
### controller(web)
   * 기능
     * 해당 요청 url에 따라 적절한 view와 mapping 처리
     * @Autowired Service를 통해 service의 method를 이용
     * 적절한 ResponseEntity(DTO)를 body에 담아 Client에 반환
   * 예시 1)
     ```
     @Controller
     @RequestMapping("/")
     public class HomeController {
         @GetMapping
         public String home(HttpSession session) {
             if (!SessionUtil.getUser(session).isPresent()) {
                 return "login";
             }
             return "index";
         }
     }
	 ```
     * @Controller
       * API와 view를 동시에 사용하는 경우에 사용
       * 대신 API 서비스로 사용하는 경우는 @ResponseBody를 사용하여 객체를 반환한다.
       * view(화면) return이 주목적
   * 예시 2)
     ```
     @RestController
     @RequestMapping("/api/users")
     public class ApiUserController {
         @Autowired
         private UserService userService;
	     
         @PostMapping("/login")
         public ResponseEntity login(@RequestBody @Valid LoginDto loginDto, HttpSession session) {
             SessionUtil.setUser(session, userService.login(loginDto));
             return new ResponseEntity(HttpStatus.OK);
         }
     }
	 ```
     * @RestController
       * view가 필요없는 API만 지원하는 서비스에서 사용 (Spring 4.0.1부터 제공)
       * @RequestMapping 메서드가 기본적으로 @ResponseBody 의미를 가정한다.
       * data(json, xml 등) return이 주목적: return ResponseEntity
       * 즉, @RestController = @Controller + @ResponseBody
### service
   * 기능
     * @Autowired Repository를 통해 repository의 method를 이용
     * 적절한 Business Logic을 처리한다.
     * DAO로 DB에 접근하고 DTO로 데이터를 전달받은 다음, 비지니스 로직을 처리해 적절한 데이터를 반환한다.
   * 예시
     ```
	 @Service
     public class UserService {
         @Autowired
         private UserRepository userRepository;
         @Resource(name = "bCryptPasswordEncoder")
         private PasswordEncoder bCryptPasswordEncoder;
         @Autowired
         private MessageSourceAccessor msa;
	     
         public User save(UserDto userDto) {
             if (isExistUser(userDto.getEmail())) {
                 throw new UserDuplicatedException(msa.getMessage("email.duplicate.message"));
             }
             return userRepository.save(userDto.toEntityWithPasswordEncode(bCryptPasswordEncoder);
         }
     }
	 ```
### repository(dao)
   * 기능
     * 실제로 DB에 접근하는 객체이다.
     * Service와 DB를 연결하는 고리의 역할을 한다.
     * SQL를 사용(개발자가 직접 코딩)하여 DB에 접근한 후 적절한 CRUD API를 제공한다.
       * JPA 대부분의 기본적인 CRUD method를 제공하고 있다.
       * extends JpaRepository<User, Long>
   * 예시 (JPA의 경우)
     ``` 
     public interface UserRepository extends JpaRepository<User, Long> {
     }
	 ```
	 ```
     public interface QuestionRepository extends CrudRepository<Question, Long> {
     }
     ```
