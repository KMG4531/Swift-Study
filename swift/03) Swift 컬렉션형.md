Swift는 많은 수의 데이터를 묶어서 저장하고 관리할 수 있는 컬렉션 타입이 있습니다.

오늘 저희가 살펴볼 컬렉션 타입에는 Array, Dictionary, Set 등이 있습니다.

## Array

배열이라고도 부르죠. 배열은 같은 타입의 데이터를 일렬로 나열한 후 순서대로 저장하는 형태의 컬렉션 타입입니다.

##### 먼저 빈 Int 타입의 Array를 생성해 주겠습니다.

~~~swift
var integers: Array<Int> = Array<Int>() 
~~~

안에 값이 아무것도 없는 integers라는 빈 Int 타입 Array를 만들어 주었습니다.

그렇다면 빈 Array 안에 값을 넣어줄 수 있는 메서드를 알아야겠죠!

값을 넣어주는 메서드인 append()와 insert(_, at:)가 있습니다.
***append()***는 맨 뒤에 값을 추가하는 메서드이고, ***insert(_, at:)***는 중간에 값을 추가해주고 싶을 때 사용하는 메서드 입니다.
insert(_, at:)는 _ = 이름 at: = 값이 들어갈 순서를 나타냅니다.

값을 추가해 주는 코드를 작성해보겠습니다.

~~~swift
integers.append(1)
integers.append(100)

integers.insert(90, at: 1)
~~~

#### 결과

