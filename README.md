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
