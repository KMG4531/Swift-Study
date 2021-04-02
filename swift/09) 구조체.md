## 구조체

Swift의 구조체는 타입을 정의하는 것이기 때문에 Upper Camel Case를 사용합니다.

struct라는 키워드를 사용합니다.


*정의*
```swift
//struct 이름 {
//	구현부
//}
```

Sample이라는 구조체와 프로퍼티 및 메서드를 예시를 통해 알아봅시다.
```swift
struct Sample {
	var mutableProperty: Int = 100		// 가변 프로퍼티
    	let immutableProperty: Int = 100	// 불변 프로퍼티
        
        static var typeProperty: Int = 100	// 타입 프로퍼티
        
        // 인스턴스 메서드
        func instanceMethod()	{
        	print("instance method")
        }
        
        // 타입 메서드
        static func typeMethod()	{
        	print("type method")
        }
}
```

프로퍼티와 메서드는 어떤 타입 안에 들어있는 것을 프로퍼티라고 하고,

타입 안에 들어가 있는 함수를 메서드라고 생각하시면 됩니다.

구조체 내부에 var와 let으로 선언을 해주었습니다.

var로 선언해 준 것은 값을 변경해 줄 수 있는 가변 프로퍼티이고,

let으로 선언해 준 것은 값을 변경할 수 없는 불변 프로퍼티입니다.

static 키워드를 var나 let 앞에 붙여주게 되면 Sample에서 사용할 수 있는 타입 프로퍼티가 됩니다.


var와 let으로 선언해 준 것은 인스턴스 프로퍼티라고 생각하시면 됩니다.

밑에 코드는 인스턴스에서 사용할 수 있는 인스턴스 메서드입니다.

```swift
        func instanceMethod()	{
        	print("instance method")
        }
```

static 키워드를 앞에 붙이면 타입 메서드가 됩니다.

```swift
        static func typeMethod()	{
        	print("type method")
        }
```

## 구조체를 사용하는 방법

### 가변 인스턴스

```swift
var mutable: Sample = Sample()
```

앞에 var로 선언해 줬기 때문에 내부의 프로퍼티의 값들을 변경해 줄 수 있습니다.

```swift
mutable.mutableProperty = 200
```

결과

