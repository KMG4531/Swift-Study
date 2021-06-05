이번시간에는 상수와 변수 그리고 데이터 타입에 대해 알아보겠습니다.

## 상수와 변수

상수와 변수는 특정 데이터 타입에 해당하는 값의 이름입니다.

상수는 한번 값을 설정하면 다음에 변경할 수 없습니다.

변수는 생성 후 데이터 값을 변경할 수 있습니다.
 
##### 상수와 변수 선언 방법을 알아보겠습니다.

~~~swift
상수 선언 키워드 let
변수 선언 키워드 var

상수 선언
let 이름 : 타입 = 값

변수 선언
var 이름 : 타입 = 값
~~~

저런 식으로 선언할 수 있습니다. 하지만 값의 타입이 정말 명확하다면 상수와 변수를 코드를 줄일 수 있습니다.

~~~swift
let 이름 = 값
var 이름 = 값
~~~

이런 식으로 말이죠.

상수와 변수의 값 변화에 대해서도 알아보겠습니다.
 
~~~swift
// 상수와 변수 입력
let conatant : String = "차후 변경 불가 값"
var variable : String = "변경 가능"
~~~
 
상수와 변수의 값을 바꿔주겠습니다.

~~~swift
conatant = "!!오류!!"
variable = "오류 안남"
~~~

상수의 값을 변경해 줬을 시

