개요
	1. C++ 프로그램의 개요
	2. 변수, 값, 상수
	3. 토큰과 주석
	4. 자료형

## 01 C++ 프로그래밍 개요
- 기본적인 C++ 프로그램

```C++
//소스 : SimpleC++.cpp
//cout과 <<연산자를 이용하여 화면에 출력

#include <iostream> // cout, << 연산자가 있음
//C++ 프로그램은 main()함수에서 실행함
int main(){
	std::cout << "Hello\n";
	std::cout << "첫번째 맛보기 입니다.";
	return 0; //main함수 종료되면 프로그램 종료
}
```

- 주석문
	- 프로그램에 대한 설명, 개발자가 쓰는 특이 사항 메모
	- 프로그램의 실행에 영향 X
		- 여러줄 주석 : `/*~~~*/`
		- 한줄 주석 : `//`

- main() 함수
	- C++ 프로그램의 실행을 시작하는 함수
		- main() 함수가 종료하면 C++ 프로그램 종료
	- main() 함수의 C++ 표준 모양

```C++
int main(){
	.....
	return 0; //생략 가능
}
```

- `#include <iostream>`
	- 전처리기(C++ Preprocessor)에게 내리는 지시
		- `<iostream>` 헤더 파일을 컴파일 전에 소스에 확장하도록 지시
- `<iosteram>` 헤더 파일
	- 표준 입출력을 위한 클래스와 객체, 변수 등 선언
		- ios, istream, ostream, iostream 클래스 선언
		- cout, cin, <<, >> 등 연산자 선언

- 화면 출력
	- cout, <<
	- `std::cout << "Hello\n"` : Hello 출력하고 다음줄로 넘어감
		- `std`가 뭘까?
			- std를 사용하여 같은 이름의 함수나 변수의 충돌 방지(가독성 굳 + 유지보수)
			- 표준 입출력, 문자열 처리, 자료구조등을 쉽게 사용하게 해줌.
			- std를 계속 입력하기 귀찮기 때문에 `using namespace std` 를 맨위에 선언
	- `cout` 객체
		- 스크린 출력 장치에 연결된 표준 C++ 출력 스트림 객체
		- `<iostream>` 헤더 파일에 선언
		- std 이름 공간에 선언 : `std::cout` 로 사용
	- `<<` 연산자
		- 스트림 삽입 연산자(stream insertion operator)
			- C++ 기본 산술 시프트연산자가 스트림 삽입 연산자로 재정의
			- ostream 클래스에 구현
			- **오른쪽 피연산자를 왼쪽 스트림 객체에 삽입**
			- cout 객체에 연결된 화면에 출력
		- 여러개 사용 가능
		  `std::cout << "Hello\n" << "첫번째 맛보기 입니다."`

- `<<` 연산자 활용
	- 문자열 및 기본타입의 데이터 출력
		- bool, char, short, int, long, float, double
	- 연산뿐 아니라 함수 호출도 가능
	  `std::cout << f();`
	- 다음줄로 넘어가기
		- `\n` or `endl` 사용
			- `std::cout << "Hello" << '\n'`
			- `std::cout << "Hello" << std::endl;`

```C++
#include <iostream>
double area(int r); // 함수의 원형 선언

double area(int r){
	return 3.14*r*r;
}
int main(){
	int n = 3;
	char c = "#";
	std::cout << c << 5.5 << '-' << n << "hello" << true << std::endl;
	std::cout << "n+5 = " << n+5 << '\n';
	std::cout << "면적은" << area(n); // 함수 area() 의 리턴 값 출력
}
```

> 실행 결과 : 
> #5.5-3hello1
> n + 5 = 8
> 면적은 28.26

>[!note] printf()는 잊어라!!
>C++ 언어는 더이상 printf()와 scanf()를 사용하지 않는다.

- 이름 충돌 사례
	- ex_) 아파트에 같은 이름의 사람이 많다 -> n동 nnn호에 사는 누구씨 이렇게 부름

### namespace 개념
- 이름(identifier) 충돌이 발생하는 경우
	1. 여러명이 서로 나누어 프로젝트를 개발하는 경우
	2. 오픈소스 or 다른 사람이 작성한 소스나 목적파일을 가져와서 컴파일 or 링크하는 경우
	- 해결하는데 시간 + 노력 필요