![1](https://images.velog.io/images/jkang4531/post/88d3326f-8565-4ef4-86c9-7fd2c40f652a/image.png)

mutableProperty의 값이 100에서 200으로 변경이 된 것을 알 수 있습니다.

let으로 선언된 immutableProperty는 당연히 값을 바꿀 수 없겠지요~


### 불변 인스턴스

```swift
let immutable: Sample = Sample()
```
위의 코드는 let으로 선언한 불변 인스턴스입니다.

let으로 선언한 불변 인스턴스 같은 경우 아무리 가변 프로퍼티로 선언을 하더라도 값을 변경해 줄 수 없습니다.

```swift
immutable.mutableProperty = 200
```

결과

![2](https://images.velog.io/images/jkang4531/post/3eea9b90-0784-41e8-9b8e-27fd1eab90d7/image.png)

불변 인스턴스라 값을 변경해 주실 수 없는 것을 알 수 있습니다.


### 타입 프로퍼티 및 메서드

```swift
Sample.typeProperty = 300
Sample.typeMethod()	// type method

// mutable.typeProperty = 400
// mutable.typeMethod()
```

타입 프로퍼티 같은 경우 Sample이라는 구조체 타입 자체가 사용할 수 있는 
프로퍼티와 메서드를 뜻합니다.

위에 있는 가변 인스턴스에서 설명한 mutable은 인스턴스에서 사용할 수 있는 프로퍼티와 메서드였는데 타입 프로퍼티를 보게 되시면 Sample이라는 타입 자체에서 사용할 수 있는 프로퍼티와 메서드가 됩니다.

또한 인스터스에서 타입 프로퍼티나 타입 메서드를 사용하려고 한다면 오류가 뜨며 사용이 불가능합니다.

```swift
mutable.typeProperty = 700
mutable.typeMethod()
```

결과

![3](https://images.velog.io/images/jkang4531/post/d75305e0-83cf-4968-94b1-f7ea0f24c811/image.png)

오류가 나는 것을 확인하실 수 있습니다.


## Ex)학생 구조체

```swift
struct Student {
    var name: String = "unknown"
    var [backtic]class[backtic]: String = "Swift" // [backtic]을 기호로 변경해 사용하시기 바랍니다.
   
    static func selfIntroduce() {
        print("학생 타입입니다")
    }
    
    func selfIntroduce() {
        print("저는 \(self.class)반 \(name)입니다")
    }
}

// 타입 메서드 사용
Student.selfIntroduce() // 학생 타입입니다

// 가변 인스턴스 생성
var mingu: Student = Student()
mingu.name = "Mingu"
mingu.class = "Swift"
mingu.selfIntroduce()   // 저는 Swift반 Mingu입니다
```

코드를 이해하기 쉽게 하나하나 설명드리겠습니다.(물론 제가 이해한 방식입니다!)

제일 먼저 Student라는 구조체를 만들어줬습니다.

var name: String = "unknown" 가변 프로퍼티를 만들어주고

var [backtic]class[backtic]: String = "Swift" 키워드로 [backtic]class[backtic]라는 이름을 만들어주었습니다.

(github backtic 문자열을 입력할 수 없어서 [backtic]로 작성하겠습니다. ₩ 모양에서 backtic 기호로 바꾸는 법은 밑에 하이버링크로 만들어놨습니다.)

backtic을 사용하여 키워드를 묶어주면 이름으로 사용할 수 있습니다.

static func selfIntroduce() {...} 은 앞에 static이 붙었으니 타입 메서드겠죠.

func selfIntroduce() {...}은 인스턴스 메서드입니다. 

selfIntroduce 안에 print("저는 \(self.class)반 \(name)입니다")을 만들어 줬는데 self는 인스턴스 자신을 지칭하며, 몇몇 경우는 제외하고 사용은 선택사항입니다.
> self가 왜 쓰이는지 정확히 모르겠어서 야곰님 github에 가서 찾아봤더니 정확하게 설명해 주셔서 가져왔습니다.

Student 타입이 자체적으로 사용할 수 있게 selfIntroduce()라고 타입 메서드를 만들어 줬기 때문에 "학생 타입입니다"라는 타입 메서드가 실행됩니다.

var mingu: Student = Student()
mingu.name = "Mingu"
mingu.class = "Swift"

가변 인스턴스를 생성해 준 다음에 mingu.selfIntroduce()를 하게 되면 
인스턴스 메서드로 구현된 func selfIntroduce() {...}메서드가 
호출이 되어 "저는 Swift반 Mingu입니다"가 나옵니다.

만약 가변 인스턴스가 아닌 불변 인스턴스로 생성을 해줬다면 프로퍼티 값도 변경 불가능하기 때문에 컴파일 오류가 발생합니다.
```swift
let ben: Student = Student()

//ben.name = "Ben"	// 오류 발생
ben.selfIntroduce()
```
name에서 변경을 해주려고 하면 오류가 발생하게 되고,

ben.selfIntroduce()을 사용하면 "저는 Swift반 unknown입니다"가 나올 것입니다.

----
맥북을 쓰시는 유저분들은 키보드에 [backtic]가 안 보이실 텐데 사실 ₩ 달러 모양 키입니다.

[backtic]로 바꾸는 방법은 밑에 링크를 참조하셔서 바꾸시면 될 거 같습니다.

[₩에서 -> `로 바꾸기](https://nathan29849.medium.com/mac-os-x-%EC%97%90%EC%84%9C-%EA%B0%80-%EC%95%84%EB%8B%8C-backtick-%EC%9D%84-%EC%9E%85%EB%A0%A5%ED%95%98%EB%A0%A4%EB%A9%B4-%ED%95%9C%EA%B8%80%EB%AA%A8%EB%93%9C%EC%97%90%EC%84%9C-45d427fcb0a)
