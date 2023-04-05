# Enum
## _Enumeration_
---
열거형은 관련된 값으로 이루어진 그룹을 공통의 형(type) 으로 선언해 형 안전성(type-safety)을 보장하는 방법으로 코드를 다룰 수 있게 해준다.

즉, 같은 주제로 연관된 데이터들을 멤버로 구성하여 나타내는 자료형이다.
예를 들어 아이돌 그룹안에 포지션이 (vocal, dance, rap) 이 있다. 이 포지션을 저장해 두어야한다면 type을 통해 저장할 수도 있다.

```swift
var idol1: String = "vocal"
var idol2: String = "dance"
var idol3: String = "rap"
```

입력할때마다 값을 직접 넣으면 vacla danse 이렇게 오타를 낼수 있는데, 가독성과 안전성이 떨어진다
이때 공통된 주제에 대하여 이미 정해놓은 입력 값만 선택해서 받고 싶을때 사용하는 것이 열거형이다.
Enum은 값 형식으로 Stack에 저장되어 성능면에서도 향상된다.

- 열거형은 저장속성을 만들 수 없다.
- 타입저장속성은 만들 수 있다.

## Enumeraion Syntax (열거형 문법)
---

```swift
enum CompassPoint {
		case north
		case south
		case east
		case west
}
```
swift에서 열거형은 생성시 각 case별로 기본 Integer값을 할당하지 않는다. 대신 Swift에서 열거형의 각 case는 CompassPoint으로 선언된 온전한 값이다.

아래 코드처럼 한줄로 작성도 가능하다.
```swift
enum Planet {
    case mercury, venus, earth, mars, jupiter, saturn, uranus, neptune
}
```
각 열거형 정의는 완전 새로운형(Type)을 정의한다. Swift 의 다른형(Type)과 마찬가지로 형의 이름은 대문자로 시작한다.








> 출처
> https://babbab2.tistory.com/116
> https://jusung.gitbook.io/the-swift-language-guide/language-guide/08-enumerations
> https://seons-dev.tistory.com/30
> https://jusung.gitbook.io/the-swift-language-guide/language-guide/08-enumerations

