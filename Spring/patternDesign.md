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
    / /main
        Electronic110V adapter = new SocketAdapter(electronic220V);
        Electronic110V.connect(electronic220V);
    ```
### 2) 프록시 패턴
- Proxy Class를 통해 대신 전달는 형태로 설계
- 실제 Client는 Proxy로부터 결과를 받는다.
- Cache의 기능으로 활용 가능하다.
    ```java
    // Proxy Class
    public class ProxyBrowser implements IBrowser{
        private String url;
        private Html html;

        public ProxyBrowser(String url){
            this.url = url;
        }

        @Overide
        public Html show(){
            if (html == null) {
                this.html = new Html(url);
                System.out.println("프록시 브라우저에서 실행합니다 : " + url);
            }
            System.out.println("프록시 브라우저에 저장된 주소로 실행합니다. : " + url)
        }
    }
    ```
    - [심화] AOP 기능 : 모든 메소드의 전/후에 실행되는 기능 (프로그램 구동 시간 등)
        ```java
        //AopBrowser
        public class AopBrowser implements IBrowser {
            private String url;
            private Html html;
            private Runnable after;
            private Runnable before;

            public AopBrowser(String url, Runnable before, Runnable after){
                this.url = url;
                this.before = before;
                this.after = after;
            }

            @Override
            public Html show() {
                if (html == null) {
                before.run();
                this.html = new Html(url);
                System.out.println("AopBrowser html loading from : " + url);
                try {
                    Thread.sleep(1500);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                }
                after.run();
                System.out.println("AopBrowser html cache : " + url);
                return html;
            }
        }

        // Main
        public static void main(String[] args) {

            AtomicLong start = new AtomicLong();
            AtomicLong end = new AtomicLong();

            IBrowser aopBrowser = new AopBrowser("www.naver.com",
                ()->{
                System.out.println("before");
                start.set(System.currentTimeMillis());
                },
                ()->{
                long now = System.currentTimeMillis();
                end.set(now - start.get());
                });

            aopBrowser.show();
            System.out.println("loading time : " + end.get());
        }
        ```
### 4) 데코레이터 패턴
- 기존 클래스는 유지하되, 필요한 형태로 꾸밀때 사용
- 상속과 동일한 개념으로 사용
    ```java
    // 데코레이트 패턴
    public class AudiDecorator implements ICar{

        protected ICar audi;
        protected String modelName;
        protected int modelPrice;

        public AudiDecorator(ICar audi, String modelName, int modelPrice){
            this.audi = audi;
            this.modelName = modelName;
            this.modelPrice = modelPrice;
        }

        @Override
        public int getPrice() {
            return audi.getPrice() + modelPrice;
        }

        @Override
        public void showPrice() {
            System.out.println(modelName + "의 가격은 " + getPrice() + "원 입니다.");
        }
    }

    // 데코레이션
    public class A5 extends AudiDecorator {
        public A5(ICar audi, String modelName) {
            super(audi, modelName, 3000);
        }
    }
    ```

## 3. 행위 패턴
### 1) 옵저버 패턴
- 이벤트 리스너(`Event Listener`)와 같은 기능
```java
// 이벤트 리스터
public class Button {
  private String name;
  private IButtonListner buttonListner;

  public Button(String name){
    this.name = name;
  }

  public void click(String message){
    buttonListner.clickEvent(message);
  }

  public void addListener(IButtonListner buttonListner){
    this.buttonListner = buttonListner;
  }
}

// 익명클래스를 통한 이벤트 리스너 생성 및 클릭 이벤트 실행
public static void main(String[] args) {
    Button button = new Button("버튼");
    button.addListener(new IButtonListner() {
      @Override
      public void clickEvent(String event) {
        System.out.println(event);
      }
    });

    button.click("메시지 전달: click1");
    button.click("메시지 전달: click2");
    button.click("메시지 전달: click3");
    button.click("메시지 전달: click4");
  }
```