- `namespace` 키워드
	- 이름 충돌 해결(2003년 C++ 표준에서 도입)
	- 개발자가 자신만의 이름 공간을 생성할 수 있도록 함
		- 이름 공간(namespace)안에 선언된 이름은 다른 이름공간과 별도 구분
		  (같은 이름이라도 namespace에 선언한것과 다른 namespace에 선언한건 구분된다는 의미)
	- 이름 공간 생성 및 사용 
		- `이름 공간 :: 이름`
		- `namespace kitae{이곳에 선언된 모든 이름은 kitae이름 공간에 생성된 이름} //kitae 라는 이름 공간 생성`

![[Pasted image 20250407215213.png]]

>[!note] Comment
>파이썬에서는 import as ~~ 를 통해 namespace 역할 수행.
>자바에서는 패키지와 클래스를 통해 이름을 구분한다.

### std:: 개념
- std
	- C++ 표준에서 정의한 이름공간(namespace)중 하나
		- `<iostream>` 헤더 파일에 선언된 모든 이름 : std 이름 공간에 있음
		- ex_)cout, cin, endl...
	- std 이름 공간에 선언된 이름을 접근하기 위해 std:: 접두어 사용
		- `std::cout`, `std::cin`, `std::endl`
	- std:: 생략 : `using` 지시어 사용(코드의 맨 윗줄에 선언)
		- `using std::cout;` : cout에 대해서만 std:: 생략
			- `cout << "Hello" << std::endl;` : std::cout에서 std::만 생략
		- `using namespace std;` : std 이름 공간에 선언된 모든 이름에 std:: 생략
			- `cout << "Hello" << endl;` : std 생략
- `#include <iostream>`과 `std`
	- `<iostream>` 이 통째로 `std` 이름 공간 내에 선언
	- `<iostream>` 헤더 파일을 사용하려면 다음 코드 필요

```C++
#include <iostream>
using namespace std;
```


1. 첫번째 프로그램
	- 프로그램 분석
		- 1행 전처리 지시자 : `#include` 지시자 뒤에는 세미콜른을 넣지 않는다.
		- 3행 함수 헤더 : main 함수에서 시작
		- 3행과 9행 중괄호 열고 닫기 : 중괄호 열고 닫는거 주의
		- `std::cout << "간단한 C++ 프로그램 입니다." << std::endl;`
			- `std::cout` : 대상(모니터)
			- `<< ` : 동작 (출력)
			- `"간단한 C++ 프로그램 입니다."`  : 출력할 문장
			- `std::endl`  : 문장 출력 후 다음줄로 이동
			- `;`  : 문장 종료

```C++
#include <iostream>

int main(){
	std::cout << "이 프로그램은 프로그램의 구조를 알아보기 위한";
	std::cout << "간단한 C++ 프로그램 입니다." << std::endl;
	std::cout << "이번 장과 이후의 내용을 통해";
	std::cout << "C++ 프로그래밍 언어와 관련된 다양한 것을 살펴보겠습니다.";
	return 0;
}
```

![[Pasted image 20250407222804.png]]

2. 두번째 프로그램
	- 프로그램 분석
		- 1~3행 : `/*~~*/` 주석은 컴파일러가 무시
		- 5행 : `using namespace std;`
		- 9행 : 별 기호로 정사각형 출력
		- 10~15행 : `using namespace std;` 사용으로 cout과 endl 앞에 std:: 생략

```C++
// 제목 : 별로 4각형을 출력하는 프로그램
#include <iostream>
using namespace std;

int main(){
	cout << "******" << endl;
	cout << "******" << endl;
	cout << "******" << endl;
	cout << "******" << endl;
	cout << "******" << endl;
	cout << "******" << endl;
	return 0;
}
```

