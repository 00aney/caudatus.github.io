---
layout: post
title:  "스위프트의 역사:3.0 ~ 4.1"
date:   2018-04-28
author: Seo Jaehyeong
categories: Swift
tags:	Swift History
cover:
---

## Switf 3.0
2016년 6월, WWDC에서 스위프트 3.0버전을 발표했습니다.
- ++와 -- 연산자를 삭제했습니다.
- C스타일의 for반복문을 삭제했습니다.
- 함수를 호출할 때 함수의 첫 번째 매개변수 이름을 생략하지 않습니다.
- 라인 제어 구문의 `#line` 표현이 `#sourceLocation`으로 변경되었습니다.
- Objective-C의 셀렉터에 접근하기 위한 `#selector`표현이 추가되었습니다.
- 옵셔널 바인딩, if구문, while구문, guard구문 등에 where절 대신 쉼표(,)로 조건을 추가하도록 변경되었습니다.
- 사용자정의 연산자를 전역함수 대신 타입 메서드로 추가할 수 있게 되었습니다.
- `ErrorProtocol`프로토콜 이름이 `Error`로 변경되었습니다.
- `StringLiteralConvertible`프로토콜 이름이 `ExpressibleByStringLiteral`로 변경되었습니다.
- Boolean프로토콜이 스위프트 표준 라이브러리에서 삭제되었습니다.
- 접근수준에 open, fileprivate 수준이 추가 되었습니다.
- 함수 매개변수 클로저의 탈출 관련 기본 설정이 비탈출로 변경되었습니다.
- `@noescape`키워드가 사라지고 `@escaping`키워드가 추가되었습니다.

### 3.1
2017년 3월에는 스위프트 3.1 버전이 발표되었습니다. 좀 더 편리하게 사용할 수 있도록 언어 스펙 일부에 변화를 주었습니다.
- 중첩 제네릭 타입을 허용합니다.
- 제네릭 타입을 활장할 때, where절을 사용하여 연관타입에 제약을 줄 수 있게 되었습니다.
- Sequence프로토콜에 클로저를 매개변수로 갖는 drop과 prefix 메서드가 추가 되었습니다.
- 선언 속성 중 available 속성의 매개변수로 스위프트 언어 버전을 사용할 수 있게 되었습니다.

<br/>

## Swift 4.0
2017년 6월, WWDC에서 스위프트 4.0이 발표되었습니다.
- String 타입이 다시 Colleciton프로토콜을 준수합니다.
- 스위프트가 유니코드9을 따릅니다.
- 여러 줄 String 리터럴 문법이 추가되었습니다.
- Substring 타입과 StringProtocol이 추가되었습니다.
- KeyPath타입이 추가되었습니다.
- Codable프로토콜이 추가되었습니다.
- JSONEncoder와 JSONDecoder가 추가되었습니다.
- 컴파일러가 암시적으로 추가했던 @ojbc속성을 대부분 위치에서 프로그래머가 명확히 명시해 주어야 합니다.
- 프로토콜의 익스텐션에서 final수식어를 사용할 수 없게 되었습니다.

### 4.1
Generic, 새로운 빌드 옵션, Swift Package Manager 및 Foundation의 사소한 기능 향상에 대한 추가 지원을 포함하여 핵심 언어에 대한 업데이트가 포함되어 있습니다. [ABI][abi]를 안정시키는데 상당한 진전이 있었습니다.
- [SE-0143 Conditional Conformance][se-0143]
- [SE-0157 Support recursive constraints on associated types][se-0157]
- [SE-0185 Synthesizing Equatable and Hashable conformance][se-0185]
- [SE-0187 Introduce Sequence.compactMap(_:)][se-0187]
- [SE-0188 Make Standard Library Index Types Hashable][se-0188]
- [SE-0191 Eliminate IndexDistance from Collection][se-0191]

<br/>

## 참고
- [스위프트 프로그래밍][hanbit]



[abi]: https://ko.wikipedia.org/wiki/응용_프로그램_이진_인터페이스
[se-0143]: https://github.com/apple/swift-evolution/blob/master/proposals/0143-conditional-conformances.md
[se-0157]: https://github.com/apple/swift-evolution/blob/master/proposals/0157-recursive-protocol-constraints.md
[se-0185]: https://github.com/apple/swift-evolution/blob/master/proposals/0185-synthesize-equatable-hashable.md
[se-0187]: https://github.com/apple/swift-evolution/blob/master/proposals/0187-introduce-filtermap.md
[se-0188]: https://github.com/apple/swift-evolution/blob/master/proposals/0188-stdlib-index-types-hashable.md
[se-0191]: https://github.com/apple/swift-evolution/blob/master/proposals/0191-eliminate-indexdistance.md
[hanbit]: http://www.hanbit.co.kr/store/books/look.php?p_code=B2206901403
