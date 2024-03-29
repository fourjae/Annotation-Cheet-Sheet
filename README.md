# Annotation-Cheet-Sheet
어노테이션 모음 (Ctrl + F로 검색 사전순 나열)

* * *


<details>
<summary>@AllArgsConstructor</summary>

- 사용되는 모든 필드 값을 파라미터로 받는 생성자를 만듭니다.

```Java
public class User {
    
    private String id;
    
    private String name;
    
    @NonNull
    private String pw;
    
    private final int age;
}
```
```Java
User user = new User("fourThree", "유저", "passW0rd", 15); // @AllArgsConstructor
```
  
</details>

<details>
<summary>@GetMapping</summary>

- Get 메서드 요청을 메서드에 맵핑(@RequestMapping) 해줍니다.
    - "기본 값은 없음이며 값을 넣을경우 해당 url 경로에 매핑해줍니다."

```Java
@RestController
@RequestMapping("/")
public class Controller {

    @GetMapping("/getParameter")    
    public String getParameter(@RequestParam String name) {
        return name;
    }
    
}
```
  
</details>





<details>
<summary>@RequiredArgsConstructor</summary>

- final 키워드가 붙은 변수나 @NonNull인 필드 값만 파라미터로 받는 생성자를 만듭니다.

```Java
public class User {
    
    private String id;
    
    private String name;
    
    @NonNull
    private String pw;
    
    private final int age;
}
```
```Java
User user = new User("passW0rd", 15); // @RequiredArgsConstructor
```

---

```Java
public class UserController {
    private final UserService userService;

    public UserController(UserService userService) {
        this.userService = userService;
    }
    
}
// 위 아래의 코드는 같은 의미를 내포합니다.
@RequiredArgsConstructor
public class UserController {

    private final UserService userService;
    
}
```
</details>


<details>
<summary>@Component</summary>
- @Component는 개발자가 직접 작성한 Class를 Bean으로 등록함으로써 **Application Context**에서 해당 클래스를 빈으로 자동 감지 및 등록하게 도와주는 Annotation 입니다.
    
    스프링 컨테이너에 스프링 Bean으로 등록되면 해당 클래스는 IoC 컨테이너가 싱글톤으로 관리합니다.
    
    Service 클래스가 아닌 직접 작성한 클래스(설정 파일 등)을 Bean으로 등록할 때 사용합니다.
    
```
@Component
public class UserService {
    // Class implementation
}   
```

</details>

<details>
<summary>@toString</summary>

- 객체 상태에 대한 관련 정보를 문자열로 출력하여 볼 수 있게 해주는 어노테이션 입니다.

```Java
public class Person {
    private String name;
    private int age;

    // Constructor and other methods omitted for brevity

    @Override
    public String toString() {
        return "Person [name=" + name + ", age=" + age + "]";
    }
}
```
    
다음과 같이 toString 메소드를 override 하여 현재 객체에 대한 상태를 보여줄 수 있지만

@toString 어노테이션을 사용하면 자동으로 override 되어 사용할 수 있습니다.


</details>



<details>
<summary>@Service</summary>
    
- @Component과 같은 맥락이며 **스프링 컨텍스트**에 bean으로 등록하는 어노테이션입니다.

    스프링 컨테이너에 스프링 Bean으로 등록되면 해당 클래스는 IoC 컨테이너가 싱글톤으로 관리합니다.
    
    보통 비즈니스 로직이나 respository layer 호출하는 Service 클래스에 사용됩니다.
    
```Java    
@Service
public class UserService {
    // Class implementation
}
``` 
   

</details>







<details>
<summary>@NoArgsConstructor</summary>

- 파라미터가 없는 기본 생성자를 만듭니다.

```Java
public class User {
    
    private String id;
    
    private String name;
    
    @NonNull
    private String pw;
    
    private final int age;
}
```
```Java
User user = new User(); // @NoArgsConstructor
```
</details>





<details>
<summary>@EqualsAndHashCode</summary>

- Equals() HashCode() 메서드를 자동으로 생성하여 클래스에 추가합니다.

```Java
@EqualsAndHashCode
public class Person {
    private String name;
    private int age;

    //equals 두 객체가 같은지 비교
    //hashCode 해시 코드를 반환
}
```

위 어노테이션은 아래와 같은 메서드를 생성합니다.

```Java
public class Person {
    private String name;
    private int age;

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        
        Person person = (Person) obj;
        return age == person.age && (name == null ? person.name == null : name.equals(person.name));
    }

    @Override
    public int hashCode() {
        int result = 17;
        result = 31 * result + age;
        result = 31 * result + (name != null ? name.hashCode() : 0);
        return result;
    }
}
```
  
</details>



