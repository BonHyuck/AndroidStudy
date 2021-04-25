# 디모의 Kotlin 강좌

[링크](https://www.youtube.com/playlist?list=PLQdnHjXZyYadiw5aV3p6DwUdXV2bZuhlN)

> 유튜버의 강의로 먼저 Kotlin을 익혀보겠습니다.



## 1. 코틀린이란?

> Java 대체 목적으로 나온 언어

- 최신의 패러다임
- 자바 약점 개선
- JVM 호환 가능
- 안드로이드 개발 및 JS, Swift 연동 개발 가능

#### Android Studio or IntelliJ를 주로 사용하지만

[학습용 사이트](https://play.kotlinlang.org/)



## 2. 코틀린의 변수와 자료형

### 기본 문법

`//` : 1줄 주석, `/**/` : 여러줄, 세미콜론 필요없음

#### 표기법

- 클래스 : 파스칼 표기법(대문자로 시작), ClassName
- 함수, 변수 : 카멜 표기법(소문자로 시작), functionName

#### 변수 선언 방법

- `var` : 일반적으로 통용되는 변수, 언제든지 읽기 쓰기 가능
- `val` : 선언시에만 초기화 가능, 중간에 값 변경 불가

#### 변수의 종류

- Property(속성) : 클래스에 선언된 변수
- Local Variable : Scope 안에 선언된 변수

#### 사용 예시

```kotlin
fun main(){
	// 자료형 선언
	var b: Int
	b = 123
	var a: Int = 111
	var c: Int? = null
}
```

Kotlin에선 변수에 값이 없다면 에러를 띄운다

- nullPointException을 원천적으로 차단
- 자료형 뒤에 `?`를 붙이면 nullable

### Primitive type : 기본 자료형

> Java와 흡사하다

| 이름 | 크기 | 분류 |
| ---- | ----- | ------ |
| Byte | 8 bits | 정수형 |
| Short | 16 bits | 정수형 |
| Int | 32 bits | 정수형 |
| Long | 64 bits | 정수형 |
| Float | 32 bits | 실수형 |
| Double | 64 bits | 실수형 |
| Char | 16 bits | 문자 |
| Boolean |  | true/false |
| 문자열 |  | `""`혹은 `""""""` 사용 |

- 10진수 = 그냥 표기
- Long = 숫자 뒤에 L
- 16진수 = `0x`로 시작
- 2진수 = `0b`로 시작
- Double = 지수 표기법이나 소수점 포함
- Float = 숫자 뒤에 f나 F



## 3. 형변환과 배열

### 형변환 : Type casting

> 하나의 변수에 있는 자료형을 호환되는 자료형으로 변환

#### 형변환 함수

##### 명시적 형변환
-  .toByte() 
-  .toShort()
- .toInt() 
- .toLong()
- .toFloat()
- .toDouble()
- .toChar()

- 암시적 형번환은 지원하지 않음

### 배열

#### Array\<T\>

- 크기 변경이 불가능하다.

- 예시 
  - `var intArr = arrayOf(1, 2, 3, 4, 5)`
  - `var nullArr = arrayOfNulls<Int>(5)`
  - 사용법은 다른 언어와 같음



## 4. 타입추론과 함수

### 타입 추론 : Type Inference

> 변수나 함수들을 선언할 때나 연산이 일어날때 자료형을 코드에 명시하지 않아도 자동으로 자료형을 추론

할당된 값의 형태로 타입을 추론해서 자료형을 명시하지 않아도 된다.

### 함수 : Function

> 특정한 동작을하거나 원하는 결과값을 연산하는데 사용

- `fun`으로 선언 시작

```kotlin
// fun 함수명(변수:타입): 리턴타입(반환값이 없으면 생략) {}
fun something(a:Int, b:Int): Int {
    return a + b
}
```

#### 단일 표현식 함수 : Single-Expression Function

`fun something(a:Int, b:Int) = a + b`



## 5. 조건문, 비교연산자

### 조건문 : if

```kotlin
if(조건) {
	참일 경우 실행
} else {
	거짓일 경우 실행
}

if(조건) 참일 경우 실행
```

### 비교 연산자

부등호 & 등호(==)

- is : 자료형 '호환' 확인 및 형변환
- !is : not is

### 다중 조건문 : When (=다른 언어의 Switch)

- 변수에게 할당하는 용도로도 가능하다

```kotlin
/*
when(변수){
	확인할 값1 -> 참일 경우 실행
	확인할 값2 -> 참일 경우 실행
	else -> 위 조건이 전부 맞지 않을 경우 실행
}
*/

fun testWhen(a:Any){
    when(a){
        1 -> println('1입니다.')
        "Something" -> println("something")
    }
}
```



## 6. 반복문, 증감연산자

### 반복문

#### 조건형 반복문

> 조건이 참인 경우 반복을 유지

##### while, do while

```kotlin
while(조건){
	조건 동안 반복
}
```

```kotlin
do{
    조건 동안 반복
}while(조건)
```

- do while은 조건과 관계없이 우선 1번 실행한다.

#### 범위형 반복문

> 반복 범위를 정해 반복을 수행

##### for

```kotlin
// 보통 1씩 증가
for(변수 in 시작값..종료값){
    반복시킬 구문
}

// 증가값만큼 증가
for(변수 in 시작값..종료값 step 증가값){
    반복시킬 구문
}

// 시작값에서 감소되어 종료값으로
for(변수 in 시작값 downTo 종료값){
    반복시킬 구문
}
```



### 증감 연산자

#### 증가 연산자

- `a++` : 후위연산자, 다음 구문부터 사용

-  `++a` : 전위연산자, 이미 증가된 수를 반영 

#### 감소 연산자

- `a--` : 후위연산자, 다음 구문부터 사용

- `--a` : 전위연산자, 이미 감소된 수를 반영 