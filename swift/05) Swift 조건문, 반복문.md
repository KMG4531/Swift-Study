## 조건문

Swift의 조건문에서는 if, else 구문과 switch, case  구문이 있습니다.
Swift의 조건문 사용시 장점은 다른 언어들과 달리 조건문을 사용 했을 시 ()가 필수였지만, 
Swift에서는 ()를 사용하지 않아도 된다는게 큰 장점입니다.



## if 구문

다른 언어에서 사용하였던 if 문과 비슷하기 때문에 쉽게 이해하실 수 있습니다.
다만, Swift의 if 구문은 조건 값이 꼭 Bool 타입이여야 합니다.

##### if의 기본

~~~swift
if condition {
    code 
} else if condition {
    statements
} else {
    statements
}
~~~

if 구문은 다른 언어랑 다를게 없다는 걸 확연시 아실 수 있습니다.
if 구문으로 만든 예제를 한번 보시죠.
#### ex) 민구의 몸무게가 60kg 미만이면 저체중, 70kg 초과이면 비만, 61kg 에서 69kg 사이이면 정상입니다. 민구의 몸무게는 65kg 입니다.
##### (if 구문으로 코드를 작성하시오)

~~~swift
let weight = 65					// 민구의 몸무게

if weight < 60 {				// 60kg 미만
  print("저체중 입니다.")
} else if weight > 70{	// 70kg 초과
  print("비만 입니다.")
} else {							
	print("정상 입니다.")
}
~~~

if 구문은 예제에서 나온 말들을 그대로 작성하면 되기 때문에 아주 쉽습니다.


## switch 구문

switch 구문은 다른 앞에 if 구문과 마찬가지로 ()를 생략할 수 있습니다.
switch 구문은 다른 언어와 다른 한 가지가 있습니다.
그것은 바로 break 키워드는 선택 사항이라는 것 입니다.
그 말은 즉, case 내부의 코드를 모두 실행하면 break 없이도 switch 구문이 종료된다는 뜻이겠죠.

##### switch 기본

~~~swift
switch value {
case pattern:
		code
default:
  	code
}
~~~

break 와 () 를 써도 안써도 switch 문을 실행시킬 수 있습니다.
Swift 언어를 사용하는 저희에게는 사소하면서도 큰 것이니 이러한 장점은 사용하는게 당연히 좋겠죠😝 



Swift에서는 switch 에서 범위 연산자를 사용할 수 있습니다.
범위 연산자를 활용하면 더욱 쉽고 유용합니다.

##### 범위 연산자의 활용 예시 

~~~swift
let num = 21

switch num {
case 0 :
    print("0")
case 1..<10 : 
    print("1 ~ 9")
case 20 :
    print("20")
case 21...Int.max :
    print("over 20")
default:
    print("unknown")
}
~~~

위 예시에 저희가 처음보는게 있습니다.
..< , ... 이라는 표현이데요. 이것을 범위 연산자 입니다.
코드를 보시면 case 1..<10 : 이런식으로 나와있습니다.
이것을 의미하는 것은 1이상 10 미만이라는 표현 의미합니다.

저 뿐만 아니라 case 21...Int.max : 가 있죠
여기서의 범위 연산자는 ... 입니다.
... 이 의미하는 것은 21 이상 Int.max 이하 이죠.
하지만 여기서 Int.max 라고 잡아줬기 때문에 무한 정수의 이하라고 생각하시면 됩니다.

또 하나의 특징으로 Swift의 switch 구문의 조건에 정수 타입 외의 대부분의 기본 타입을 사용할 수 있습니다.
다만, 각 case에 들어갈 비교 값은 입력 값과 데이터 타입이 같아야 합니다.
또, 명확히 case에 명시되지 않은 한 default를 꼭 작성해줘야 합니다.

##### 예시

~~~swift
switch "mango" {
case "watermelon":
    print("watermelon")
case "apple":
    print("apple")
case "melon":
    print("melon")
case "plum":
    print("plum")
default:                    
    print("unknown")
}	// mango
~~~

