07) Optional에서 다뤄봤던 것을 가지고 Optional의 값을 꺼내오는 방법과

어떤 식으로 활용을 하는지에 대해 다뤄보겠습니다.

## 📌 Optional Unwrapping

값을 꺼내는 방법에는두 가지지 방법이 있습니다.

* Optional Binding - 옵셔널 바인딩
* Force Unwrapping - 강제 추출

먼저 Optional Binding부터 알아봅시다.

### 📐 Optional Binding

Optional Binding 방법은nil 체크를 함과 동시에 안전하게 값을 추출할 수 있는 값입니다.

값이 있는지 없는지 확인을한 후후 값이 있으면 값을 빼오고 값이 없으면 지나치는 방식입니다.

if-let 방식으로 Optional Binding을 해줄 수 있습니다.
#### if-let

```swift
func printName(_ name: String) {
	print(name)
}

var myName: String! = nil

if let name: String = myName {
	printName(name)
} else {
	print("myName == nil")
}
```
코드에 보이는 것처럼 암시적 추출 옵셔널 형식도 Optional이기 때문에

if-let 방식으로 값을 꺼내올 수 있습니다.

name이라는 상수는 if-let 구문 안에서만 사용이 가능합니다.

상수 사용범위를 벗어나면 컴파일 오류가 발생하게 됩니다.

 
위와 같이 한 번에 하나씩 바인딩 할 수 있는 게 아니라 쉼표를 사용하여 여러 옵셔널 변수들을 바인딩을 할 수 있습니다.


```swift
var myName: String? = "Mingu"
var yourName: String? = nil

if let name = myName, let friend = yourName {
	print("\(name) and \(friend)")
}
```
위와 같이 쉼표를 사용하여 여러 옵션널 변수들을 바인딩 할 수 있습니다.

하지만 변수에 yourName이 nil이기 때문에 실행되지 않습니다.

그 이유는? myName과 yourName에 값이 들어가야 실행이 되기 때문입니다.

그러면 yourName에 값을 할당해 준 후 실행을 해봅시다.
```swift
var myName: String? = "Mingu"
var yourName: String? = "Ben"

if let name = myName, let friend = yourName {
	print("\(name) and \(friend)")
}
```
![](https://images.velog.io/images/jkang4531/post/0e4d5ac2-a624-4b44-93ba-7a07b096a5fb/image.png)

yourName에 값을 할당하고 나서 잘 출력되는 것을 보실 수 있습니다.



### 📐 Force Unwrapping

옵셔널을 강제 추출하는 방식입니다.

옵셔널을 벗기고 강제로 값을 넘겨준다 라는 의미로 생각하시면 될 꺼 같습니다.

```swift
func printName(_ name: String) {
	print(name)
}

var myName: String? = "Mingu"
printName(myName!) // Mingu
```

옵셔널? 가 벗겨지면서 안에 있던 값이 myName!으로 가고 Optional 타입이 아닌
String 타입으로 값을 넘겨주게 됩니다.

myName!를 보시면! 가 붙어있는데!를 붙이게 되면 Optional 타입의 값을 강제로 추출한다고 생각하시면 됩니다.

강제로 추출된 실질적인 값인 Mingu가 printName에 전달됩니다.


만약 myName에 nil 값을 할당하게 되면 어떻게 될까요?
```swift
myName = nil

print(myName!)
```
nil로 할당하고 강제 추출 시 값이 없으므로 런타임 오류가 발생합니다.

---
**옵셔널 강제 추출 방식보다 옵셔널 바인딩 방식으로 사용하는 것이 더 안전합니다.**
