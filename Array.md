# TIL

# Array
---
Swift 에서 array는 두개의 배열이 존재한다. Swift 에서 제공하는 Array, Foundation에서 제공하는 NSArray

|        | Array | NSArray |
| ------ | ------ | ------ |
| 타입 | 구조체 | 클래스 |
| 저장 위치 | Stack | Heap |
| Element(요소) 자료형 | 모두 동일한 자료형만 저장 가능 | 인스턴스라면 타입 상관없이 저장가능 (Int, Double 같은 구조체 타입은 저장 불가, NSNumber 같은 인스턴스로는 가능, 인스턴스기만 한다면 NSString, NSNumber 등 타입에 상관 없이 하나의 배열에 모두 저장 가능) |
| COW(copy-on-write) | O | X |
## Swift Collection Type

1) Array : 데이터를 순서대로 저장하는 컬렉션

2) Dictionary : 데이터를 키와 값으로 하나의 쌍으로 만들어 관리하며 순서가 없는 컬렉션

3) Set : 수학에서의 집합과 비슷한 연산을 제공하는 순서가 없는 컬렉션

```swift
var numberArray = [1, 2, 3, 4, 5]
let numberArray2 = [3, 55, 8, 12, 2, 75]
var stringArray = ["red", "blue", "orange", "black"]
```

배열의 타입 표기

```swift
// 정식 문법
let arrayType: Array<Int> = []

// type Annotation으로 생성하기
let emptyArray = [] // 타입 추론으로는 빈배열 생성 불가, 반드시 타입을 넣어줘야한다
let array1 = [1, 2, 3, 4] // 가능
let arrayType2: [String]
let arrayType3: [String] = []

//생성자로 생성하기
var array4 = Array<Int>()
var array5 = [Int]()
```

만약 하나의 배열에 여러 타입을 저장하고 싶으면 Type을 Any로 선언하거나, NSArray를 사용하면 된다.

```swift
var array6: [Any] = [1, "hi", 36.5]
var array9: NSArray = [1, "Sodeul", 20.4]
```

NSArray는 class 형식이라 무조건 인스턴스 요소로 구성되어야 한다.

array6 배열의 1, 36.5 는 각 Int, Double 이 아니라 NSNumber라는 인스턴스로 저장된다. 이런 경우 Swift의 장점(구조체로 만들어서 Stack에 저장됨)이 사라지고.. Any Type을 사용하면 컴파일 시 실행 오류를 잡기 힘들기 때문에 지양합니다!

배열의 기본 기능

```swift
var numberArray = [1, 2, 3, 4, 5]

numberArray.count   // 배열의 요소의 갯수 확인
numberArray.isEmpty // 배열의 요소가 비어있는지 아닌지 Bool 타입으로 나옴

numberArray.contains(5)     // 파라미터로 값을 전달 () 안의 값을 포함하고 있는지 확인
numbarArray.randomElement() // 랜덤으로 값 하나를 추출

numberArray.swapAt(0, 1) // 인덱스 값의 위치를 바꾸는 함수
```








> 출처
> -https://babbab2.tistory.com/92
> -앨런 문법강의
