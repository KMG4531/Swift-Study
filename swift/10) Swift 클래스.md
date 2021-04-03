## 📌 class

class는 앞에 배웠던 구조체와 매우 유사합니다.

서로 다른 점이 있다면 구조체는 값 타입인 반면,

class는 참조 타입입니다.

Swift의 class는 다중 상속이 되지 않습니다.

<정의>

```swift
// class 이름 {
//	구현부
//}
```

class는 구현부와 같이 프로퍼티와 메서드를 가질 수 있습니다.

class에서의 타입 메서드는 두 가지로 나눌 수 있습니다.

앞에 static과 class 키워드가 붙냐에 따라서 타입 메서드의 성질이 바뀝니다.

타입 메서드만 자세히 보시면 됩니다.

```swift
class Sample {
	var mutableProperty: Int = 100        	// 가변 프로퍼티
    	let immutableProperty: Int = 100    	// 불변 프로퍼티
        
        static var typeProperty: Int = 100   	 // 타입 프로퍼티
        
        // 인스턴스 메서드
        func instanceMethod()    {
            print("instance method")
        }
    
        // 타입 메서드
        // 상속을 받았을 때 재정의 불가 타입 메서드 - static
        static func typeMethod() {
            print("type method - static")
        }

        // 상속을 받았을 때 재정의 가능 타입 메서드 - class
        class func classMethod() {
            print("type method - class")
        }
}
```


### 📐 클래스 사용법
클래스 사용법을 알아봅시다.

밑에 있는 코드를 보시죠
```swift
var mutableReference: Sample = Sample()

mutableReference.mutableProperty = 200		// 변경 가능
// mutableReference.immutableProperty = 200	// 변경 불가능

let immutableReference: Sample = Sample()

immutableReference.mutableProperty = 200
// immutableReference.immutableProperty = 200

// immutableReference = mutableReference
```

class는 구조체와 다르게 mutable과 immutable을 let과 var로 사용한 인스턴스 
모두가 가변 프로퍼티 mutableProperty를 변경해 줄 수 있습니다.

처음부터 불변 프로퍼티로 선언된 immutableProperty는 불가능합니다.


구조체와 마찬가지로 타입 프로퍼티와 메서드를 사용하는 것도 크게 다를게 없습니다.
```swift
Sample.typeProperty = 300
Sample.typeMethod()	 // type method

//mutableReference.typeProperty = 400
//mutableReference.typeMethod()
```
