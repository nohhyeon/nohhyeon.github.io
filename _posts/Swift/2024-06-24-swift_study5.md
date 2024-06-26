---
title: swift 함수-2
categories: study
tags: swift
---
swift 함수-2
## 매개변수 기본 값

매개변수에 기본적으로 전달될 값을 미리 지정할 수 있습니다

> 기본값을 갖는 매개변수는 매개변수 목록 중에 뒤쪽에 위치하는 것이 좋습니다

```
func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 = 매개변수 기본값 ...) -> 반환타입 {
    /* 함수 구현부 */
    return 반환값
}

func greeting(friend: String, me: String = "yagom") {
    print("Hello \(friend)! I'm \(me)")
}

// 매개변수 기본값을 가지는 매개변수는 호출시 생략할 수 있습니다
greeting(friend: "hana") // Hello hana! I'm su
greeting(friend: "john", me: "eric") // Hello john! I'm eric

```

## 전달인자 레이블

함수를 호출할 때 함수 사용자의 입장에서 매개변수의 역할을 좀 더 명확하게 표현하고자 할 때 사용합니다

```
func 함수이름(전달인자 레이블 매개변수1이름: 매개변수1타입, 전달인자 레이블 매개변수2이름: 매개변수2타입 ...) -> 반환타입 {
    /* 함수 구현부 */
    return
}

// 함수 내부에서 전달인자를 사용할 때에는 매개변수 이름을 사용합니다
func greeting(to friend: String, from me: String) {
    print("Hello \(friend)! I'm \(me)")
}

// 함수를 호출할 때에는 전달인자 레이블을 사용해야 합니다
greeting(to: "hana", from: "su") // Hello hana! I'm su
```

## 가변 매개변수

전달 받을 값의 개수를 알기 어려울 때 사용할 수 있습니다

> 스위프트 버전 5.4 미만에서는 함수당 하나의 가변 매개변수만 가질 수 있습니다(5.4 버전부터 여러개 가능)

```
func 함수이름(매개변수1이름: 매개변수1타입, 전달인자 레이블 매개변수2이름: 매개변수2타입...) -> 반환타입 {
    /* 함수 구현부 */
    return
}

func sayHelloToFriends(me: String, friends: String...) -> String {
    return "Hello \(friends)! I'm \(me)!"
}
print(sayHelloToFriends(me: "su", friends: "hana", "eric", "wing"))
// Hello ["hana", "eric", "wing"]! I'm yagom!

print(sayHelloToFriends(me: "su"))
// Hello []! I'm yagom!

```

> 위에 설명한 함수의 다양한 모양은 모두 섞어서 사용 가능합니다

## 데이터 타입으로서의 함수

스위프트는 함수형 프로그래밍 패러다임을 포함하는 다중 패러다임 언어이므로 스위프트의 함수는 일급객체입니다. 그래서 함수를 변수, 상수 등에 할당이 가능하고 매개변수를 통해 전달할 수도 있습니다

### 함수의 타입표현

반환타입을 생략할 수 없습니다.

```
 (매개변수1타입, 매개변수2타입 ...) -> 반환타입
```

### 함수타입 사용

```
var someFunction: (String, String) -> Void = greeting(to:from:)
someFunction("eric", "su") // Hello eric! I'm su

someFunction = greeting(friend:me:)
someFunction("eric", "yagom") // Hello eric! I'm su


// 타입이 다른 함수는 할당할 수 없습니다 - 컴파일 오류 발생
//someFunction = sayHelloToFriends(me: friends:)


func runAnother(function: (String, String) -> Void) {
    function("jenny", "mike")
}

// Hello jenny! I'm mike
runAnother(function: greeting(friend:me:))

// Hello jenny! I'm mike
runAnother(function: someFunction)
```

> 참고 : 스위프트의 전반적인 문법에서 띄어쓰기는 신경써야할 때가 많습니다