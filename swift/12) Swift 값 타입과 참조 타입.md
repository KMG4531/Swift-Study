## 📌 값 타입 / 참조 타입

지금까지 배웠던 class, struct, Enum을 살펴봅시다.


### 📐 class
* 단일 상속
* (인스턴스/타입) 메서드
* (인스턴스/타입) 프로퍼티
* **참조 타입**
* Apple 프레임워크의 대부분의 큰 뼈대는 모두 클래스로 구성


### 📐 struct
* C 언어 등의 구조체보다 다양한 가능
* 상속 불가
* (인스턴스/타입) 메서드
* (인스턴스/타입) 프로퍼티
* **값 타입**
* Swift의 대부분의 큰 뼈대는 모두 구조체로 구성


### 📐 Enum
* 다른 언어의 열거형과는 많이 다른 존재
* 상속 불가
* (인스턴스/타입) 메서드
* (인스턴스/타입) 연산 프로퍼티
* ** 값 타입**
* Enumeration
* 유사한 종류의 여러 값을 유의미한 이름으로 한 곳에 모아 정의
  예) 요일, 상태값, 월(Month) 등
* 열거형 자체가 하나의 데이터 타입
  열거형의 case 하나하나 전부 하나의 유의미한 값으로 취급
* 선언 키워드 - enum


### 📐 Class/Struct/Enum
밑에 있는 표를 보시면
![표](https://images.velog.io/images/jkang4531/post/b92ddc55-1303-4595-8f62-13136cb9dcce/image.png)
Class만 참조 타입이고 상속을 받을 수 있습니다.

Extension 기능은 나중에 블로그로 정리하겠습니다 :)


## 📌 구조체는 언제 사용하지?
* 연관된 몇몇의 값들을 모아서 하나의 데이터타입으로 표현하고 싶을 때
* 다른 객체 또는 함수 등으로 전달될 때
* **참조가 아닌 복사를 원할 때**
* 자신을 상속할 필요가 없거나, 자신이 다른 타입을 **상속받을 필요가 없을 때**
* Apple 프레임워크에서 프로그래밍을 할 때에는 주로 클래스를 많이 사용


## 📌 값 타입 VS 참조 타입
* 값 타입 (Value)
  * 데이터를 전달할 때 값을 복사하여 전달하는 방식

* 참조 타입 (Reference)
  * 데이터를 전달할 때 값의 메모리 위치를 전달하는 방식
  
**Class vs Struct/Enum**
참조 타입과 값 타입의 비교 코드입니다.

코드 안에 주석으로 설명을 해놨으니 보시면 됩니다.


```swift
// 구조체 구현
struct ValueType {
    var property = 1
}

// 클래스 구현
class ReferenceType {
    var property = 1
}

// 첫 번째 상수 구조체 인스턴스
let firstStructInstance = ValueType()
// 두 번째 변수 구조체 인스턴스에 첫 번째 구조체 인스턴스를 복사합니다.
var secondStructInstance = firstStructInstance
// 두 번째 변수 구조체 프로퍼티 값 2로 수정하면
secondStructInstance.property = 2

// 첫 번째 인스턴스의 프로퍼티 값은 1이 나오게 되고, 두 번쨰 인스턴스의 값은 2가 나오게 됩니다.
// 그 이유는 firstStructInstance가 똑같이 복사가 되어서 secondStructInstance에 들어가기 때문에
// 똑같은 모양의 구조체가 하나 더 생성이 되어서 들어간 것 입니다.
print("first struct instance property : \(firstStructInstance.property)")   // 1
print("second struct instance prooerty : \(secondStructInstance.property)") // 2

// 클래스 인스턴스 생성 후 참조 타입을 생성해줍니다.
let firstClassReference = ReferenceType()
// 첫 번째 클래스 인스턴스를 두 번째 인스턴스에 할당해줍니다.
var secondClassReference = firstClassReference
// 그 이후 프로퍼티 값을 2로 바꿔줬습니다.
secondClassReference.property = 2

// 첫 번째 참조 프로퍼티 값이 2로 변경이 되었습니다.
// 하나의 인스턴스를 가지고 두 참조가 같은 인스턴스를 가리키기 때문에 참조값이 복사됩니다.
print("first class reference property : \(firstClassReference.property)")   // 2
print("second class reference property : \(secondClassReference.property)") // 2
```


Swift 언어는 구조체, 열거형 사용을 선호하기 때문에 잘 알아두셔야 합니다.

하지만 Apple 프레임워크는 대부분 클래스를 사용합니다.

그러므로 Apple 프레임워크 사용시 구조체/클래스 선택은 우리의 몫 입니당:)