만약 watermelon과 apple를 하나의 케이스 안에 넣고 싶으면
, 로 연결하여 사용할 수 있습니다.

~~~swift
case "watermelon", "apple" :
~~~

이 방법말고도 하나의 방법이 더 있습니다.
fallthrough 키워드를 사용하는 방법입니다.

##### 예시

~~~swift
case "watermelon":
    print("watermelon")
    fallthrough
case "apple":
    print("apple")
~~~

두 개의 방법들 중 여러분들에게 맞는 방법을 찾으셔서 쓰시면 됩니당. 😊 



## 반복문

반복문은 앞에서 포스팅 했던 내용인 컬렉션 타입과 많이 사용이 됩니다.
반복문에는 for-in, while, repeat-while 구문이 있습니다.



## for-in

for-in 반복 구문은 반복적인 데이터를 다룰 때 많이 사용됩니다.

##### for-in

~~~swift
for item in items { 		// item = 임시상수(아이템 이름), items = 컬렉션 타입
		code
}
~~~

이런 식으로 보면 도저히 무슨 말인지 이해를 못 합니다. 저라두 이해 못해요.
그러니 간단한 예를 통해서 알아봅시다.

~~~swift
var integers = [1, 2, 3]				// Array
let people_info = ["mingu":21, "ben":10, "mark":17]	// Dictionary

for integer in integers {			// 안에 있는 구문을 반복적으로 실행
  	print(integer)
}

// Dictionar의 item은 Key와 Value로 구성된 튜플 타입입니다.
// 튜플 타입의 방식의 for-in 반복문
for (name, age) in people {
  print("\(name): \(age)")			// name = Key, age = value
}
~~~

#### 결과

![](https://images.velog.io/images/jkang4531/post/0b40d9ac-2dcb-48fc-9915-1c023a85fd97/a.png)

코드를 짠대로 나오는 것을 보실 수 있습니다.



## while

Swift의 while 반복 구문도 다른 프로그래밍 언어의 while 구문과 크게 다르지 않습니다.
while 구문도 ()를 쓰고 안쓰고의 차이는 취향 차이 입니다.
whie 문은 조건이 참이면 계속 실행하는 반복문 입니다.

##### while

~~~swift
while condition {
	code
}
~~~

아래 예시를 보시죠

#### 예시

~~~swift
var integers = [1, 2, 3]			// Array

while integers.count > 1 {
		integers.removeLast()
}
~~~

딱 이 예시만 보고 여러분들이 값을 맞춰보세요!

여러분들은 예시를 보고 값이 딱 이거다 하시는 분들이 있으신 분들이 있을 겁니다.



#### 결과

![](https://images.velog.io/images/jkang4531/post/00140722-c29f-4ec5-a575-f61326132530/b.png)

결과 값은 1입니다.
count가 1이 될 때 까지 integers. removeLast() 실행되기 때문에 1이라는 결과 값이 나오겠죵



## repeat-while

repeat-while 반복 구문은 다른 언어의 do-while 크게 다르지 않습니다.
그냥 do가 repeat으로 바뀐거 뿐입니다.
repeat 블록의 코드를 최초 1회 실행한 후, while 다음 조건이 True이면 블록 내부의 코드를 반복합니다.

##### repeat-while

~~~swift
repeat {
	Code				// 수행할 명령어
} while condition			// 반복 조건
~~~



예시를 보시죵~!

#### 예시

~~~swift
var integers = [1, 2, 3]	// Array

repeat {
    print("integers \(integers.removeFirst())")
} while integers.count > 0
~~~

#### 결과

![](https://images.velog.io/images/jkang4531/post/16406f15-1fb4-47f7-bb11-297cdd75aba2/c.png)

count가 0 이 될 때까지 integers.removeFirst()로 맨 앞에 있는 값을 빼주고 print로 출력했습니다.