## 02 변수, 값, 상수
### 1. 변수
- 변수는 이름과 자료형을 기반으로 확보한 메모리의 특정 공간을 말한다.
- 프로그램이 실행되는 동안 이 공간 안의 내용물은 변경 불가
- 실행문 중간에 변수 선언
	- C++의 변수 선언
		- 변수 선언은 아무곳이나 가능
		- 장점 : 변수 사용 직전 선언으로 변수 이름에 대한 타이핑 오류 감소
		- 단점 : 선언된 변수 일괄적으로 보기 힘듦 + 코드 사이에 있는 변수 찾기 어려움
### 2. 값
- 변수에 저장된 내용

```CPP
#include <iostream>
using namespace std;

int main(){
	//선언
	int num1;
	int num2;
	int sum;
	
	//입력받기
	cout << "first number input : ";
	cin >> num1;
	cout << "second number input : ";
	cin >> num2;
	
	//출력
	sum = num1 + num2;
	cout << "sum : " << sum;
	return 0;
}
```

>결과:
>first number input : 23
>second number input : 35
>sum : 58

>[!warning] 주의!!!!!@@@
> `<<` : 이 연산자는 **출력**을 해주는 친구
> `>>` : 이 연산자는 **입력**을 해주는 친구

- cin 객체와 cout 객체
	- cin 객체 : 변수의이름을 알아야 함
	- cout 객체 : 값을 알아야 함

#### cin과  >> 연산자를 이용한 키 입력
- cin : 표준 입력 장치(키보드)를 연결하는 C++ 입력 스트림 객체
- >> 연산자
	- 스트림 추출 연산자(stream extraction operator)
		- C++ 산술 시프트 연산자(>>)가 `<iostream>` 헤더 파일에 [[스트림]] 추출 연산자로 재정의됨
		- 입력 스트림에서 값을 읽어 변수에 저장
	- 연속된 >> 연산자를 사용하여 여러 값 입력 가능
- Enter키 누르면 변수에 값 전달
	- cin의 특징
		- 입력 버퍼를 내장하고 있음
		- 엔터키가 입력될때까지 입력된 키를 입력 버퍼에 저장
	- >> 연산자
		- 엔터키가 입력되면 cin의 입력 버퍼 -> 키 값 읽음 -> 변수에 전달

![[Pasted image 20250408172757.png]]

#### C++ 문자열
1. C-String 방식
2. '\0' 으로 끝나는 문자 배열

![[Pasted image 20250408173134.png]]

- string 클래스 사용
	- `<String>` 헤더 파일에 선언
	- 다양한 멤버 함수 제공, 문자열 비교, 복사, 수정
1.  C-String으로 문자열 다루기
	- C 언어에서 사용한 함수 사용 가능
		- ex_) `strcmp()` , `strlen()` , `strcpy()`...
- 

```c++
#include <cstring> //이렇게 쓰는게 국룰(표준 방식)
#include <string.h>

int n = strlen("hello");
```

- cin을 이용한 문자열 입력
	1. 빈 배열 만들기
	2. 입력 받기
	3. 리스트에 저장
- 근데 리스트를 초과해서 입력 받으면 ? 
	- 오류 생김
	- 동적크기 리스트 사용 필요

```C++
char name[6]; //다섯개의 문자를 저장 할수있는 char배열
cin >> name; //키보드로 부터 문자열을 읽어 name 배열에 저장
```

- 키보드에서 문자열 입력받고 출력
	- 주의!!@@ 문자 입력중 빈칸을 만나면 문자열이 종료됨

```C++
#include <iostream>
using namespace std;

int main(){
	cout << "이름을 입력하세요>>";
	char name[11]; //한글은 5글자, 영문은 10자까지 저장 가능
	cin >> name; //키보드로 부터 문자열 읽는다.
	cout << "이름은" << name << " 입니다.\n"; //이름 출력
}
```

- C-String 이용, 암호가 입력되면 프로그램을 종료하는 예

```C++
#include <iostream>
#include <cstring> //strcmp() 함수 사용을 위한 헤더 파일
using namespace std;

int main(){
	char password[11];
	cout << "프로그램을 종료하려면 암호를 입력하세요" << endl;
	while(true){
		cout << "암호 >> ";
		cin >> password;
		if(strcmp(password, "C++")==0){
			cout << "프로그램을 정상 종료합니다." << endl;
			break;
		}else
		cout << "암호가 틀립니다~~" << endl;
	}
}
```

