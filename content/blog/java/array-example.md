---
title: '배열 예제'
excerpt: 자바의 정석 책으로 공부합니다.
date: 2020-11-25
category: 'Java'
draft: false
---

### 예제5-5

for문을 이용해서 배열에 저장된 값을 모두 더한 결과를   
배열의 개수로 나누어서 평균을 구하는 예제이다.   


```java
public class ArrayEx {
	public static void main(String[] args) {
		int sum =0;				//총점을 저장하기 위한 변수
		double average = 0d;	//평균을 저장하기 위한 변수
		
		int[] score = {100, 88, 100, 100, 90};
		
		for(int i=0; i < score.length; i++) {
			//반복문을 이용해서 배열에 저장되어 있는 값들을 모두 더한다.
			sum += score[i];
		}		
		//평균값을 double로 얻기 위해 형변환
		average = (double)sum/score.length;
		
		System.out.println("총점 : " + sum);
		System.out.println("평균 : " + average);
	}	
}

//실행결과
//총점: 478
//평균: 95.6
```





### 예제5-6

배열에 저장된 값 중에서 최대값과 최소값을 구하는 예제이다.   
반복문을 통해서 배열의 두 번째 요소 `score[1]`부터 max와 비교한다.   
만일 배열에 담긴 값ㅂ이 max에 저장된 값보다 크다면, 이 값을 max에 저장한다.  



```java
public class ArrayEx {
	public static void main(String[] args) {
		int[] score = {79, 88, 91, 23, 100, 55, 95};
		
		int max = score[0];	//배열의 첫 번째 값으로 최대값을 초기화한다.
		int min = score[0]; //배열의 첫 번째 값으로 최대값을 초기화한다.
		
		//배열의 두 번째 요소부터 읽기 위해 변수 i의 값을 1로 초기화
		for(int i =1; i < score.length; i++) {
			if(score[i] > max) {
				max = score[i];
			}else if(score[i] < min){
				min = score[i];
			}
		}
		System.out.println("최대값 : " + max);
		System.out.println("최소값 : " + min);
	}	
}

//실행결과
//최대값: 100
//최소값: 23
```


### 예제5-7
배열의 요소의 순서를 바꿔보자.   



```java
public class ArrayEx {
	public static void main(String[] args) {
		int[] numArr = new int[10];
		
		for (int i = 0; i < numArr.length; i++) {
			numArr[i] = i;	//배열을 0~9로 초기화 한다.
			System.out.print(numArr[i]);
		}
		System.out.println();
		
		for(int i=0; i < 100; i++) {
			int n = (int)(Math.random()*10);	//0~9중의 하나를 랜덤으로 얻는다.
			//numArr[0]과 numArr[n]의 값을 바꾼다.
			int tmp = numArr[0];
			numArr[0] = numArr[n];
			numArr[n] = tmp;
		}
		
		for(int i=0; i <numArr.length; i++) {
			System.out.print(numArr[i]);
		}
	}
}
```

길이가 10인 배열 `numArr`를 생성하고 0~9의 숫자로 차례대로 초기화하여 출력한다.   
그 다음 `random()`을 이용해서 배열의 임의의 위치에 있는 값과   
배열의 첫 번째 요소인 `numArr[0]`의 값을 교환하는 일을 100번 반복한다.   


만일 random()을 통해 얻은 값 n이 3이라면, 코드1은 코드2처럼 될 것이다.  
```java
//코드1
int tmp = numArr[0];
numArr[0] = numArr[n];	
numArr[n] = tmp; 

```


```java
//코드2
int tmp = numArr[0];
numArr[0] = numArr[3];
numArr[3] = tmp;
```

**코드2**는 `numArr[0]`과 `numArr[3]`에 저장된 값을 서로 바꾸는 일을 한다.   
두 컵에 담긴 내용물을 바꾸려면, 하나의 빈 컵이 더 필요한 것과 같다.   
여기서 변수 `tmp`가 빈컵의 역할을 한다.   



