---
layout: post
title:  "열거형 - Enumerations"
date:   2018-02-27
author: Seo Jaehyeong
categories: Swift
tags:	enum
cover:
---

## 열거형(Enumerations)

* 그룹에 대한 연관된 값을 정의하고 사용가능한 타입
* 다른 언어와 달리 항목 그 자체가 고유의 값으로 해당 항목에 값을 매칭 시킬 필요가 없다.
* 원시값(rawValue)이라는 형태로 실제 값(정수, 실수, 문자 등)을 부여 할 수 있다.
* 열거형의 이니셜라이즈를 정의 할 수 있으며, 프로토콜 채택, 연산프로퍼티, 메소드 등을 만들 수 있다.


### 열거형 문법
```swift
enum <열거형 이름> {
  case <열거 항목1>
  case <열거 항목2>
  case <열거 항목3>
}

//example 1
enum CompassPoint {
    case north
    case south
    case east
    case west
}

//example 2
enum Planet {
    case mercury, venus, earth,mars, jupiter, saturn,uranus, neptune
}

//열거형 값 지정
var directionToHead = CompassPoint.west
directionToHead = .north
```
각 case의 값만 지정 할 수 있으며, 선언 후에도 dot syntax를 통해 값을 변경 할 수 있다.


### Switch 문과 함께 사용
```swift
directionToHead = .south
switch directionToHead {
case .north:
    print("Lots of planets have a north")
case .south:
    print("Watch out for penguins")
case .east:
    print("Where the sun rises")
case .west:
    print("Where the skies are blue")
}
// Prints "Watch out for penguins"


let somePlanet = Planet.earth
switch somePlanet {
case .earth:
    print("Mostly harmless")
default:
    print("Not a safe place for humans")
}
// Prints "Mostly harmless"

```
열거형의 모든 case가 제공될때는 default 값은 제공되지 않아도 되지만
모든 case가 제공되지 않는다면 default 값은 제공 되어야 한다.


### Associated Values
<img src="/assets/posts/barcode_UPC.png" title="Barcode UPC">
<img src="/assets/posts/barcode_QR.png" title="Barcode QR">




```swift
```
