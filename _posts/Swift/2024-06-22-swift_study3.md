---
title: ios 데이터 타입
categories: study
tags: swift
---

ios 데이터 타입

## Bool

`true`와 `false`만을 값으로 가지는 타입

```
var someBool: Bool = true
someBool = false
// someBool = 0 // 컴파일 오류발생
// someBool = 1 // 컴파일 오류발생
```

## Int, UInt

### Int

정수 타입. 현재는 기본적으로 64비트 정수형.

```
var someInt: Int = -100
// someInt = 100.1 // 컴파일 오류발생
```

### UInt

양의 정수 타입. 현재는 기본적으로 64비트 양의 정수형.

```
var someUInt: UInt = 100
// someUInt = -100 // 컴파일 오류발생
// someUInt = someInt // 컴파일 오류발생
```

## Float, Double

### Float

실수 타입. 32비트 부동소수형.

```
var someFloat: Float = 3.14
someFloat = 3
```

### Double

실수타입. 64비트 부동소수형.

```
var someDouble: Double = 3.14
someDouble = 3
// someDouble = someFloat // 컴파일 오류발생
```

## Character, String

### Character

문자 타입. 유니코드 사용. 큰따옴표(“”) 사용.

```
var someCharacter: Character = "😀"
someCharacter = "👭"
someCharacter = "가"
someCharacter = "A"
// someCharacter = "하하하" // 컴파일 오류발생
print(someCharacter)
```

### String

문자열 타입. 유니코드 사용. 큰따옴표(“”) 사용.

```
var someString: String = "하하하 ? "
someString = someString + "웃으면 복이와요"
print(someString)

// someString = someCharacter // 컴파일 오류발생
```

여러줄 문자열은 큰따옴표 세 개 사용.

```
someString = """
여러줄 문자열을
사용할 수 있습니다.
첫 줄에 겹따옴표 세 개,
마지막 줄에 겹따옴표 세 개를
사용하면 됩니다.
"""

someString = """
겹따옴표 세 개인 줄(첫줄, 끝줄)에서
줄 바꿈을 하지 않으면 오류가 발생합니다.
"""

/*
someString = """오류발생
오류발생"""
*/
```

## Any

Swift의 모든 타입을 지칭하는 키워드

```swift
var someAny: Any = 100
someAny = "어떤 타입도 수용 가능합니다"
someAny = 123.12
```

> Any 타입에 Double 자료를 넣어두었더라도 Any는 Double 타입이 아니기 때문에 할당할 수 없습니다. 명시적으로 타입을 변환해 주어야 합니다. 타입 변환은 차후에 다룹니다

```swift
let someDouble: Double = someAny  // 컴파일 오류발생
```

## AnyObject

모든 클래스 타입을 지칭하는 프로토콜

> 클래스와 프로토콜에 대한 설명은 차후에 합니다

```swift
class SomeClass {}

var someAnyObject: AnyObject = SomeClass()
```

AnyObject는 클래스의 인스턴스만 수용 가능하기 때문에 클래스의 인스턴스가 아니면 할당할 수 없습니다.

```swift
someAnyObject = 123.12    // 컴파일 오류발생
```

## nil

없음을 의미하는 키워드

> 다른 언어의 `NULL`, `Null`, `null` 등과 유사한 표현입니다.

아래 코드에서 `someAny`는 `Any` 타입이고, `someAnyObject`는 `AnyObject` 타입이기 때문에 `nil`을 할당할 수 없습니다.  
`nil`을 다루는 방법은 **옵셔널** 파트에서 다룹니다.

```swift
someAny = nil         // 컴파일 오류발생
someAnyObject = nil   // 컴파일 오류발생
```

|타입|설명|
|:--|:--|
|Array|순서가 있는 리스트 컬렉션|
|Dictionary|`키`와 `값`의 쌍으로 이루어진 컬렉션|
|Set|순서가 없고, 멤버가 유일한 컬렉션|

## Array

Array는 멤버가 순서(인덱스)를 가진 리스트 형태의 컬렉션 타입입니다.

> Array 선언 및 생성  
> `Array는 여러 리터럴 문법을 활용할 수 있어서 표현 방법이 다양합니다`

![](https://yagomdotnet-bucket.s3.ap-northeast-2.amazonaws.com/wp-content/uploads/2020/02/09041039/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA-2021-08-09-%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB-4.09.29.png)

> Array 활용

```
integers.append(1)
integers.append(100)

// Int 타입이 아니므로 Array에 추가할 수 없습니다
//integers.append(101.1)

print(integers) // [1, 100]

// 멤버 포함 여부 확인
print(integers.contains(100)) // true
print(integers.contains(99)) // false

// 멤버 교체
integers[0] = 99

// 멤버 삭제
integers.remove(at: 0)
integers.removeLast()
integers.removeAll()

// 멤버 수 확인
print(integers.count)

// 인덱스를 벗어나 접근하려면 익셉션 런타임 오류발생
//integers[0]
```

> let을 사용하여 Array를 선언하면 불변 Array가 됩니다

```
let immutableArray = [1, 2, 3]

// 수정이 불가능한 Array이므로 멤버를 추가하거나 삭제할 수 없습니다
//immutableArray.append(4)
//immutableArray.removeAll()
```

## Dictionary

Dictionary는 `키`와 `값`의 쌍으로 이루어진 컬렉션 타입입니다.

> Dictionary의 선언과 생성  
> `Dictionary는 여러 리터럴 문법을 활용할 수 있어서 표현 방법이 다양합니다`

![](https://yagomdotnet-bucket.s3.ap-northeast-2.amazonaws.com/wp-content/uploads/2020/02/09041043/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA-2021-08-09-%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB-4.09.37.png)

> Dictionary 활용

```
// 키에 해당하는 값 할당
anyDictionary["someKey"] = "value"
anyDictionary["anotherKey"] = 100

print(anyDictionary) // ["someKey": "value", "anotherKey": 100]

// 키에 해당하는 값 변경
anyDictionary["someKey"] = "dictionary"
print(anyDictionary) // ["someKey": "dictionary", "anotherKey": 100]

// 키에 해당하는 값 제거
anyDictionary.removeValue(forKey: "anotherKey")
anyDictionary["someKey"] = nil
print(anyDictionary)
```

> let을 사용하여 Dictionary를 선언하면 불변 Dictionary가 됩니다

```
let emptyDictionary: [String: String] = [:]
let initalizedDictionary: [String: String] = ["name": "yagom", "gender": "male"]

// 불변 Dictionary이므로 값 변경 불가
//emptyDictionary["key"] = "value"
```

> 키에 해당하는 값을 다른 변수나 상수에 할당하고자 할 때는 옵셔널과 타입 캐스팅 파트에서 다룹니다

```
// "name"이라는 키에 해당하는 값이 없을 수 있으므로 
// String 타입의 값이 나올 것이라는 보장이 없습니다.
// 컴파일 오류가 발생합니다
let someValue: String = initalizedDictionary["name"]
```

## Set

Set는 순서가 없고, 멤버가 유일한 것을 보장하는 컬렉션 타입입니다.

> Set의 선언과 생성

![](https://yagomdotnet-bucket.s3.ap-northeast-2.amazonaws.com/wp-content/uploads/2020/02/09041049/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA-2021-08-09-%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB-4.09.45.png)

> Set는 집합연산에 많이 활용됩니다

![](https://yagomdotnet-bucket.s3.ap-northeast-2.amazonaws.com/wp-content/uploads/2020/02/09041057/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA-2021-08-09-%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB-4.09.59.png)