---
layout: post
title:  "Property List"
date:   2018-02-27
author: Seo Jaehyeong
categories: iOS
tags:	plist
cover:
---

## Property List - plist
* 심플한 `파일` 저장 방법 중 하나
* key, value 구조로 데이터 저장
* File 형태로 저장되다 보니 외부에서 Access 가능 (보안 취약)

### 파일 위치


번들
실행코드,이미지,사운드,nib파일, 프레임워크,설정파일 등 코드와리소스가 모여있는
file system내의 Directory

번들리소스확인

번들가져오기
샌드박스안에 있는 폴더이다.
싱글인스턴스 Bundle.main을 제공한다.
제일 먼저 경로를 가져와야한다. path라는 메소드를 사용하여 리소스를 가져온다
로드에 실패할 가능성이 있기때문에 옵셔널 변수로 받고 바인딩을 사용한다
파일의 path나 url을 요구하는 경우가 있다
