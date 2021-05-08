## 튜플

튜플은 타입의 이름이 따로 지정되어 있지 않은, 프로그래머 마음대로 만드는 타입입니다.

일정 타입의 나열만으로 튜플 타입을 생성해 줄 수 있습니다.

------

#### 튜플의 기본

~~~swift

// String, Int, Double, Double
var person: (String, Int, Double, Double) = ("Mingu", 21, 197.6, 63.2)

// index를 통해서 값을 빼 올 수 있습니다.
print("이름: \(person.0), 나이: \(person.1), 키: \(person.2), 몸무게: \(person.3)")

person.2 = 169.9
person.3 = 58.1

print("이름: \(person.0), 나이: \(person.1), 키: \(person.2), 몸무게: \(person.3)")
~~~

#### 결과

![1](https://KMG4531.github.io/assets/images/2021-03-25/a.png)

튜플의 각 요소를 이름 대신 숫자로 표현하기 때문에 간편해 보일 수 있지만,

차후에 다른 프로그래머가 코드를 본다면 각 요소가 어떤 게 있고 어떤 의미가 있는지 유추하기 어렵습니다. 
그래서 튜플의 요소마다 이름을 붙일 수도 있습니다.

------

#### 튜플 요소 이름 지정

~~~swift
// String, Int, Double, Double
var person: (name: String, age: Int, height: Double, weight: Double) = ("Mingu", 21, 197.6, 63.2)

// 요소의 이름을 통해서 값을 빼 올 수 있습니다.
print("이름: \(person.name), 나이: \(person.age), 키: \(person.height), 몸무게: \(person.weight)")

person.age = 34
person.3 = 100

// 기존처럼 인덱스를 이용하여 값을 빼 올 수도 있습니다.
print("이름: \(person.0), 나이: \(person.1), 키: \(person.2), 몸무게: \(person.3)")
~~~

#### 결과

![2](https://KMG4531.github.io/assets/images/2021-03-25/b.png)

이름을 지정했을 때 불편함이라고 한다면 선언해 줄 때마다 긴 튜플 타입을 모두 써야 하는 게 불편함이라고 말할 수 있겠네요.

이럴 때 타입에 별칭을 사용하여 더 깔끔하게 코드를 작성할 수 있습니다.

------

#### 튜플 별칭 지정

~~~swift
typealias PersonTuple = (name: String, age: Int, height: Double, weight: Double)

let mingu : PersonTuple = ("Mingu", 21, 189.2, 59)
let ben : PersonTuple = ("Ben", 17, 153, 43)

print("이름: \(mingu.name), 나이: \(mingu.age), 키: \(mingu.height), 몸무게: \(mingu.weight)")
print("이름: \(ben.name), 나이: \(ben.age), 키: \(ben.height), 몸무게: \(ben.weight)")
~~~

#### 결과

![3](https://KMG4531.github.io/assets/images/2021-03-25/c.png)
