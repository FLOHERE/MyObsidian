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
1. 변수
	- 변수는 이름과 자료형을 기반으로 확보한 메모리의 특정 공간을 말한다.
	- 프로그램이 실행되는 동안 이 공간 안의 내용물은 변경 불가
	- 실행문 중간에 변수 선언
		- C++의 변수 선언
			- 변수 선언은 아무곳이나 가능
			- 장점 : 변수 사용 직전 선언으로 변수 이름에 대한 타이핑 오류 감소
			- 단점 : 선언된 변수 일괄적으로 보기 힘듦 + 코드 사이에 있는 변수 찾기 어려움
2. 값
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

### cin과  >> 연산자를 이용한 키 입력
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

### C++ 문자열
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