>결과:
>프로그램을 종료하려면 암호를 입력하세요.
>암호 >>JAVA
>암호가 틀립니다~~
>암호 >>C++
>프로그램을 정상 종료합니다.

- cin.getline()으로 공백이 낀 문자열 입력
	- 공백이 낀 문자열 입력받는 방법
		- `cin.getline(char buf[], int size, char delimitChar)`
			1.  buf에 최대 size-1개의 문자 입력. 끝에 '\0' 붙임
			2. delimitChar 를 만나면 입력 중단. 끝에 '\0' 붙임
				- delimitChar의 디폴트 값은 '\n'(한줄 띄우기)

```C++
char address[100]
cin.getline(address, 100, '\n');
//최대 99개의 문자를 읽어 address배열에 저장, 도중에 엔터키 입력시 입력 중단.
```

- cin.getline()을 이용한 문자열 입력
	- 빈칸이 있어도 Enter키가 입력될때까지 하나의 문자열로 인식

```C++
#include <iostream>
using namespace std;

int main(){
	cout << "주소를 입력하세요 >>";
	char address[100];
	cin.getline(address, 100, '\n'); //키보드로 부터 주소 읽기
	
	cout << "주소는" << address << "입니다\n"; //주소 출력
}
```

>결과:
>주소를 입력하세요 >>컴퓨터시 프로그램구 C++동 스트링 1-1
>주소는 컴퓨터시 프로그램구 C++동 스트링 1-1 입니다.

- C++에서 문자열을 다루는 string 클래스(C-String과는 다름)
	- C++ 표준 클래스
	- 문자열의 크기에 따른 제약 없음
		- string 클래스가 스스로 문자열 크기에 맞게 내부 버퍼 조절
	- 문자열 복사, 비교, 수정등을 위한 다양한 함수와 연산자 제공
	- 객체 지향적
	- `<string>` 헤더 파일에 선언
		- `#include <string>` <-- 이렇게 쓴다
	- C-String 보다 쓰기 쉽다.

```C++
#include <iostream>
#include <string> //string 클래스 사용을 위한 헤더 파일
using namespace std;

int main(){
    string song("falling in love with you"); //문자열 song
    string elvis("Elvis Presley"); //문자열 elvis
    string singer; //문자열 singer
	
    cout << song + "를 부른 가수는"; // + 로 문자열 연결
    cout << "(힌트 : 첫 글자는 )" << elvis[0] << ")?"; //[ ] 연산자 사용
	
    getline(cin, singer); //문자열 입력
    if(singer == elvis) //문자열 비교
        cout << "맞았습니다";
    else
        cout << "틀렸습니다." + elvis + "입니다." << endl; //+로 문자열 연결
}
```

>결과:
>falling in love with you를 부른 가수는(힌트 : 첫 글자는 E)?몰루
>틀렸습니다. Elvis Presley 입니다.

- `#include <iostream>`와 전처리기
	- `#include <iostream>` 은 전처리기 지시문 입니다.
	- 전처리 과정
		1. `#include <iostream>`이 전처리기를 통과
		2. 컴파일 전, 특정 파일을 현재 소스코드에 포함시킨다.
		3. 확장된 C++.cpp 파일완성 (전처리기의 정보 포함한 파일이 됨)
		4. 컴파일
- `<iostream>` 헤더 파일은 어디 있을까?
	- 확장자 없는 텍스트 파일
	- 컴파일러가 설치된 폴더 아래 include 폴더에 존재
		- 버전에 따라 경로가 다름 주의

- 표준 C++ 헤더 파일은 확장자가 없다
	- std 이름 공간 적시
		- `#include <iostream>`
		- `using namespace std;`
- 헤더 파일의 확장자 비교

| 언어  | 헤더 파일 확장자 | 사례           | 설명                               |
| --- | --------- | ------------ | -------------------------------- |
| C   | .h        | `<string.h>` | C/C++ 프로그램에서 사용 가능               |
| C++ | 확장자 없음    | `<cstring>`  | using namespace std;와 함께 사용해야 함. |
- `#include <헤더 파일>` 
	- '헤더파일'을 찾는 위치
	- 컴파일러가 설치된 폴더에서 찾으라는 지시
