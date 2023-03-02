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
