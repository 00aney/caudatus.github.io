---
layout: post
title:  "Type Casting"
date:   2018-03-31
author: Seo Jaehyeong
categories: Swift
tags:	Type Downcasting Any AnyObject
cover:
---

# Type Casting
Type Casting은 인스턴스의 타입을 확인하거나, 해당 인스턴스를 동일 클래스 계층 구조의 다른 수퍼클래스나 서브클래스로 처리하는 방법이다.

Swift의 형 변환은 **is**와 **as**연산자로 구현되며 이 두 연산자는 value의 타입을 확인하거나 다른 타입으로 변환하는 간단하고 표현적인 방법을 제공하며 또한 해당 타입이 프로토콜을 채택하는지도 확인 할 수 있다.

```swift
class MediaItem {
  var name: String
  init(name: String) {
    self.name = name
  }
}


class Movie: MediaItem {
  var director: String
  init(name: String, director: String) {
    self.director = director
    super.init(name: name)
  }
}

class Song: MediaItem {
  var artist: String
  init(name: String, artist: String) {
    self.artist = artist
    super.init(name: name)
  }
}


let library = [
    Movie(name: "Casablanca", director: "Michael Curtiz"),
    Song(name: "Blue Suede Shoes", artist: "Elvis Presley"),
    Movie(name: "Citizen Kane", director: "Orson Welles"),
    Song(name: "The One And Only", artist: "Chesney Hawkes"),
    Song(name: "Never Gonna Give You Up", artist: "Rick Astley")
]
// the type of "library" is inferred to be [MediaItem]
```

<br/>

## Checking Type

**is** 연산자를 사용하여 인스턴스가 특정 서브클래스 타입인지 체크할수 있다.

```swift
var movieCount = 0
var songCount = 0

for item in library {
  if item is Movie {
    movieCount += 1
  } else if item is Song {
    songCount += 1
  }
}

print("Media library contains \(movieCount) movies and \(songCount) songs")
// Prints "Media library contains 2 movies and 3 songs"
```

<br/>

## Downcasting
특정 클래스의 상수 또는 변수는 하위 클래스의 인스턴스를 참조(값으로 저장) 할 수 있다. 이 경우에는 **as** 연산자를 사용하여 서브 클래스 타입으로 다운캐스팅을 할 수 있고 다운캐스팅이 실패할 수 있기때문에 **as**연산자는 두가지 형태로 사용한다.
* as?(conditional form) - 실패시 다운캐스팅 하려는 타입의 옵셔널 값(nil)을 반환한다.
* as!(forced form) - 강제 다운캐스팅을 시도하며 항상 성공할 것이라는 확신이 있을때만 사용한다. 잘못된 클래스 유형으로 다운캐스팅을 시도하거나 실패시 런타입 에러를 발생시킨다.

```swift
for item in library {
  if let movie = item as? Movie {
    print("Movie: \(movie.name), dir. \(movie.director)")
  } else if let song = item as? Song {
    print("Song: \(song.name), by \(song.artist)")
  }
}

// Movie: Casablanca, dir. Michael Curtiz
// Song: Blue Suede Shoes, by Elvis Presley
// Movie: Citizen Kane, dir. Orson Welles
// Song: The One And Only, by Chesney Hawkes
// Song: Never Gonna Give You Up, by Rick Astley
```

<br/>

## Type Casting for Any and AnyObject
Swift는 두가지 특별한 타입을 제공한다.
- Any : 함수타입을 포함하여 모든 타입의 인스턴스를 나타낼 수 있다.
- AnyObject : 모든 클래스 타입의 인스턴스를 나타낼 수 있다.

```swift
var things = [Any]()

things.append(0)
things.append(0.0)
things.append(42)
things.append(3.14159)
things.append("hello")
things.append((3.0, 5.0))
things.append(Movie(name: "Ghostbusters", director: "Ivan Reitman"))
things.append({ (name: String) -> String in "Hello, \(name)" })

for thing in things {
    switch thing {
    case 0 as Int:
        print("zero as an Int")
    case 0 as Double:
        print("zero as a Double")
    case let someInt as Int:
        print("an integer value of \(someInt)")
    case let someDouble as Double where someDouble > 0:
        print("a positive double value of \(someDouble)")
    case is Double:
        print("some other double value that I don't want to print")
    case let someString as String:
        print("a string value of \"\(someString)\"")
    case let (x, y) as (Double, Double):
        print("an (x, y) point at \(x), \(y)")
    case let movie as Movie:
        print("a movie called \(movie.name), dir. \(movie.director)")
    case let stringConverter as (String) -> String:
        print(stringConverter("Michael"))
    default:
        print("something else")
    }
}

// zero as an Int
// zero as a Double
// an integer value of 42
// a positive double value of 3.14159
// a string value of "hello"
// an (x, y) point at 3.0, 5.0
// a movie called Ghostbusters, dir. Ivan Reitman
// Hello, Michael
```

<br/>

## Note
Swift는 Any 타입이 예상외는 값이 옵셔널로 선언되면 warning을 표시한다. 만약 옵셔널 값을 Any 값으로 사용해야 한다면 **as**연산자를 사용하여 명시적으로 Any타입으로 선언해주어야 한다.

```swift
let optionalNumber: Int? = 3
things.append(optionalNumber)        // Warning
things.append(optionalNumber as Any) // No warning
```
