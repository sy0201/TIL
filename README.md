# 6/23(금)

- foreground 상태에서 push 알림 수신 기능
    - iOS 10 이전에는 앱이 켜진 상태에서 push 핸들링을 하려면 직접 만든 custom alert만 띄울수 있었으나 iOS 10 이상부터는 앱이 켜졌을 때도 iOS에서 제공하는 푸시 형태로 띄울 수 있게 되었다.
    알림이 도착했을 때 앱이 foreground 에 있으면 userNotificationCenter에서 아래 메서드를 호출하여 알림을 앱에 직접 전달한다. 
    **userNotificationCenter(_:willPresent:withCompletionHandler:)**
    함수를 이용하여 notification 이 왔을때 앱이 실행중이면 user notification center에서 해당 메서드를 콜해줘서 notification을 직접 앱으로 쏴준다고한다.
    여기서 액션 처리를 해주고 completionHandler 블럭을 구현하고 user에게 alert를 어떻게 보여줄지 지정해줘야 한다. 
    해당 메서드를 구현하지 않으면 시스템은 옵션을 블록에 전달한 것처럼 동작되며 시스템은 알림의 원래 옵션을 사용하여 사용자에게 경고를 보냅니다.

- push 메시지 탭시 연결된 url로 이동해야하는데 기존에는 함수로 구현되어있었고, 클로저로 수정한 부분을 보고 왜 클로저로 수정했는지 궁금해졌습니다.
    - 클로저 사용시 비동기적인 작업의 완료를 감지하고 작업완료후 추가적인 작업을 수행할수 있는데 웹페이지 로드가 완료되기 전에 다른 작업을 시작하지 않도록 보장하거나 로드작업 성공여부에 따라 다른 동작을 수행할 수 있도록 제어할 수 있어서 클로저를 사용하게된 이유를 공부했습니다.
 
- iOS 최소버전 수정시 특정 버전에 대한 분기처리가 필요하게 되어 #available 과 @available의 키워드 차이를 공부하였습니다.
    
    ### #available
    
    여러 플랫폼에서 서로 다른 처리를 결정하기 위해 if문 또는 guard문과 같이 사용된다.(*은 필수)
    
    *를 사용하여 모든 플랫폼 이름에 대한 선언의 가용성(availablility)을 나타낼 수도 있다.
    Bool을 반환하는 런타임 검사
    
    ```swift
    if #available(iOS 12.0, *) {
    	//iOS 12 이상~
    } else {
    	//iOS 11 이하 버전
    }
    ```
    
    ### @available
    
    함수, 클래스, 프로토콜을 플랫폼 별로 제한할 때 사용한다. 타입 또는 프로토콜이 적용되는 플랫폼 및 OS를 나타낸다. #available과 다르게 컴파일 시 경고 또는 오류를 생성한다.
    
    ```swift
    //iOS 12를 포함한 그 이상의 버전에서만 test함수를 호출할 수 있다.
    @available(iOS 12, *)
    func test() { }
    
    //여러개의 플랫폼도 지정가능하다.
    @available(iOS 12, macOS 10.12, *)
    func test2() { }
    
    //모든 플랫폼에서 unavailable하다는 뜻
    @available(*, unavailable)
    func test3() { }
    
    //모든 플랫폼에서 unavailable하다는 뜻
    @available(macOS, unavailable)
    func test3() { }
    ```

    추가로 공부한 내용(신규 프로젝트파일 생성하면서 무심코 지나쳤던 부분을 공부하였습니다)

- New File 생성시 ****Swift File과 Cocoa Touch Class의 차이점****
    
    
    cocoa touch class 는 iOS를 위한 UIFramework이다. Subclass of로 원하는 개발환경을 선택하고 Class 명을 입력하면 된다. 예를들어 UIStackView로 선택 후 생성파게 되면 UIStackView를 상속하여 코드가 작성된 상태로 파일이 생성된다.  UIKit 을 import 한다
    
    Swift File은 바로 저장경로를 물어보며 file name 입력시 바로 생성된다. 그리고 만들어진 파일은 빈 파일로 생성된다.  Foundation 을 import 한다
    
- Cocoa Touch
코코아 터치란? iOS 애플리케이션 개발에 주 축을 이루는 개발환경으로, 애플리케이션의 다양한 기능 구현에 필요한 여러 프레임 워크를 포함하는 최상위 계층이다. 참고로 코코아 계층은 macOS 애플리케이션 제작에 사용한다.
    - ‘코코아’라는 단어는 Objective-C 런타임을 기반으로 하고, NSObject를 상속받는 모든 클래스 또는 객체를 가리킬 때 사용한다.
    - ‘코코아 터치’ 또는 ‘코코아’는 iOS 또는 macOS의 전반적인 기능을 활용해 애플리케이션을 제작할 때 사용하는 프레임 워크 계층이다.
    
    
- UIKit
    
    iOS,iPadOS, tvOS 앱의 핵심 인프라를 구성하는데 사용할 수 있는 구성요소를 포함하고 있다. 앱 구축을 이해 다양한 기능을 제공한다. 
    
    - UIKit는 iOS 애플리케이션의 사용자 인터페이스를 구현하고 이벤트를 관리하는 프레임 워크입니다.
        - 제스처 처리, 애니메이션, 그림 그리기, 이미지 처리, 텍스트 처리 등 사용자 이벤트 처리를 위한 클래스를 포함한다.
        - UITableView, Slider, UIButton, UITextField, Alert 등 애플리케이션의 화면을 구성하는 요소를 포함한다.
        - UIResponder에서 파생된 클래스나 사용자 인터페이스에 관련된 클래스는 애플리케이션의 메인 스레드(혹은 메인 디스패치큐)에서만 사용해야 한다.
    
    ### UIKit 기능별 요소
    
    - 사용자 인터페이스
        - View and Control: 화면에 콘텐츠 표시
        - View Controller: 사용자 인터페이스 관리
        - Animation and Haptics: 애니메이션과 햅틱을 통한 피드백 제공
        - Window and Screen: 뷰 계층을 위한 윈도우 제공
    - 사용자 액션
        - Touch, Press, Gesture: 제스처 인식기를 통한 이벤트 처리 로직
        - Drag and Drop: 화면위에서 드래그 앤 드롭 기능
        - Peek and Pop: 3D터치에 대응한 미리 보기 기능
        - Keyboard and Menu: 키보드 입력을 처리 및 사용자 정의 메뉴 표시
    
    UIKit을 import하면 Foundation도 import 되기 때문에 함께 import할 필요는 없다.
    
- Foundation
    
    코코아 터치 프레임워크에 포함되어있는 Foundation 프레임워크다. 데이터 저장 및 지속성, 텍스트처리, 날짜 및 시간 계산, 정렬 및 필터링, 네트워킹을 포함하여 앱 및 프레임워크에 대한 기능의 기본 계층을 제공한다. 즉 iOS 애플리케이션의 운영체제 서비스와 기본기능을 포함하는 프레임워크이다. 
    
    - 데이터타입, 날짜 및 시간 계산, 필터 및 정렬, 네트워킹 등 기본기능을 제공한다.
    
    Foundation에서 제공하는 데이터 타입 및 컬렉션 타입의 대부분은 Objc 언어의 기능에서 지원하지 않는 것이기 때문에 언어기능을 보완하기 위한 구현이며, Swift 에서는 이에 해당하는 데이터 타입과 기능 대부분을 Swift 표준 라이브러리에서 제공한다.
