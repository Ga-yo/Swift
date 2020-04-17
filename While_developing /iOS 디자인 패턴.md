### MVC패턴 in iOS

-----

#### MVC 패턴이란?

: Model - View - Controller의 줄임말이다. 

__Model__ 은 데이터에 관한 로직을 담는 부분이다. 값들을 계산하고 저장하는 부분

__View__ 는 사용자에게 보여지는 화면을 가리킨다. 값들이 보여지는 UI

__Controller__ 는 View로 입력된 값을 Model로 전달해주는 역할을 한다. 

이런 패턴은 프로그램이 커져도 유지보수가 상대적으로 쉽다. 왜냐하면 프로그램의 UI를 바꾸고 싶으면 View부분만 바꿔주면 되고 로직을 바꾸고 싶다면 Model부분만 바꾸면 되기 때문이다.

또한 Apple은 iOS를 개발할 때 MVC를 권장합니다. MVC로 개발하기 쉽게 만들어놨기 때문에 권장한다고 볼 수 있다.

![1*jIPmux_88FcVLxtXenbYUA](https://miro.medium.com/max/3589/1*jIPmux_88FcVLxtXenbYUA.png)

이 그림을 보면 Model과 View사이에 중앙선이 있는데 이는 절대 서로에게 접근할 수 없다는 뜻과 같다. 그래서 Controller-View 나 Controller-Model로의 접근은 가능하다. 

그러면 Model-Controller로의 접근은 어떤가? Model은 데이터의 값을 바꾸고 관리만해야한다. 그럼 어떻게 값을 전달할 것인가? 바로 __Notification__ 을 사용한다. Notification이란 Model의 값이 바뀌었을 때 직접 전달하는 게 아니라 Model이 값이 바꼈다고 알려주면 Controller가 이를 듣고 Model에 접근하여 할 수 있다.

다음으로 View-Controller로의 접근은 어떤가? View는 화면을 갱신하는 역할이기 때문에 유저가 View에 값을 입력하거나 터치했을 때 그 변화를 Controller에 직접 전달하면 안된다. 그럴 땐 __Delegate__ or __Data Source__ 를 사용하면 된다. 

-----

#### MVC 패턴의 장단점

__장점__

1. 생산성이 좋다.

__단점__

1. iOS의 MVC는 분리가 완전하지 않아서 실제로 View의 생명주기에 관한 코드나 네트워크 통신에 관한 코드도 Controller에 위치해있어서 Controller의 크기가 커치는 경향이 있다.

------

### Facade패턴 in iOS

#### Facade 디자인 패턴이란?

: 복잡한 서브 시스템에 대한 단인 인터페이스를 제공한다. 사용자를 일련의 클래스 및 해당 API에 노출시키는 대신 하나의 간단한 통합 API만 노출한다.

![facade2](https://koenig-media.raywenderlich.com/uploads/2013/07/facade2.png)

API 사용자는 아래에 있는 복잡성을 완전히 인식하지 못한다. Facade 패턴은 많은 클래스로 작업할 때, 특히 사용하기 복잡하거나 이해하기 어려운 경우에 이상적이다.

#### Facade 패턴을 사용하는 방법

> bludLibrary 프로젝트 기준

<code>PersistencyManager</code> 는 앨범 데이터를 <code>HTTPClient</code>에 저장하고 원격통신을 처리해야한다. 

이 패턴을 구현하기 위해서는 오직 <code>LibraryAPI</code> 만 보유해야한다. 그 다음 해당 서비스에 액세스하는 간단한 API를 공개한다.

![design-patterns-part1-facade-1-480x87](https://koenig-media.raywenderlich.com/uploads/2017/05/design-patterns-part1-facade-1-480x87.png)

이렇게 말이다.

### Decorator 패턴 in iOS

#### Decorator 디자인 패턴이란?

: 코드를 수정하지 않고 객체에 동작과 책임을 동적으로 추가한다. 클래스를 다른 객체로 감싸서 클래스의 동작을 수정하는 클래스의 대안이다.

#### 확장과 위임

- 확장

  확장을 추가하면 서브 클래스 없이 기존 클래스로, 구조 또는 열거 유형에 새로운 기능을 추가할 수 있는 매우 강력한 매커니즘이다. <code>UIView</code> 와 같은 Cocoa 클래스에 고유한 메소드를 추가할 수 있다

- 사용 방법

  > blueLibrary 프로젝트 기준

  앨범 타이틀은 Album 모델이므로 Album 구조체의 확장을 만든다. 

- 위임

  한 객체가 다른 객체를 대신하거나 다른 객체를 조정하는 매커니즘이다. 

- 사용 방법

  > blueLibrary 프로젝트 기준

  확장을 해서 중괄호 뒤에 Delegate 속성 추가하기

-----

### Adapter 패턴 in iOS

#### Adapter 디자인 패턴이란?

: 어댑터를 사용하면 호환되지 않는 인터페이스가 있는 클래스를 함께 사용할 수 있다. 객체를 감싸고 해당 객체와 상호 작용할 수 있는 표준 인터페이스를 제공

-------

### Observer 패턴 in iOS

#### Observer 디자인 패턴이란?

: observer = 관찰자, 해당 프로퍼티가 변경 되는 걸 관찰하고 있다가 변경되는 시점에서 update가 수행되게 되는 형탱

Cocoa는 두 가지 방식으로 observer 패턴을 구현한다. 알림과 키 값 관찰

#### 알림

개체가 다른 개체에서 메세지를 보낼 수 있는 구독 및 게시 모델을 기반으로 한다.

Apple은 알림을 많이 사용한다. <code>UIKeyboardWillShow</code>, <code> UIKeyboardWillHide</code>, <code>UIApplicationDidEnterBackground</code>

#### 키 값 관찰(KVO)

객체는 특정 속성에 대한 변경 사항을 통지하도록 요청할 수 있다. 자체 또는 다른 객체의 개체 중 하나이다. 

------

### Memento 패턴 in iOS

#### Memento 디자인 패턴이란?

: 객체 내부 상태를 갭처하고 외부화한다. 어딘가에 물건을 저장한다고 생각, 나중에 이 외부화 된 상태는 캡슐화를 위반하지 않고 복원될 수 있다. == 개인 데이터는 개인정보로 유지됨

