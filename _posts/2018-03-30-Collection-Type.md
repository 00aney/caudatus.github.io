---
layout: post
title:  "Collection Type"
date:   2018-03-30
author: Seo Jaehyeong
categories: Swift
tags:	array set dictionary
cover:
---

# Collection Type

Swift는 값의 모음을 저장하기 위한 Array, Set, Dictionary 라는 세가지 기본 형식을 제공합니다.
<img src="/assets/posts/CollectionTypes.png" title="Collection_Types" width="500px">

## Array
배열은 인덱스와 대응하는 데이터들로 이루어진 자료 구조를 나타낸다. 일반적으로 배열에는 같은 종류의 데이터들이 순차적으로 저장되며, 인덱스가 곧 배열의 시작점으로부터 값이 저장되어 있는 상대적인 위치가 된다.

* 기본 표현은 Array<Element>로 Array Type을 나타낸다.
* 여기에서 Element는 배열에 저장할 수 있는 타입이다.
* 또 다른 축약 문법으로 [Element]로 표현 할 수 있다.

```swift
//Creating an Empty Array

var someInts = [Int]()
print("someInts is of type [Int] with \(someInts.count) items.")
// Prints "someInts is of type [Int] with 0 items."

someInts.append(3)
// someInts now contains 1 value of type Int

someInts = []
// someInts is now an empty array, but is still of type [Int]



//Creating an Array with a Default Value
var threeDoubles = Array(repeating: 0.0, count: 3)
// threeDoubles is of type [Double], and equals [0.0, 0.0, 0.0]

var anotherThreeDoubles = Array(repeating: 2.5, count: 3)
// anotherThreeDoubles is of type [Double], and equals [2.5, 2.5, 2.5]

var sixDoubles = threeDoubles + anotherThreeDoubles
// sixDoubles is inferred as [Double], and equals [0.0, 0.0, 0.0, 2.5, 2.5, 2.5]



//Creating an Array with an Array Literal
var shoppingList: [String] = ["Eggs", "Milk"]
var shoppingList = ["Eggs", "Milk"]
// shoppingList has been initialized with two initial items



//Accessing and Modifying an Array
print("The shopping list contains \(shoppingList.count) items.")
// Prints "The shopping list contains 2 items."

if shoppingList.isEmpty {
    print("The shopping list is empty.")
} else {
    print("The shopping list is not empty.")
}
// Prints "The shopping list is not empty."

shoppingList.append("Flour")
// shoppingList now contains 3 items, and someone is making pancakes

shoppingList += ["Baking Powder"]
// shoppingList now contains 4 items
shoppingList += ["Chocolate Spread", "Cheese", "Butter"]
// shoppingList now contains 7 items

var firstItem = shoppingList[0]
// firstItem is equal to "Eggs"

shoppingList[4...6] = ["Bananas", "Apples"]
// shoppingList now contains 6 items

shoppingList.insert("Maple Syrup", at: 0)
// shoppingList now contains 7 items
// "Maple Syrup" is now the first item in the

let mapleSyrup = shoppingList.remove(at: 0)
// the item that was at index 0 has just been removed
// shoppingList now contains 6 items, and no Maple Syrup
// the mapleSyrup constant is now equal to the removed "Maple Syrup" string

let apples = shoppingList.removeLast()
// the last item in the array has just been removed
// shoppingList now contains 5 items, and no apples
// the apples constant is now equal to the removed "Apples" string



//Iterating Over an Array
for item in shoppingList {
    print(item)
}
// Six eggs
// Milk
// Flour
// Baking Powder
// Bananas

for (index, value) in shoppingList.enumerated() {
    print("Item \(index + 1): \(value)")
}
// Item 1: Six eggs
// Item 2: Milk
// Item 3: Flour
// Item 4: Baking Powder
// Item 5: Bananas
```

<br/>

## Sets
Set은 같은 타입의 데이터가 순서없이 모여있는 자료구조로, 각 항목의 순서가 중요하지 않거나 한번만 표시해야 하는 경우 사용한다.

* 기본 표현은 Set<Element>로 Set Type을 나타낸다.
* 여기에서 Element는 배열에 저장할 수 있는 타입이다.
* Set은 Array와 다르게 축약 문법이 없다.

```swift
var someInts:Set<Int> = Set<Int>()

//Creating and Initializing an Empty Set
var letters = Set<Character>()
print("letters is of type Set<Character> with \(letters.count) items.")
// Prints "letters is of type Set<Character> with 0 items."

letters.insert("a")
// letters now contains 1 value of type Character
letters = []
// letters is now an empty set, but is still of type Set<Character>



//Creating a Set with an Array Literal
var favoriteGenres: Set<String> = ["Rock", "Classical", "Hip hop"]
// favoriteGenres has been initialized with three initial items

var favoriteGenres: Set = ["Rock", "Classical", "Hip hop"]



//Accessing and Modifying a Set
print("I have \(favoriteGenres.count) favorite music genres.")
// Prints "I have 3 favorite music genres."

if favoriteGenres.isEmpty {
    print("As far as music goes, I'm not picky.")
} else {
    print("I have particular music preferences.")
}
// Prints "I have particular music preferences."

favoriteGenres.insert("Jazz")
// favoriteGenres now contains 4 items

if let removedGenre = favoriteGenres.remove("Rock") {
    print("\(removedGenre)? I'm over it.")
} else {
    print("I never much cared for that.")
}
// Prints "Rock? I'm over it."

if favoriteGenres.contains("Funk") {
    print("I get up on the good foot.")
} else {
    print("It's too funky in here.")
}
// Prints "It's too funky in here."



//Iterating Over a Set
for genre in favoriteGenres {
    print("\(genre)")
}
// Jazz
// Hip hop
// Classical

for genre in favoriteGenres.sorted() {
    print("\(genre)")
}
// Classical
// Hip hop
// Jazz

```

