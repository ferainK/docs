# 패턴 설계 (Pattern Design)
- 가장 최적의 방법으로 개발할 수 있도록 패턴화한 설계 방법
- 주로 GoF(Gong of Four)로 설계 패턴이 공유됨

|__생성 패턴__|__구조 패턴__|__행위 패턴__|
|-|-|-|
|_(생성자)_|_(클래스 구조)_|_(클래스 상호작용)_|
|Factory Method|`Adapter`|Template Method|
|`Singleton`|Composite|Interpreter|
|Prototype|Bridge|Iterator|
|`Builder`|`Decorator`|Observer|
|Abstract Factory|`Facade`|`Strategy`|
|`Chaining`|Flyweight|`Visitor`|
||`Froxy`|Chain of Responsibility|
|||Command|
|||Mediator|
|||State|
|||Memento|

## 1. 생성 패턴
### 1) 싱글톤 패턴
- 1개의 유일한 객체를 다른 객체에서 사용되는 형태
- (Ex. 소캣통신에서 서버와 연결된 Connect 객체에 사용)
- 외부에서 생성자를 만들 수 없도록 구현되어야함
    ```java
    private static SocketClient socketClient = null; // 스스로를 선언
    private SocketClient(){}; // 외부에서 생성자를 만들 수 없음

    // 외부에서 클래스를 호출할 경우 객체 반환하는 메서드
    public static SocketClient getInstance(){
    if (socketClient == null){
        socketClient = new SocketClient();
    }
    return socketClient;
    }
    ```
## 2. 구조 패턴
### 1) 어댑터 패턴
- 호환성이 없는 기존 클래스를 `인터페이스를 변환`을 통해 호환성 부여
    ```java
    // 변경하고자하는 클래스를 상속
    public class SocketAdapter implements Electronic110V{
        // 현재 클래스 인스턴스화
        private Electronic220V electronic220V;
        public SocketAdapter(Electronic220V electronic220V){
            this.electronic220V = electronic220V;
        }
    }
    ```
    ```java
    //main
        Electronic110V adapter = new SocketAdapter(electronic220V);
        Electronic110V.connect(electronic220V);
    ```
### 2) 프록시 패턴