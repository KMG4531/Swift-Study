## 📌함수 기본

조건문이나 반복문 같은 Swift의 다른 문법들과 달리 함수에서는 소괄호(())를 생략할 수 없습니다.

Swift의 함수는 자유도가 굉장히 높은 문법 중 하나입니다.

기본으로 함수의 이름과 매개변수, 반환타입 등을 사용하여 함수를 정의합니다.

### 📐함수선언의 기본 형태

함수를 정의하는 키워드는 func입니다.

함수 이름을 지정해준 후 매개변수는 소괄호(())를 써줍니다.

반환 타입을 명시하기 전에는 ->를 사용하여 어떤 타입으로 반환될 것인지 명시해줄 수 있습니다.

반환을 위한 키워드는 다른언어와 같이 return입니다.

함수의 기본 형태를 보시면

*함수 기본 형태*

```swift
func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입...) -> 반환타입 {
    함수구현부
    return 반환값
}
```
위와 같이 정리한 것들이 있습니다.


기본 형태를 사용하여 sum이라는 함수를 만들어주겠습니다.

*기본형태 사용*

```swift
func sum(a: Int, b: Int) -> Int {
    return a + b
}
```

함수를 호출하는 방법은

|이름을 쓰고 소괄호 안에 매개변수이름 : 값 |을 입력하시면 됩니다.


*함수에 대한 호출*

```swift
sum(a: 6, b: 5)
```

*호출 결과*