![1번](https://KMG4531.github.io/assets/images/2021-03-23/a.png)

상수로 입력해 준 것은 오류가 나고 변수로 입력해 준 것은 오류가 안 나는 것을 알 수 있다.

오류를 보면 컴파일러가 [ Cannot assign to value: 'conatant' is a 'let' constant ]라고 말하네요.

이 말은 즉 [conatant는 상수로 선언되어 있으니 값을 받을 수 없다 ]입니다.

conatant를 주석 처리하고 print()를 활용해 실행시켰을 시

~~~swift
// conatant = "!!오류!!"
variable = "오류 안남"

print(conatant)
print(variable)
~~~

![2번](https://KMG4531.github.io/assets/images/2021-03-23/b.png)

상수로 선언한 것은 그대로 나오고, 변수로 선언한 것만 변경되는 것을 알 수 있습니다.


## 데이터 타입 기본

데이터 타입은 프로그램 내에서 다뤄지는 데이터의 종류를 뜻합니다. 

Swift는 

Swift의 기본 데이터 타입

- Int
- UInt
- Bool
- Float
- Double
- Character
- String


### Int

Int는 64비트 정수형 타입입니다. 양수와 정수, 0을 모두 포함할 수 있습니다.

~~~swift
var someInt : Int = -100 //(-100, 0, 100) 다 가능
~~~


### UInt

UInt는 부호가 없는 정수라고 칭합니다. 즉 양의 정수만 받을 수 있다는 것이지요. 

~~~swift
var someUInt : UInt = 100	// 음수나 실수 "X" 😡
~~~


### Bool

Bool 타입은 True, False 타입의 두 가지 값만 받을 수 있습니다.

~~~swift
var someBool : Bool = true // false
~~~

다른 언어와 같이 Bool 타입에 0 과 1도 넣고 실행시켜 봅시다.

```swift
someBool = 0
someBool = 1
```


#### 결과

![3번](https://KMG4531.github.io/assets/images/2021-03-23/c.png)

바로 에러가 뜨게 됩니다.

***자 여기서 질문 "민구님 다른 언어에서는 Bool 타입을 0과 1로도 표현하던데 왜 Swift는 안되는 거에요??"***

Swift의 언어는 다른 언어들과 다르게 데이터 타입이 예민하게 반응하고, 값을 변경해 준 0과 1을 보시면 0과 1은 Int 타입이기에 True와 False의 값만 받는 Bool 타입에서는 값을 받을 수 없습니다.



### Float

Float은 32비트의 부동 소수형 타입입니다. Float 타입의 장점은 정수를 입력받을 수 있습니다.

~~~swift
var someFloat : Float = 9.99
someFloat = 10
~~~

원래 값인 9.99를 10으로 나오게 값을 변경해 주고,

print(someFloat)로 값을 출력해보면

#### 결과

![4번](https://KMG4531.github.io/assets/images/2021-03-23/d.png)

10.0으로 정수 타입도 받을 수 있다는 것을 알 수 있습니다.


### Double

Double은 64비트의 부동 소수형 타입입니다. Double 타입도 정수를 입력받을 수 있습니다.

결과가 99.99가 나오는 값에 100이라는 정수 타입으로 값을 변경해 줄 시

```swift
var someDouble : Double = 99.99
someDouble = 100

print(someDouble)
```

#### 결과

![5번](https://KMG4531.github.io/assets/images/2021-03-23/e.png)

100.0으로 정수 타입도 받을 수 있다는 것을 알 수 있습니다.



***만약 Double 타입 값에 Float 타입의 값을 넣어주면 어떻게 될까요?***

```swift
// Float
var someFloat : Float = 9.99
someFloat = 10

// Double
var someDouble : Double = 99.99
someDouble = 100

someDouble = someFloat

print(someDouble)
```

####  결과

![5번](https://KMG4531.github.io/assets/images/2021-03-23/f.png)

[에러: 왜 Double 타입에 Float 타입 값을 넣었어!]라고 오류를 발생시키네요.



### Character

Character 타입은 문장처럼 문자의 집합이 아닌 단 ***하나***의 문자를 의미합니다. Character 타입은 유니코드를 사용할 수 있으므로 영어는 물론, 유니코드에서 지원하는 모든 언어 및 특수기호 등을 다 사용할 수 있습니다. 단, 문자를 표현하기 위해서는 값의 앞에 큰따옴표("")를 사용해 줘야 합니다. 결과 값을 출력해 주면

```swift
var someCharacter : Character = "A"
someCharacter = "가"
someCharacter = "🥭"

print(someCharacter)
```

#### 결과

![6번](https://KMG4531.github.io/assets/images/2021-03-23/g.png)

맨 마지막에 입력한 맛 좋은 망고 이모티콘이 나옵니다.



### String

String 타입은 Character 타입과 다르게 여러 문자의 값을 받을 수 있습니다.

변수이니 값을 바꿔줄 수도 있고, 연산자를 사용하여 문자열을 합쳐줄 수도 있습니다.

print(someString)를 이용해 값을 출력해 주면

```swift
var someString : String = "사랑합니다"
someString  = "여러분"

someString = someString + "사랑해용 >_+ ♥️"


print(someString)
```

#### 결과

![7번](https://KMG4531.github.io/assets/images/2021-03-23/h.png)



## Any,  nil

기본 데이터 타입은 아니지만 데이터 타입에 있는 편리한 기능을 알아보겠습니다.



### Any

Swift의 모든 데이터 타입을 사용할 수 있다는 뜻입니다. 

~~~swift
var someAny : Any = 100
someAny = 987.65
someAny = "다 가능합니다"
someAny = "😛"
~~~

print(someAny) 사용해 출력해주면

#### 결과

![8번](https://KMG4531.github.io/assets/images/2021-03-23/i.png)

귀여운 이모티콘이 출력됩니다.



### nil

nil은 '없음'을 나타내는 키워드입니다. 다른 언어에서는 'Null' 있죠.

Any의 반대로 생각하시면 됩니다.

여기서 문제 밑에 밑에 코드처럼 입력을 한 뒤 실행시키면 어떤 결과를 가져올까요??

```
someAny = "😛"
someAny = nul
```





#### 결과

Swift를 처음 공부하시는 분들은 귀여운 이모티콘으로 바뀔 수 있다고 생각하셨을 거예요.

왜냐하면 Any 타입은 모든 타입을 받기 때문이라고 생각하셨기 때문이에요.

![9번](https://KMG4531.github.io/assets/images/2021-03-23/j.png)

위에 결과를 보시면 에러가 뜹니다.

[에러: 'nil' cannot be assigned to type 'Any']

***nil은 특정 타입이 아니라 위에도 말씀드렸듯이 그냥 '없음'이기 때문에 데이터 타입이 아닌 nil은 Any 타입이 받을 수 없습니다.***



*Any, nil 말고 AnyObject라고 있습니다.*

*Any와 AnyObject는 가능하면 사용하지 않는 게 좋습니다.*

*위에도 말씀드렸듯이 Swift 언어의 데이터 타입은 매우 예민하기 때문에 Any, AnyObject로 선언된 변수의 값을 가져다 쓰면 예기치 못한 오류가 생길 수 있습니다. 쓰지 않는 걸 추천드립니다.*