- 헤더 파일에는 무엇이 있는가?(질문 모음집)
	1. `<cstring>` 파일에 `strcpy()` 함수의 코드가 들어 있을까?
		- (X) : 함수의 정보가 들어가있는거임.
	2. `strcpy()` 함수의 원형이 선언되어 있다.
		- (O)
	3. `strcpy()` 함수의 코드는 어디 있을까?
		- 컴파일된 바이너리 코드로, 비주얼 스튜디오가 설치된 lib 폴더에 libcmt.lib 파일에 들어있음
		- 링크시 `strcpy()` 함수의 코드가 exe에 들어간다.
	4. 그럼 헤더 파일은 왜쓰냐?
		- 사용자 프로그램에서 `strcpy()` 함수를 호출하는 구문이 정확한지 확인하기 위해 컴파일러에 의해 필요함.

>[!warning] 함수의 코드 VS 함수의 원형 의미 차이는?
>함수의 코드 : 실제로 동작하는 코드를 말함.
>함수의 원형 : 함수의 매개변수 타입, 함수의 이름, 반환 타입등을 포함하는 형태(단순 정보 제공)

- cin 과 cout 는 어디에 선언되어 있는가?
	- `<iostream>` 헤더 파일에 선언되어 있다.
	- `#include <iostream>` 을 한 프로그램에는 자동을로 cin과 cout이 전역변수로 선언한 결과가 됨
		- 프로그램에서 cin과 cout 바로 사용 가능

- 할당 연산자
	- 오른쪽에 있는 변수는 값으로 활용
	- 소스로서의 값 의미
	- 왼쪽에 있는 변수는 값의 저장 목적지로 사용
	- `변수 = 값;` 의 형태

### 3. 상수
- 값을 변경할수 없는 저장소 엔티티
- 언제나 고정정
- 상수 선언시 `const` 라는 한정자와 이름 지정
	- 이후 할당 연산자를 입력, 저장할 값 지정
- `const double PI = 3.14159;` 

## 03 토큰과 주석

### 1. 토큰
- 식별자
	- C++ 프로그래밍 언어는 엔티티 이름을 실별자(identifier)라고 함
	- 키워드, 미리 정의된 식별자, 사용자 정의 식별자로 구분
- 키워드
	- 키워드(keyword) 또는 예약어라고도 부름
	- C++ 프로그래밍 언어에서 미리 예약된 식별자

![[Pasted image 20250408213953.png]]

![[Pasted image 20250408214050.png]]

- 리터럴
	- 리터럴은 자료형을 가진 상수 값을 의미
- 심볼
	- C++ 은 알파벳이 아닌 기호들을 연산자와 문장 부호로 사용

![[Pasted image 20250408214200.png]]

### 2. 주석
- 한줄 주석
	- 간단한 주석을 만들때 쓴다.
	- // 부터 시작해서 줄 끝까지
- 여러 줄 주석
	- 여러 줄에 걸쳐있는 주석
	- 시작 부분을 정의하는 `/*` 기호와 종료 부분을 정의하는 `*/` 기호 필요
- 중첩 주석
	- 중첩 주석 지원 X

## 04 자료형
### 1. 자료형
1. 내장 자료형
	1. 기본 자료형
		- 정수(int)
		- 문자(char)
		- 불(bool)
		- 부동 소수점
		- Void
	2. 복합 자료형
2. 사용자 정의 자료형
	1. 열거 형
	2. 클래스

### 2. 정수 자료형
- signed 는 생략 가능 but unsigend는 생략 불가

| 자료형       | 부호                                     | 범위                                                    |
| --------- | -------------------------------------- | ----------------------------------------------------- |
| short int | 부호 있음 : (signed)<br>부호 없음 : (unsigned) | -32,768 ~ +32,767<br>0 ~ 65,536                       |
| int       | 부호 있음 :<br>부호 없음:                      | -2,147,483,648 ~ + 2,147,483,648<br>0 ~ 4,294,967,295 |
| long int  | 부호 있음 :<br>부호 없음 :                     | -2,147,483,648 ~ + 2,147,483,647<br>0 ~ 4,294,967,295 |

