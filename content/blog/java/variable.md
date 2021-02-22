---
title: '변수(Variable)'
excerpt: 자바의 정석 책으로 공부합니다.
date: 2020-11-18
category: 'Java'
draft: false
---

## 기본형(primitive type)
### 논리형 - boolean
논리형에는 boolean 한가지 밖에 없다.
boolean형 변수에는 true와 false 중 하나를 저장할 수 있으며
기본값은(default)은 false이다.

### 문자형 - char
문자형 역시 char 한 가지 자료형 밖에 없다.
문자를 저장하기 위한 변수를 선언할 때 사용되며,
char타입의 변수는 단 하나의 문자만을 저장할 수 있다.

```Java
char ch = 'A';  //문자 'A'를 char 타입의 변수 ch에 저장.
```

위의 문장은 변수에 '문자'가 저장되는 것 같지만, 사실은 문자가 아닌 '문자의 유니코드(정수)'가 저장된다.
그래서 문자 리터럴 대신 문자의 유니코드를 직접 저장 가능
문자'A'의 유니코드는 10진수로 65이며, 아래의 두 문장은 동일한 결과를 얻는다.
```Java
char ch = 'A';
char ch = 65;
```

