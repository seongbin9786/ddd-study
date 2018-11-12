# Value Object

도메인에서 사용되는 `값`을 표현하는 객체로, `밸류`라고도 한다.

## 왜 필요할까?

1. 아래 코드와 같이 필드가 String과 같은 타입인 경우 항상 validation이 추가적으로 필요하다. validation이 필요한 이유는 String이라는 타입이 적절하지 않기 때문이다. `String`은 아무런 제한이 없는 문자열을 나타내는데 반해 `email`은 그럴 수 없기 때문이다.

2. 도메인 개념을 코드 상에서 더 명확하게 나타낼 수 있기 때문이다. 예를 들어:

    ```java
    public class Customer {

        //...
        private String email;

    //...
    }

    public class CustomerService {

        public void create(..., String email) {
            //...
        }
    }

    ```

    따라서 위와 같은 코드를 아래와 같이 변경할 수 있다:

    ```java
    public class Customer {
        // ...
        private EmailAddress email;
    }

    // EmailAddress라는 Value Object를 정의한다.
    public class EmailAddress {

        // 내부적으로는 String을 사용하여 저장한다.
        private String value;

        public EmailAddress(String value) {
            // 생성자에서 validation을 수행한다.
        }
    }
    ```

## 단점은 없을까?

Java의 경우 Boilerplate Code가 많이 생산되는 편이다. (언어별로 boilerplate 비용이 다르다.)