>[!note] signed와 unsigned를 왜쓸까?
>메모리 절약 및 명확성을 위해 사용.

```C++
//동전과 지폐들의 금액 합계를 구하는 프로그램
#include <iostream>
using namespace std;

int main(){
    const unsigned int pennyValue = 1;
    const unsigned int nickelValue = 5;
    const unsigned int dimeValue = 10;
    const unsigned int quarterValue = 25;
    const unsigned int dollarValue = 100;
    //변수 정의(각 코인의 수)
    unsigned int pennies;
    unsigned int nickels;
    unsigned int dimes;
    unsigned int quarters;
    unsigned int dollars;
    //전체 값을 나타내는 변수선언
    unsigned long totalValue;
    //코인 입력 받기
    cout << "페니의 수 : ";
    cin >> pennies;
    cout << "니켈의 수 : ";
    cin >> nickels;
    cout << "다임의 수 : ";
    cin >> dimes;
    cout << "쿼터의 수 : ";
    cin >> quarters;
    cout << "달러의 수 : ";
    cin >> dollars;
    //전체 금액 계산
    totalValue = pennies * pennyValue + nickels * nickelValue + dimes * dimeValue + quarters * quarterValue + dollars * dollarValue;
    // 결과 출력
    cout << "전체 값은 " << totalValue << "페니 입니다.";
    return 0;
}
```

- 정수 변수

```C++
// 3회 거래 후의 계좌 잔액
#include <iostream>
using namespace std;

int main(){
    int balance = 0;
    int transaction;
    //첫번째 거래 후 잔액 조정
    cout << "첫번째 거래 금액 입력 : ";
    cin >> transaction;
    balance = balance + transaction;
    // 두번째 거래 후 잔액 조정
    cout << "두번째 거래 금액 입력 : ";
    cin >> transaction;
    balance = balance + transaction;
    //세번째 거래 후 잔액 조정
    cout << "세번째 거래 금액 입력 : ";
    cin >> transaction;
    balance = balance + transaction;
    // 최종 잔액 출력
    cout << "계좌의 최종 잔액은 " << balance << "달러 입니다.";
    return 0;
}
```

- 정수 변수

```C++
//3가지 정수 자료형의 크기를 확인하는 프로그램
#include <iostream>
using namespace std;

int main(){
    cout << "short int의 크기는 " << sizeof(short int) << "바이트 입니다." << endl;
    cout << "int 의 크기는 " << sizeof(int) << "바이트 입니다." << endl;
    cout << "long int의 크기는 " << sizeof(long int) << "바이트 입니다." << endl;
    return 0;
}
```

- 정수 리터럴
	- long : 접미사 'l' or 'L'을 사용하여 타입 명시
	- unsigned int // unsigned long : 접미사 'u' or "U" 사용

```C++
//변수를 초기화 할떄 리터럴을 사용하는 프로그램
#include <iostream>
using namespace std;

int main(){
    int x = -1245; //OK
    unsigned int y = 1245; //OK
    unsigned int z = -2367; //논리적 오류, 음수값이 양수 값으로 바뀜
    unsigned int t = 14.56; //소수점 아래 부분 잘림
    //초기화된 값 출력
    cout << x << endl;
    cout << y << endl;
    cout << z << endl;
    cout << t;
    return 0;
}
```

- 정수 리터럴

```C++
//리터럴 값을 단독으로 사용하는 프로그램
#include <iostream>
using namespace std;

int main(){
    int x;
    unsigned long int y;
    //할당
    x = 1456;
    y = -14567;
    //출력
    cout << x << endl; //OK
    cout << y << endl; //잘못된 값(부호 없는 정수를 나타내는 변수, 음수 할당해서 발생하는 문제)
    cout << 1234 << endl; //OK
    cout << 143267L << endl; //OK
    return 0;
}
```

### 3. 문자 자료형
- 이스케이프 문자
	- `\n` : 줄바꿈
	- `\t` : 탭
	- `\b` : 백 스페이스
	- `\r` : 캐리지 리턴(커서의 위치 앞으로 이동)
	- `\f` : 폼 피드(다음 페이지로 넘기기)
	- `\'` : 작은 따옴표
	- `\"` : 큰 따옴표
	- `\\` : 역 슬래시