![](https://images.velog.io/images/jkang4531/post/dd127346-ae7c-47ab-b6a7-81c8df4c1c3e/image.png)

함수를 호출을 해주고 a와 b에 값을 넣어주니 11이라는 값이 나오는 것을 알 수 있습니다.

### 📐반환 값이 없는 함수

반환 값이 없는 함수는 값의 반환이 굳이 필요하지 않을 때 사용합니다.

반환 타입을 "없음"을 의미하는 Void로 표기하거나 아예 반환 타입 표현을 생략해도 됩니다.

*반환 값이 없는 함수*

```swift
func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입...) -> void { 
    함수구현부
    return 반환값
}
```

*반환 값이 없는 함수 사용(Void 표기)*
```swift
func printMyName(name: String) -> Void {
    print(name)
}
```

*반환 값이 없는 함수 사용(Void 생략)*

```swift
func printYoutname(name: String) {
    print(name)
}
```
두 가지 방법으로 사용이 가능합니다


두 가지의 방법으로 함수 만들어 준 것을 호출하면
```swift
printMyName(name: "Mingu")
printYoutname(name: "Ben")
```

*호출 결과*
![](https://images.velog.io/images/jkang4531/post/2ad36979-e49f-4aa6-aea7-b4c665902ec4/image.png)

### 📐매개변수가 없는 함수
매개변수가 없다면 소괄호(()) 안을 비워줘도 됩니다.

위에도 말했듯이 없다고 해서 소괄호를 생략 할 수 없습니다.

*매개변수가 없는 함수*
```swift
func 함수이름() -> 반환타입 {
    함수 구현부
    return 반환값
}
```

*매개변수가 없는 함수 사용*
```swift
func maximumIntegerValue() -> Int {
    return Int.max
}
```

*매개변수가 없는 함수 출력*
```swift
maximumIntegerValue()
```

매개변수가 없기 때문에 아무것도 뜨지 않습니다.

### 📐매개변수와 변환값이 없는 함수

*매개변수와 변환값이 전부 없는 함수*
```swift
func 함수이름() -> Void {
    함수구현부
    return
}
```

나타내어보면
```swift
func hello() -> Void { print("hello") } 
```
이런식으로 나타내어 줄 수 있다.

보시면 한 줄로 표현하였는데

함수가 간단한 경우에는 줄바꿈을 하지 않고 코드를 작성하여도 됩니다.

*매개변수와 변환값이 전부 없는 함수 호출*
```swift
hello()
```
*호출결과*
![](https://images.velog.io/images/jkang4531/post/4bcd4899-864d-49ce-b504-28362f129a63/image.png)

---
## 📌함수 고급

### 📐매개변수 기본값
함수의 매개변수에 값이 들어오지 않아도 자동적으로 매개변수를 값게 되는 타입입니다.

매개변수 기본값을 선언 해주려면 매개변수 이름뒤에 타입을 써주고 매개변수 기본값을 할당해주면 됩니다.

매개변수 기본값은 매개변수 목록 중에 뒤쪽에 위치하는 것이 좋습니다.

*매개변수 기본값*
```swift
func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수 2타입 = 매개변수 기본값 ...) -> 반환타입 {
    함수구현부
    return 반환값
}
```

*매개변수 기본값이 없는 매개변수와 매개변수 기본값이 있는 매개변수 생성*
```swift
func greeting(friend: String, me: String = "Mingu") {  
    print("Hello \(friend)! I'm \(me)")
}
```
매개변수의 기본값이 없는 매개변수는 friend

매개변수의 기본값이 있는 매개변수는 me

*매개변수 기본값을 가지는 매개변수는 생략할 수 있습니다*
```swift
greeting(friend: "Eric") // Hello Eric! I'm Mingu
// 매개변수 me에는 매개변수의 값이 있기 때문에 따로 전달인자로 전달해 주지 않아도 된다. 
// greeting 이라는 함수가 동작을 하게 된다.

greeting(friend: "Ben", me: "Mango") // Hello Ben! I'm Mango
// 기본값 외에 따로 값을 넣어주고 싶다면 명시해주면 된다.
```

### 📐전달인자 레이블

전달 인자 레이블은 함수를 호출할 때 매개변수의 역할을 좀 더 명확하게 하거나 함수 사용자의 입장에서 표현하고자 할 때 사용합니다.

전달인자 레이블을 사용하면 함수의 중복 정의도 손쉽게 할 수 있습니다.

*전달인자 레이블*
```swift
func 함수이름 (전달인자 레이블 매개변수1이름: 매개변수1타입, 전달인자 레이블 매개변수2이름:
매개변수2타입...) -> 반환타입 {
    함수구현부
    return
}
```
*함수 내부에서 전달인자를 사용할 때 매개변수 이름 사용*
```swift
func greeting(to friend: String, from me : String) {  
    print("Hello \(friend)! I'm \(me)")
}
```

위에 greeting이라는 함수를 사용하였는데 greeting 함수와 똑같은 매개변수를 가지는 함수지만 to와 from이라는 전달인자 레이블을 사용해서 함수의 이름 자체가 바뀐 효과를 봤기 때문에 중복 정의로써의 역할을 수행할 수 있습니다.

greeting이라는 같은 이름을 가지고 있는 것으로 보이긴 하지만 실제로 Swift에서는 함수의 이름이 greeting 그리고 to, from까지 전부 함수의 이름으로 취급되기 때문에 위에 함수랑 다른 함수로 취급이 됩니다.

함수의 외부에서는 to 라는 전달인자 레이블을 사용해서 함수를 호출할 수 있고, 함수 내부에서는 friend 라는 이름을 가지고 매개변수 이름을 가지고 사용하게 됩니다.

*함수 호출*

함수를 호출할 때에는 전달인자 레이블을 사용해야 합니다.

```swift
greeting(to: "hana", from: "Mingu") // Hello hana! I'm Mingu
```

### 📐가변 매개변수

전달 받을 값의 개수를 알기 어려울 때 사용할 수 있습니다.

가변 매개변수는 함수당 하나만 가질 수 있습니다.

가변 매개변수를 사용하려면 매개변수 타입 뒤에 ...를 찍고 사용하면 됩니다.


*가변 매개변수*
```swift
func 함수이름(매개변수1이름: 매개변수1타입, 전달인자 레이블 매개변수2 이름: 
매개변수2타입...) -> 변환타입 {
    함수 구현부
    return
}
```

*친구에게 인사를 하는 함수*
```swift
func sayHelloToFriends(me: String, firends: String...) -> String {
    return "Hello \(firends)! I'm \(me)"
}
```
firends: String... 은 친구가 몇 명이 되어도 상관이 없다는 뜻 입니다.

```swift
print(sayHelloToFriends(me: "Mingu", firends: "Ben", "Eric", "Jenny"))
```

가변인자에 아무 값도 넘기고 싶지 않다면 전달인자 레이블을 생략하면 됩니다.

```swift
print(sayHelloToFriends(me: "Mingu"))
```

---

위에서 설명한 Swift 함수의 다양한 모양은 모두 섞어서 사용 가능합니다.

---

### 📐데이터 타입으로서의 함수
Swift는 함수형 프로그래밍 패러다임을 포함하는 다중 패러다임 언어입니다.

Swift의 함수는 일급객체이므로 상수, 변수, 상수 등에 저장이 가능하고 매개변수를 통해 전달할 수도 있습니다.

Swift의 함수는 데이터 타입으로써 표현할 수 있습니다.

*함수의 타입표현*

```swift
(매개변수1타입, 매개변수2타입...) -> 반환타입
```
반환타입은 절대적으로 생략할 수 없습니다.

예시 보며 알아봅시다.

ex)
```swift
var someFunction: (String, String) -> Void = greeting(to:from:)
someFunction("Ben", "Mingu")   // Hello Ben! I'm Mingu

someFunction = greeting(friend:me:)
someFunction("Ben", "Mingu")   // Hello Ben! I'm Mingu
```

someFunction이라는 변수안에 둘 다 String 타입의 매개변수를 가지고 반환값이 없는 함수가 들어올 수 있다고 명시를 해줬습니다.

아까 만들어둔 greeting이라는 함수를 someFunction에 할당을 해준 것입니다.

[위로 가서 코드를 보기 귀찮으신 분들을 위해 위에 있는 코드를 가져왔습니다.]
```swift
// 1. greeting 함수(to, from)

func greeting(to friend: String, from me : String) {  
    print("Hello \(friend)! I'm \(me)")
}

// greeting(to:from:)
// someFunction("Ben", "Mingu")   // Hello Ben! I'm Mingu
```
```swift
// 2. greeting 함수(friend:me:)

func greeting(friend: String, me: String = "Mingu") {  
    print("Hello \(friend)! I'm \(me)")
}

// someFunction = greeting(friend:me:)
// someFunction("Ben", "Mingu")   // Hello Ben! I'm Mingu
```

타입이 다른 함수는 할당할 수 없습니다.
```swift
someFunction = sayHelloToFriends(me: friends:)
```
![](https://images.velog.io/images/jkang4531/post/f52cef4a-40fa-43d8-a8be-e9248954de03/image.png)

friends가 String 타입이긴 하지만 가변 매개변수를 가지기 때문에 타입이 다릅니다.


함수타입을 매개변수 타입으로 지정을 해주면 function이라는 매개변수를 안에서도 실행 가능합니다.

```swift
func runAnother(function: (String, String) -> Void) {  
    function("Jenny", "rona")
}
```

함수를 직접 넘겨줄 수도 있고, 변수에 담겨있는 someFunction을 넘겨줄 수도 있습니다.
```swift
runAnother(function: greeting(to:from:))
// Hello Jenny! I'm rona

runAnother(function: someFunction)
// Hello Jenny! I'm rona
```

