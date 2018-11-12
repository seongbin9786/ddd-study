# Bounded Context

각각의 하위 도메인마다 사용하게 되는 개념이 조금씩 다른데, 예를 들어 `User`가 회원 도메인에서는 `User`이지만, `Order`에서는 `Orderer`이고, `Board(게시판)`에서는 `Writer`과 같이 실제로 `User`를 구성하는 전체 정보가 아닌 일부 정보만, 그것이 살짝 다른 개념(명칭)으로 필요하게 된다.

```java
@Entity
public class User {
    private UserId userId;
    private String name;
    private Password password;
    private boolean blocked;
    // ...

    public void initializePassword() {
        //...
    }

    
    public void block() {
        //...
    }

    
    public void unblock() {
        //...
    }

    public void changePassword(String oldPw, String newPw) {
        //...
    }
}

// 타 bounded context에서 직접 정의한 Value
@Embeddable
public class Orderer {
    private UserId userId;
    private String name;
    private Address shippingAddress;
}

// 타 bounded context에서 직접 정의한 Value
@Embeddable
public class Writer {
    private UserId userId;
    private String name;
    private WriterRank rank;

    //...
}
```

## 왜 필요할까?



## Bounded Context를 발견하는 방법

