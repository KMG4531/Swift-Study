
## 📌 열거형

열거형은 연관된 항목들을 묶어서 표현할 수 있는 타입입니다.

enum은 타입이므로 대문자 카멜케이스를 사용하여 이름을 정의합니다.

각 case는 소문자 카멜케이스로 정의합니다.

각 case는 그 자체가 고유의 값입니다.

### 📐 열거형 기본

```swift
enum 이름 {
    case 이름1
    case 이름2
    case 이름3, 이름4, 이름 5
    ...
}
```

### 📐 열거형 예제

```swift
enum Weekday{
    case mon	// 한 개씩 만듬
    case tue
    case wed, thu, fri, sat, sun	// 연속해서 만듬
}

var day: Weekday = Weekday.mon	// 열거형 case를 나타내는 방법 (= 열거형이름 케이스이름)
day = .tue	// 위에 처럼 나타내주고 축약하여 나타내도 됨 (= 케이스이름)

print(day)


switch day {	// switch 구문에 열거형 타입 사용가능.
    case .mon, .tue, .wed, .thu:
    	print("평일입니다")
    case Weekday.fri:
    	print("불금 파티")
    case .sat, .sun:
    	print("주말")
}
```

[코드 설명]

Weekday를 열거형으로 만들어주었습니다.

case를 한 개씩 만들어줘도 되고, 아니면 연속해서 만들어줘도 됩니다.

열거형의 케이스를 나타내는 문법은 var day: Weekday = Weekday.mon으로 나타내 주었습니다.

열거형 케이스를 나타내는 방법은 [var 변수이름: 열거형이름 = 열거형이름.케이스이름] 으로 나타내줄 수 있습니다.
