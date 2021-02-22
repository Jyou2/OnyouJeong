---
title: 'IO'
date: 2021-01-16
category: 'Java'
draft: false
---


### IO(입출력)

외부자원(키보드, 파일, DB서버, API서버 등등)으로 부터   
자바 프로그램으로(메모리로) 데이터를 읽어오거나 반대로 외부자원에 출력하는 것.   
<br>


### Stream

데이터가 오가는 **단방향** 통로이다.   
즉 하나의 Stream으로 입력과 출력을 모두 해결할 수 없다.   
입력과 출력을 하기 위해서는 반드시 두개의 Stream이 필요하다.   
Stream의 사용이 끝나면 반드시 Stream을 닫아줘야한다.(close())   
만약 사용이 끝난 Stream을 닫아주지 않으면 JVM이 알아서 닫아준다.   
하지만 예상하지 못한 예외상황이 발생할 수 있음으로 반드시 **수동으로** 닫아줘야 한다.   
보조스트림을 닫아주면 보조스트림안의 기반스트림까지 한번에 닫아준다.   
<br>




### 바이트스트림과 문자스트림

**바이트스트림**은 Stream을 통해서 입출력되는 데이터의 크기가 `1byte` 단위이다.   
**문자스트림**은 Stream을 통해 입출력되는 데이터의 크기가 `2byte` 단위이다.   
Java의 문자는 2byte이기 때문에 바이트스트림을 통해 문자를 주고 받을 경우,   
데이터가 유실되거나 문제가 발생하는 경우가 있다.   
2byte 단위로 데이터를 입출력하는 문자스트림이 문자를 다룰때는 안전하다.   
<br>




### 기반스트림과 보조스트림

**기반스트림** : 실제로 외부자원과 데이터를 입출력하는 스트림   
FileInputStream/FileOutputStream  - 파일 입출력 스트림
PipedInputStream/PipedOutputStream  - 쓰래드간 데이터를 입출력
ByteArrayInputStream/ByteArrayOutputStream  - 바이트 배열에 입출력
<br>


**보조스트림** : 기반스트림에 기능을 추가해주는 클래스   
BufferedInputStream/BufferedOutputStream   
중간 버퍼를 생산해 입출력 속도를 향상   
<br>
ObjectInputStream/ObjectOutputStream   
객체를 파일 또는 네트워크와 입출력할 수 있도록 기능을 제공   
<br>
InputStreamReader/OutputStreamWriter    
바이트기반의 스트림을 문자기반의 스트림으로 변환   
<br>


### 절대경로와 상대경로

절대경로 : root(window에서는 C드라이브)부터 경로를 지정하는 방식, \\\\로 경로 구분   
상대경로 : 현재 위치부터 경로를 지정하는 방식, /로 경로 구분   
공백 또는 ./ : 현재 위치    
../ : 현재 폴더의 상위폴더   


### 원하는 경로(폴더) 생성
mkdir() : 마지막 폴더 하나만 생성   
ex) "study/practice/project" -> project폴더만 생성, 만약 practice폴더가 없으면 에러   
<br>
mkdirs() : 여러 폴더를 동시에 생성   
ex) "study/practice/project" practice폴더가 없으면 practice도 한번에 생성   
<br>
exists() : 디렉토리에 파일이 있으면 true 없으면 false    
<br>
<br>


**OutputStream**

출력스트림   
프로그램(메모리)에 있는 데이터를 외부자원(데이터목적지)로 출력하는 스트림   
<br>

**InputStream**
입력스트림   
외부자원으로 부터 프로그램(메모리)로 데이터를 가져오는 스트림   
<br>


**BufferedInputStream**

기반스트림에게 내부 버퍼를 제공해 속도를 향상 시켜 주는 보조스트림   
내부 버퍼의 크기만큼 데이터를 외부자원으로 부터 한번에 읽어온 다음   
사용자가 필요한 만큼 데이터를 반환해준다.   
<br>


**BufferedOutputStream**
기반스트림에게 내부 버퍼를 제공해 속도를 향상 시켜주는 보조스트림   
내부 버퍼에 데이터를 저장한 다음 운영체제에 한번에 출력한다.   
<br>


버퍼가 가득 찰 경우 자동으로 데이터를 외부자원에 보내지만   
버퍼가 가득 차지 않아서 버퍼에 데이터가 남아있게 되는 경우가 있다.   
내부버퍼에 남아있는 데이터를 모두 파일로 송출하기 위해 `flush()`를 사용한다.   