### Fundamental Set Operations
<img src="/assets/posts/setVennDiagram.png" title="Set_Diagram" width="500px">

* Use the intersection(_:) method to create a new set with only the values common to both sets.
* Use the symmetricDifference(_:) method to create a new set with values in either set, but not both.
* Use the union(_:) method to create a new set with all of the values in both sets.
* Use the subtracting(_:) method to create a new set with values not in the specified set.

```swift
let oddDigits: Set = [1, 3, 5, 7, 9]
let evenDigits: Set = [0, 2, 4, 6, 8]
let singleDigitPrimeNumbers: Set = [2, 3, 5, 7]

oddDigits.union(evenDigits).sorted()
// [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
oddDigits.intersection(evenDigits).sorted()
// []
oddDigits.subtracting(singleDigitPrimeNumbers).sorted()
// [1, 9]
oddDigits.symmetricDifference(singleDigitPrimeNumbers).sorted()
// [1, 2, 9]
```

### Set Membership and Equality

<img src="/assets/posts/setEulerDiagram.png" title="setEulerDiagram" width="500px">

* Use the “is equal” operator (==) to determine whether two sets contain all of the same values.
* Use the isSubset(of:) method to determine whether all of the values of a set are contained in the specified set.
* Use the isSuperset(of:) method to determine whether a set contains all of the values in a specified set.
* Use the isStrictSubset(of:) or isStrictSuperset(of:) methods to determine whether a set is a subset or superset, but not equal to, a specified set.
* Use the isDisjoint(with:) method to determine whether two sets have no values in common.

```swift
let houseAnimals: Set = ["🐶", "🐱"]
let farmAnimals: Set = ["🐮", "🐔", "🐑", "🐶", "🐱"]
let cityAnimals: Set = ["🐦", "🐭"]

houseAnimals.isSubset(of: farmAnimals)
// true
farmAnimals.isSuperset(of: houseAnimals)
// true
farmAnimals.isDisjoint(with: cityAnimals)
// true
```

<br/>

## Dictionaries
딕셔너리는 순서가 정해져 있지 않은 데이터에 키값을 통해 구분할 수 있는 자료구조이다.
항목의 순서가 중요치 않고 키값을 통해서 데이터에 접근할 수 있다.

* 기본 표현은 Dictionary<key, value>로 Dictionary Type을 나타낸다.
* Key값은 Dictionary에서 value를 가져오는데 사용되는 값이다.
* 또 다른 축약 문법으로 [key: value]로 표현할 수 있다.

```swift
var someInts:[String:Int] = [String:Int]()
var someInts:Dictionary<String,Int> = [:]

//Creating an Empty Dictionary
var namesOfIntegers = [Int: String]()
// namesOfIntegers is an empty [Int: String] dictionary

namesOfIntegers[16] = "sixteen"
// namesOfIntegers now contains 1 key-value pair
namesOfIntegers = [:]
// namesOfIntegers is once again an empty dictionary of type [Int: String]



//Creating a Dictionary with a Dictionary Literal
var airports: [String: String] = ["YYZ": "Toronto Pearson", "DUB": "Dublin"]
var airports = ["YYZ": "Toronto Pearson", "DUB": "Dublin"]



//Accessing and Modifying a Dictionary
print("The airports dictionary contains \(airports.count) items.")
// Prints "The airports dictionary contains 2 items."

if airports.isEmpty {
    print("The airports dictionary is empty.")
} else {
    print("The airports dictionary is not empty.")
}
// Prints "The airports dictionary is not empty."

airports["LHR"] = "London"
// the airports dictionary now contains 3 items

airports["LHR"] = "London Heathrow"
// the value for "LHR" has been changed to "London Heathrow"

if let oldValue = airports.updateValue("Dublin Airport", forKey: "DUB") {
    print("The old value for DUB was \(oldValue).")
}
// Prints "The old value for DUB was Dublin."

if let airportName = airports["DUB"] {
    print("The name of the airport is \(airportName).")
} else {
    print("That airport is not in the airports dictionary.")
}
// Prints "The name of the airport is Dublin Airport."

airports["APL"] = "Apple International"
// "Apple International" is not the real airport for APL, so delete it
airports["APL"] = nil
// APL has now been removed from the dictionary

if let removedValue = airports.removeValue(forKey: "DUB") {
    print("The removed airport's name is \(removedValue).")
} else {
    print("The airports dictionary does not contain a value for DUB.")
}
// Prints "The removed airport's name is Dublin Airport."



//Iterating Over a Dictionary
for (airportCode, airportName) in airports {
    print("\(airportCode): \(airportName)")
}
// YYZ: Toronto Pearson
// LHR: London Heathrow

for airportCode in airports.keys {
    print("Airport code: \(airportCode)")
}
// Airport code: YYZ
// Airport code: LHR

for airportName in airports.values {
    print("Airport name: \(airportName)")
}
// Airport name: Toronto Pearson
// Airport name: London Heathrow

let airportCodes = [String](airports.keys)
// airportCodes is ["YYZ", "LHR"]

let airportNames = [String](airports.values)
// airportNames is ["Toronto Pearson", "London Heathrow"]
```