```C++
//char 자료형의 변수를 선언 -> 초기화 하는 프로그램
#include <iostream>
using namespace std;

int main(){
    //char 자료형의 변수 선언과 초기화
    char first  = 'A';
    char second = 65;
    char third = 'B';
    char fourth = 66;
    //값 출력
    cout << "first의 값 : " << first << endl;
    cout << "second의 값 : " << second << endl;
    cout << "third의 값 : " << third << endl;
    cout << "fourth의 값 : " << fourth;
    return 0;
}
```

```C++
//이스케이프 문자를 사용하는 프로그램
#include <iostream>
using namespace std;

int main(){
    cout << "Hello\n";
    cout << "Hi\t friends." << endl;
    cout << "Buenos dias  \bamigos." << endl; //이전 글자 삭제(띄어쓰기 하나 삭제됨)
    cout << "Hello\rBonjour mes amis." << endl; //줄의 앞부분으로 커서를 옮기고 다시 입력(따라서 앞의 내용 삭제)
    cout << "This is a single quote \'." << endl; //
    cout << "This is a double quote\"." << endl;
    cout << "This is how to print a backslash \\.";
    return 0; 
}
```

### 4. 불타입
- 불 변수 
	- 참 or 거짓
	- `bool` 키워드 사용
- 불 리터럴
	- 0 : false
	- 0이 아닌 값 : true

```C++
// 불 변수와 값을 사용하는 프로그램
#include <iostream>
using namespace std;

int main(){
    bool x = 123; //boolean은 0이상이면 무조건 true임.
    bool y = -8;
    bool z = 0;
    bool t = -0;
    bool u = true;
    bool v = false;
    //값출력
    cout << "x : " << x << endl;
    cout << "y : " << y << endl;
    cout << "z : " << z << endl;
    cout << "t : " << t << endl;
    cout << "u : " << u << endl;
    cout << "v : " << v << endl;
    return 0;
}
```

### 5. 부동 소수점 자료형
- 소수점을 갖는 숫자를 말함. (floatingpoint)
- float, double, long double
	- `float <= double <= long double`
- 부동 소수점 변수
	- 부동 소수점 변수도 정수 변수를 선언할때와 같은 방법으로 정의
	- 선언하면서 어떤 값으로 초기화 할수 있고 이후 다른 값으로 할당 가능
- 부동 소수점 리터럴
	- float : 'f' or 'F' 사용
		- ex_) 12.3F , 1234,45F, -1436F
	- double : 없음
	- long double : 'l' or 'L' 사용

```C++
//원의 반지름을 기반으로 둘레와 면적을 구하는 프로그램
#include <iostream>
using namespace std;

int main(){
    const double PI = 3.14159;
    double radius;
    double perimeter;
    double area;
    cout << "원의 반지름 입력 : ";
    cin >> radius;
    perimeter = 2*PI*radius;
    area  = PI * PI * radius;
    cout << "반지름 : " << radius <<endl;
    cout << "둘레 : " << perimeter << endl;
    cout << "면적 : " << area;
    return 0;
}
```

### 6. void 자료형
- 값이 없음을 나타내는 특별한 자료형
- "함수가 어떠한 값도 결과로 내지 않는다" 를 명시

### 7. 문자열 자료형
- `#include <string>` : 문자열을 쓸수있는 헤더 파일 명시
- `string name;` <-- 이런식으로 사용

```C++
//이름, 이니셜, 성을 입력받고 결합해서 출력하는 프로그램
#include <iostream>
#include <string>
using namespace std;

int main(){
    string first;
    string initial;
    string last;
    string space = " ";
    string dot = ".";
    string fullName;
    //값 입력 받기
    cout << "이름 : ";
    cin >> first;
    cout << "이니셜 : ";
    cin >> initial;
    cout << "성 : ";
    cin >> last;
	
    fullName = first + space + initial + dot + space + last;
    cout << "전체 이름 : " << fullName;
    return 0;
}
```


---

# 연습문제 코드 모음집

