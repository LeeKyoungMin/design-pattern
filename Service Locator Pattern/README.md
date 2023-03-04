# Service Locator Pattern

## Service Locator 패턴

---

예를 들어, 서비스 레이어에서 repositoy 인터페이스에 의존하는 경우가 생긴다. !! 특히나 RDB, NoSQL 등과 같이. 이럴 경우 2가지 패턴의 해결 방식이 존재한다.

### 1. Service Locator 패턴

---

```java
public class UserApplicationService{
	private IUserRepository userRepository;

	public UserApplicationService(){
		//ServiceLocator를 통해 필요한 인스턴스를 받는다.
		this.userRepository = ServiceLocator.Resolve<IUserRepository>();
  }

  //생략 ...
}
```

<img width="700" alt="service Locator pattern" src="https://user-images.githubusercontent.com/22589581/222904588-6d3c5071-f77c-4be3-ac1e-d60a6dc9fe3a.png">


but. Service Locator 패턴은 처음부터 안티패턴으로 보는 경우가 있다.

1) 의존 관계를 외부에서 보기 어렵다.

2) 테스트 유지가 어렵다.

### 1) 의존 관계를 외부에서 보기 어렵다.

---

```java
public class UserApplicationService{
	public UserApplicationService();
	public void Register(UserRegisterCommand command);
}
```

→ 만약 개발자는 해당 정의를 보고 나면 UserApplicationService의 인스턴스를 만들고 Register 메소드를 호출할 것이다. 그렇다면 의존관계 해소가 되지 않았기 떄문에 에러가 발생하고 프로그램이 강제종료 될 것이다.

### 2. 테스트 유지가 어렵다

---

```java
//테스트를 준비하는 코드
ServiceLocator.Register<IUserRepository, InMemoryUserRepository>();
var UserApplicationService = new UserApplicationService();
```

```java
public class UserApplicationService{
	private IUserRepository userRepository;

	public UserApplicationService(){
		//ServiceLocator를 통해 필요한 인스턴스를 받는다.
		this.userRepository = ServiceLocator.Resolve<IUserRepository>();
		this.fooRepository = ServiceLocator.Resolve<IFooRespository>();
  }

  //생략 ...
}
```

→ 테스트는 개발자의 실수를 바로잡아 주지만, 변화한 코드에 새로운 의존관계가 추가될 경우 테스트 코드에는 IFooRepository에 대한 의존 관계 해소 정보가 등록되지 않는다. 이로써 테스트는 깨진다.
