### Bundle?

```swift
class Bundle : NSObject	
```

Apple은 <code>Bundle</code> 을 사용하여 앱, 프레임 워크, 플러그인 및 기타 여러 특정 유혀의 컨텐츠를 나타낸다. 번들 객체를 사용하면 번들의 구조를 몰라도 번들의 리소스에 액세스 할 수 있다.

- 번들 오브젝트는 번들구조, 사용자 환경 설정, 사용 가능한 현지화 및 기타 관련 요소를 고려하려 항목을 찾기 위한 단일 인터페이스 제공

- 모든 실행 파일은 번들 객체를 사용하여 앱의 번들 내부 또는 다른 위치에 있는 알려진 번들에서 리소스를 찾을 수 있다.

- 번들 객체를 사용하여 컨테이너 디렉토리 또는 파일 시스템의 다른 부분에서 파일을 찾을 수 없다.

  