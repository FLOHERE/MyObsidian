개요
	1. C++ 프로그램의 개요
	2. 변수, 값, 상수
	3. 토큰과 주석
	4. 자료형

## 01 C++ 프로그래밍 개요
- 기본적인 C++ 프로그램

```C++
/*소스 : SimpleC++.cpp
cout과 <<연산자를 이용하여 화면에 출력*/

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
	- ex_) 아파트에 같은 이름의 사람이 많다 -> n동 nnn호에 사는 누구씨