## 📌Optional
Swift의 핵심 개념임 Optional입니다.

Optional의 뜻은 값이 있을 수도, 없을 수도 있습니다.


### 📐Optional이 필요한 이유

* nil의 가능성을 명시적으로 표현해 줄 수 있습니다.

* nil의 가능성을 문서화하지 않고 코드만으로 충분히 표현할 수 있습니다.

* 전달받은 값이 옵셔널이 아니라면 nil 체크를 하지 않더라도 안심하고 사용할 수 있습니다.

예시를 보시면
```swift
// 1
// someOptionalParam can be nil
func someFunction(someOptionalParam: Int?) {
	// ...
}

// 2
// someParam must not be nil
func someFunction(someParam: Int) {
	// ...
}

// nil 전달
someFunction(someOptionalParam: nil)
someFunction(someParam: nil)
```
첫 번째 함수에는 Int Optional 타입이 명시되어 있고,

두 번째 함수에는 Optional 타입이 아닌 Int 타입이 명시가 되어있습니다.

두 개의 함수에 nil 값을 전달해 주겠습니다.

*결과*
![](https://images.velog.io/images/jkang4531/post/94e9546e-a033-4516-8e55-5792baf1eed5/image.png)

첫 번째 함수는 Optional 타입이 명시가 되어있어 nil을 받아도 상관없지만

두 번째 함수는 Optional이 아닌 타입에는 nil을 보낼 수 없다는 것을 알 수 있습니다.


### 📐enum + general
Optional은 enum + general의 합작품으로 볼 수 있습니다.

```swift
enum Optional<Wrapped> : ExpressibleByNilLiteral {
case none // 값이 없다
case some(Wrapped) // 값이 있다
}

let optionalValue: Optional<Int> = nil
let optionalValue: Int? = nil
```
열거형이 기본 타입이고 case none은 Optional의 값이 없다를 뜻하고, case some(Wrapped)은 Optional 안에 값이 있다를 두 가지 case로 구성이 되어 있습니다.

실제로 Optional를 선언할 때 타입은 Optional(Int)로 해주는 것이 완전한 문법이지만 Int?를 적어주면
Int의 Optional 타입이라는 것을 표현해 줍니다.

_**Velog오류로 인해< > 안에 Int를 표현할 수 없어 ( )로 대처했습니다.**_

  
### 📐Optional 표현
  
Optional 표현에는 **!, ?** 가 있습니다.
  
!를 먼저 살펴봅시다.

!는 암시적 추출 옵셔널이라고 말합니다.
  
타입 뒤에 !를 표현하는 것은 암시적 추출 옵셔널 형식이라는 것을 알 수 있습니다.
 
```swift
var optionalValue: Int! = 100  //Int! = 암시적 추출 옵셔널

switch optionalValue {
	case .none:
    	print("This Optional variable is nil")
    case .some(let value):
    	print("Value is \(value)")
}
```
Optional 타입 자체는 열거형이기 때문에 switch-case 구문으로 구분이 가능합니다.


암시적 추출 옵셔널 형식은 기존 변수처럼 사용이 가능하고 nil을 할당받을 수 있습니다.

하지만 잘못된 접근으로 인해서 런타임 오류가 발생할 수도 있습니다.

```swift
// 기존 변수처럼 사용 가능
optionalValue = optionalValue + 1

// nil 할당 가능
optionalValue = nil

// 잘못된 접근으로 인해서 런타임 오류 발생
optionalValue = optionalValue + 1
```
왜 잘못된 접근으로 인해서 런타임 오류가 발생할까요?
optionalValue = nil 값을 넣어줬는데 optionalValue에 접근을 하려다 보니 오류가 발생합니다.


?를 살펴봅시다.

?를 사용한 Optional은 일반적인 Optional입니다.

타입 뒤에 ?를 쓴 Optional은 값이 있을 수도 있고, 없을 수도 있는 변수입니다.

```swift
var optionalValue: Int? = 100

switch optionalValue {
	case .none:
    	print("This Optional variable is nil")
    case .some(let value):
    	print("Value is \(value)")
}
```
위와 똑같이 case .none과 case .some을 가지고 값이 있는지 없는지 구분을 해볼 수 있습니다.

Optional 타입이기 nil이 할당 가능합니다.

하지만 Optional과 일반 값은 다른 타입이므로 연산이 불가하기 때문에 기존 변수처럼 사용은 불가능합니다.

```swift
// nil 할당 가능
optionalValue = nil

// 기존 변수처럼 사용 불가능
optionalValue = optionalValue + 1
```