![1번](https://KMG4531.github.io/assets/images/2021-03-24/a.png)

아무것도 없는 빈 값에 append를 사용하여 1과 100이 들어간 것을 알 수 있습니다.
그 이후 insert를 이용해 90이라는 값이 at: 1의 자리에 들어간 것을 알 수 있죠.

------

자 여기서 질문 ***"민구 님 insert를 이용해 90이라는 값이 at: 1의 자리에 들어갔는데 결과에는 [1, 90, 100]이런 식으로 나왔는데 at: 1이 첫 번째 자리를 뜻하니까 가장 앞에 들어가야 하는 거 아닌가요?"*** 

***배열은 1이 아닌 0부터 시작됩니다. 그러므로 첫 번째 자리에 90을 넣고 싶으면 insert(90, at: 0)이라고 코드를 입력해 줘야 합니다.***

------


배열 안에 값이 존재하는지 없는지를 확인하는 메서드도 있습니다. 그것은 바로 contains()라는 메서드입니다.
contains() 메서드의 괄호 안에 확인하고 싶으신 값을 넣으면 있으면 True 없으면 False로 표시해 줍니다.

~~~swift
integers.contains(100)
integers.contains(99)
~~~

#### 결과

![2](https://KMG4531.github.io/assets/images/2021-03-24/b.png)

배열 안에 100이라는 값이 있으니 true, 99는 없으니 false를 나타내는 것을 알 수 있습니다.


이뿐만 아니라 배열 안에 있는 값을 지울 수 있는 메서드도 있습니다.
remove(), remove(at:), removeFirst(), removeLast(), removeAll()이라는 메서드도 있습니다.
* remove()는 괄호 안에 값을 넣어주면 배열 안에 있는 값이 지워줍니다.
* remove(at:)은 괄호의 순서를 입력해 주면 그 순서의 있는 값이 지워줍니다.
* removeFirst()는 0번째에 있는 값을 지워줍니다.
* removeLast()는 마지막 순서에 있는 값을 지워줍니다.
* removeAll()은 배열 안에 있는 모든 값을 지워줍니다.

사용법

~~~swift
integers.remove(1)	// 배열 안에 있는 1을 지워줍니다.
integers.remove(at:1)	// 배열의 0 다음 안에 있는 1에 있는 값을 지워줍니다.
integers.removeFirst()	// 배열의 0 번째 값을 지워줍니다.
integers.removeLast()	// 배열의 마지막 순서에 있는 값을 지워줍니다.
integers.removeAll()	// 배열 안에 있는 모든 값을 지워줍니다.
~~~

배열 안에 몇 개의 값이 들어있는지 알 수 있는 메서드도 있죠! 그것은 바로 count입니다.
사용법

~~~swift
// 배열 안에 [1, 90, 100]이 있다고 가정하고 count를 써주면
integers.count
~~~

#### 결과

![3](https://KMG4531.github.io/assets/images/2021-03-24/c.png)
배열 안에 값이 3개가 있는 걸 알 수 있습니다.


배열의 타입을 정확히 명시해 줬다면 ()만으로도 빈 배열을 생성할 수 있습니다.
~~~swift
// Double 타입으로 생성
var double: Array<Double> = [Double]()

// String 타입으로 생성
var string: [String] = [String]()
~~~

Array<[Double]>와 [Double]는 동일한 표현이기 때문에 둘 중 아무거나 써도 됩니다.
String 타입으로 생성한 것도 동일한 표현이기 때문에 상관없습니다.
저 뿐만 아니라 한 가지 더 축약할 수 있는 방법이 있습니다.

~~~swift
// Character Array 생성
var characters: [Character] = []
~~~

이번에는 ()가 아닌 []를 써줘서 최대한 축약하여 Array를 생성할 수 있습니다.
------

변수가 아닌 상수를 써서 나타내 줄 수 있습니다.
상수를 나타낼 때는 값을 정하여 나타내줘야 합니다.

~~~swift
let immutableArray = [1, 2, 3]
~~~

상수로 입력할 시 당연히 값을 변경할 수 없겠죠!


## Dictionary

Dictionary는 값의 순서 없이 키와 값의 쌍으로 구성되는 컬렉션 타입입니다.
Dictionary에 저장되는 값은 항상 키와 쌍을 이루게 되는데, Dictionary 안에는 키가 하나이거나 여러 개일 수 있습니다.
단, 하나의 Dictionary 안의 키는 같은 이름을 중복해서 사용할 수 없습니다.
~~~swift
// Key가 String 타입이고 Value가 Any인 빈 Dictionary 생성
var anyDictionary: Dictionary<String, Any> = [String: Any]()

anyDictionary["someKey"] = "value"      // "someKey" : "value" 입력
anyDictionary["anotherKey"] = 100       // "anotherKey" : 100  입력

anyDictionary
~~~

#### 결과

![4](https://KMG4531.github.io/assets/images/2021-03-24/d.png)
anyDictionary 안에 ["someKey": "value", "anotherKey": "100"] 잘 입력된 것을 보실 수 있습니다.
Dictionary도 값 변경이 가능합니다.

~~~swift
anyDictionary["anotherKey"] = "dictionary"      // 값 변경 가능
anyDictionary
~~~

#### 결과
![5](https://KMG4531.github.io/assets/images/2021-03-24/e.png)
anyDictionary를 보면 100이 dictionary로 바뀐 걸 알 수 있습니다.


Dictionary의 Key에 해당되는 값을 없애고 싶을 때 쓰는 removeValue(forKey: ) 메서드가 있습니다.

사용법

~~~swift
anyDictionary.removeValue(forKey: "anotherKey")
anyDictionary
~~~

anyDictionary 안에 있는 anotherKey를 삭제했으니 출력해보면 ["someKey": "value"]만 있겠죠.
#### 결과

![6](https://KMG4531.github.io/assets/images/2021-03-24/f.png)
------

## Set

Set는 같은 타입의 데이터를 순서 없이 하나의 묶음으로 저장하는 형태의 컬렉션 타입입니다.
Set 내의 값은 모두 유일한 값, 즉 중복된 값이 존재하지 않습니다. 그래서 보통 ***순서가 중요하지 않거나 각 요소가 유일한 값***이어야 하는 경우에 사용합니다. 
Set는 ***해시 가능한 값***이 들어와야 합니다.
Set은 배열과 달리 줄여서 표현할 수 있는 축약형이 없습니다.

Set 생성 방법

~~~swift
var integerSet: Set<Int> = Set<Int>()
~~~

생성 방법은 같지만 다만 축약형이 없는 거죠.
Set는 집합 연산처럼 사용이 가능합니다.
예를 들어 setA, setB의 합집합, 교집합, 차집합의 코드를 짜보겠습니다.
~~~swift
let setA: Set<Int> = [0, 1, 2, 3, 4, 5]
let setB: Set<Int> = [3, 4, 5, 6, 7, 8]

let union: Set<Int> = setA.union(setB)      // union이라는 메서드를 사용하면 합집합 하지만 자동으로 정렬이 안됨

let sortUnion: [Int] = union.sorted()       // sorted()라는 메서드를 사용하면 같은 타입의 배열로 정렬이 됨

let intersection: Set<Int> = setA.intersection(setB)        // intersection은 교집합

let subtracting: Set<Int> = setA.subtracting(setB)          // subtracting는 차집합
~~~

차례대로 출력을 해보겠습니다.

#### 결과

![7](https://KMG4531.github.io/assets/images/2021-03-24/g.png)
합집합부터 차집합까지 나온 것을 알 수 있습니다.