```C++
// short 자료형과 unsinged int 자료형의 최대값과 최소값을 찾는 프로그램을 만드세요.
#include <iostream>
using namespace std;

int main(){
    short max_value = std::numeric_limits<short>::max(); //32767
    const unsigned int max_value1 = std::numeric_limits<int>::max(); //2147483647

    cout << max_value << endl;
    cout << max_value1 << endl;

}
```


```C++
//long 자료형과 longlong 자료형의 최대값과 최소값을 찾는 프로그램을 만드세요
#include <iostream>
using namespace std;

int main(){
    long max_value1 = std::numeric_limits<long> :: max();//9223372036854775807
    long min_value1 = std::numeric_limits<long> :: min();//-9223372036854775808

    long long max_value2 = std::numeric_limits<long long> :: max(); //9223372036854775807
    long long min_value2 = std::numeric_limits<long long> :: min(); //-9223372036854775808

    cout << max_value1 << endl;
    cout << min_value1 << endl;
    cout << max_value2 << endl;
    cout << min_value2 << endl;
}
```

```C++
//float 자료형과 double 자료형의 최대값과 최소값을 찾는 프로그램을 만드세요.
#include <iostream>
using namespace std;

int main(){
    float max_value1 = std::numeric_limits<float> :: max(); //3.40282e+38
    float min_value1 = std::numeric_limits<float> :: min(); //1.17549e-38

    double max_value2 = std::numeric_limits<double> :: max();//1.79769e+308
    double min_value2 = std::numeric_limits<double> :: min();//2.22507e-308

    cout << max_value1 << endl;
    cout << min_value1 << endl;
    cout << max_value2 << endl;
    cout << min_value2 << endl;
}
```

```C++
//int 자료형의 정수를 입력 받아서, 두번째 자릿수를 추출한 뒤 출력하는 프로그램을 만드세요
#include <iostream>
using namespace std;

int main(){
    unsigned int number, secondDigit;
    cin >> number;
    cout << "\n";
    secondDigit = (number / 10)%10;

    cout << secondDigit;
}
```

```C++
//int 자료형의 정수를 입력 받아서, 첫번째부터 세번째 자릿수를 각각 출력하는 프로그램을 만드세요
#include <iostream>
using namespace std;

int main(){
    int num;
    cin >> num;

    int result1 = num/100; //셋쩨 자리 수
    int result2 = (num%100)/10; // 둘째자리 수
    int result3 = (num%100)%10; //첫째자리 수

    cout << result1 << endl;
    cout << result2 << endl;
    cout << result3 << endl;
}
```

```C++
//세자릿수 정수가 주어졌을떄, 해당 숫자를 역순으로 하는 정수를 구성하고 출력하는 프로그램을 만드세요(ex:372 -> 273 출력)
#include <iostream>
using namespace std;

int main(){
    int num;
    cin >> num;

    int num1 = (num/100);
    int num2 = (num%100)/10;
    int num3 = (num%100)%10;

    cout << num3 << endl;
    cout << num2 << endl;
    cout << num1 << endl;
}
```

```C++
//시간을 입력으로 받을때, 이를 주, 일, 시간으로 변환하는 프로그램(0~6일, 0~23시)
#include <iostream>
using namespace std;

int main(){
    int time;
    cin >> time;

    int week = (time/24)/7;
    int day = time/24;
    int RealTime = time%24;

    cout << "Week : " << week << endl;
    cout << "day : " << day << endl;
    cout << "Real time : " << RealTime << endl;
}
```

```C++
//시간을 시, 분, 초 단위로 입력받았을때, 이를 초 단위로 변환하는 프로그램을 만드세요
#include <iostream>
using namespace std;

int main(){
    int hour, min, sec;
    cin >> hour;
    cin >> min;
    cin >> sec;

    int result = (hour*60)*60 + (min*60) + sec;
    cout << result << endl;
}
```

```C++
//초단위(long 자료형)를 입력받았을때, 이를 시, 분, 초 단위로 변환하는 프로그램을 만드세요
#include <iostream>
using namespace std;

int main(){
    long sec;
    cin >> sec;

    int hour = (sec/60)/60;
    int min = (sec/60)%60;
    int secResult = (sec%60)%60;

    cout << hour << ":";
    cout << min << ":";
    cout << secResult;
}
```

