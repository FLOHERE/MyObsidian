- `<cmath>` : 수학 관련 라이브러리 함수
	- abs(x) : x의 절대값
	- ceil(x) : 올림
	- floor(x) : 내림
	- log(x) : x 의 자연 로그(밑이 e) 리턴
	- log10(x) : x의 상용 로그(밑이 10) 리턴
	- exp(x) : e^x 를 리턴
	- pow(x,y) : x^y를 리턴
	- sqrt(x) : x의 루트를 리턴

```cpp
/* 다음 함수들을 실행할수 있는 짧은 프로그램을 작성하세요
a. abs(25) 와 abs(-23)
b. floor(44.56)과 floor(-23.78)
c.ceil(25.33)과 ceil(-2.89) */

#include <iostream>
#include <cmath>
using namespace std;

int main(){
    cout << "abs(25) = " << abs(25) << endl;
    cout << "abs(-23) = "  << abs(-23) << endl;
    cout << "floor(44.56) = " << floor(44.56) << endl;
    cout << "floor(-23.78) = " << floor(-23.78) << endl;
    cout << "ceil(25.33) = " << ceil(25.33) << endl;
    cout << "ceil(-2.89) = " << ceil(-2.89) << endl;
}
/* 결과 : 
abs(25) = 25
abs(-23) = 23
floor(44.56) = 44
floor(-23.78) = -24
ceil(25.33) = 26
ceil(-2.89) = -2
*/
```

```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main(){
    int a,b,c;
    double term;

    cout << "계수 a의 값을 입력하세요 : ";
    cin >> a;
    cout << "계수 b의 값을 입력하세요 : ";
    cin >> b;
    cout << "계수 c의 값을 입력하세요 : ";
    cin >> c;

    term = pow(b,2) - 4 * a * c;
    if(term < 0){
        cout << "근이 없습니다." << endl;
    }else if(term == 0){
        cout << "두 근이 같습니다." << endl;
        cout << "x1 = x2 = " << -b/(2*a) << endl;
    }else{
        cout << "서로 다른 근 2개가 있습니다." << endl;
        cout << "x1 = " << (-b + sqrt(term)) / (2*a) << endl;
        cout << "x2 = " << (-b -sqrt(term)) / (2*a) << endl; 
    }
}
```

- 삼각함수
	- cos(x) : 코사인 리턴
	- sin(x) : 사인 리턴
	- tan(x) : 탄젠트 리턴
	- acos(x) : 역 코사인
	- asin(x) : 역사인
	- atan(x) : 역 탄젠트

```CPP
//삼각 함수 프로그램
#include <iostream>
#include <cmath>
using namespace std;

int main(){
    const double PI = 3.14592653589793238462;
    double degree = PI/4;
	
    cout << "sin(45) : " << sin(degree) << endl;
    cout << "cos(45) : " << cos(degree) << endl;
    cout << "tan(45) : " << tan(degree);
    return 0;
}
```

```cpp
//정 다각형의 둘레와 넓이 구하기

#include <iostream>
#include <cmath>
using namespace std;

int main(){
    const double PI = 3.14592653589793238462;
    int n;
    double s,peri,area;
	
    do{
        cout << "변의 개수를 입력하세요 (4 이상 정수): ";
        cin>>n;
    }while (n<4);
	
    do{
        cout << "변의 길이 입력 : ";
        cin >> s;
    }while(s <= 0.0);
	
    peri = n * s;
    area = (n*pow(s,2))/(n*tan(PI / n));
	
    cout << "둘레 : " << peri << endl;
    cout << "넓이 : "<< area;
}
```

- `<cctpye>` : 문자 구분 함수
	- int isalnum(int x) : 매개변수가 알파벳 또는 숫자인지 확인
	- int isalpha(int x) : 매개변수가 알파벳인지 확인
	- int iscntrl(int x) : 매개변수가 control 문자인지 확인
- 문자 변환 함수
	- int tolower(int x) : 매개변수를 소문자로 변환
	- int toupper(int x) : 매개변수를 대문자로 변환

```cpp
//문자 함수 사용하기
#include <iostream>
#include <cctype>
using namespace std;

int main(){
    char ch;
    int count = 0;

    while(cin >> noskipws >> ch){
        if(isalpha(ch)){
            count++;
        }
        ch = toupper(ch);
        cout << ch;
    }
    cout << "알파벳 문자의 개수 : " << count;
    return 0;
}
```

- `<ctime> ` : 시간 함수 
	- 유닉스 타임 기준 : 1970년 1월 1일 기준 ~ 현재시간

```cpp
//현재 시간 찾기(그리니치 표준시)
#include <iostream>
#include <ctime>
using namespace std;

int main(){
    long elaspedSeconds = time(0);
    int currentSecond = elaspedSeconds % 60;

    long elpasedMinutes = elaspedSeconds / 60;
    int currentMinute = elpasedMinutes % 60;

    long elapsedHours = elpasedMinutes / 60;
    int currentHour = elapsedHours % 24;

    cout << "현재 시간 = ";
    cout << currentHour << " : " << currentMinute <<" : " << currentSecond;
    return 0;
}
```

- `<cstdlib>` : 랜덤 숫자 관련 함수 사용 `srand(time(0))`
	- 범위 확대, 축소 : `temp = rand() % (b-a+1)`
	- 범위 이동 : `result = temp + a`

```cpp
// 숫자 추측 게임
#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

int main(){
    int low = 5;
    int high = 15;
    int tryLimit = 5;
    int guess;

    srand(time(0));
    int temp = rand();
    int num = temp % (high-low +1) + low;

    int counter = 1;
    bool found = false;
    while(counter <= tryLimit && !found){
        do{
            cout << "5~15 사이의 정수를 입력하세요 : ";
            cin >> guess;
        }while(guess < 5 || guess > 15);
			
        if(guess == num){
            found = true;
        }else if(guess > num){
            cout << "더 작은 숫자 입니다. " << endl;
        }else{
            cout << "더 큰 숫자 입니다. " << endl;
        }
        counter++;
    }
    if(found){
        cout << "축하합니다. 추측에 성공 했습니다.";
        cout << "답 = " << num;
    }
    else{
        cout << "아쉽게 추측에 실패 했습니다.";
        cout << "답 = " << num;
    }
    return 0;
}
```

- 함수의 네가지 사용 패턴

```cpp
// 첫번째 : 매개변수 없는 void 함수
void 이름(){
	...
	return;
}

//두번째 : 매개변수 있는 void 함수
void 이름(자료형 parameter, ...){
	...
	return;
}

//세번째 : 매개변수가 없지만 리턴값이 있는 함수
자료형 이름(){
	...
	return value;
}

//네번째 : 매개변수와 리턴값이 있는 함수
자료형 이름(자료형 parameter){
	...
	return value;
}
```

```cpp
//매개변수가 없는 void 함수
#include <iostream>
using namespace std;

void greeting(){ // 매개변수가 없는 void 함수, 리턴은 없지만 화면에 메세지를 출력할수 있다.
    cout << "*********************" << endl;
    cout << "* 안녕하세요!          *" << endl;
    cout << "*********************";
    return;
}
int main(){
    greeting();
    return 0;
}

```

```cpp
//매개변수가 있는 void 함수
#include <iostream>
using namespace std;

void pattern(int size){ //매개변수가 있는 void 함수
    for(int i  = 0; i<size; i++){
        for(int j = 0; j < size; j++){
            cout << "*";
        }
        cout << endl;
    }
    return;
}

int main(){
    int patternSize;

    do{
        cout << "패턴의 크기를 입력하세요 : ";
        cin >> patternSize;
    }while (patternSize <= 0);

    pattern(patternSize); // patternSize 는 인수다.
    return 0;
    
}
```

```cpp
//매개변수가 없지만 리턴값이 있는 함수
#include <iostream>
using namespace std;

int getData(){
    int data;
    do{
        cout << "양의 정수를 입력하세요 : ";
        cin >> data;
    }while (data<=0);
    return data;
}

int main(){
    int number = getData();
    cout << "가장 오른쪽의 숫자 = "<< number%10;
    return 0;
}
```

```cpp
//매개변수와 리턴값이 있는 함수

#include <iostream>
using namespace std;

int larger(int fst, int snd){
    int max;
    if(fst>snd){
        max = fst;
    }else{
        max = snd;
    }
    return(max);
}

int main(){
    int first, second;
    cout << "첫번째 숫자를 입력하세요 : ";
    cin >> first;
    cout << "두번째 숫자를 입력하세요 : ";
    cin >> second;
    cout << "두 수 중에 큰것  = " << larger(first,second);
    return 0;
}
```

- 선언 : `type name(type, type,...);`
- 호출 : `name(arg1, arg2, ...);`
- 정의 : `type name(type1 p1, type2 p2){ }`

```cpp
//윤년인지 확인하기

#include <iostream>
using namespace std;

int input();
bool process (int year);
void output(int year, bool result);

int main(){
    int year = input();
    bool result = process(year);
    output(year, result);
    return 0;
}

int input(){
    int year;
    do{
        cout << "1582년 이후의 연도를 입력하세요 : ";
        cin >> year;
    }while(year <= 1582);
    return year;
}

bool process(int year){
    bool criteria1 = (year % 4 ==0);
    bool criteria2 = (year %100 !=0) || (year%400 == 0);
    return(criteria1) && (criteria2);
}

void output(int year, bool result){
    if(result){
        cout << year << "년은 윤년 입니다.";
    }else{
        cout << year << "년은 윤년이 아닙니다.";
    }
    return;
}
```

## 자료 전달
### 1. 값으로 전달
- 인수(argument)의 값이 복사되어서 매개변수(parameter)에 할당
- 호출되는 함수에서 인수를 변경하지 않게 할떄 사용(읽기 전용)
- 전달할 값의 크기가 작을때 적합

```cpp
//값으로 전달 확인하기
#include <iostream>
using namespace std;

void fun(int y); //함수 선언

int main(){
    int x = 10;
    fun(x);

    cout << "main함수 내부의 x = " << x << endl;
    return 0;
}

void fun(int y){
    y++;
    cout << "fun함수 내부의 y = " << y << endl;
    return;
}

/*
fun함수 내부의 y = 11
main함수 내부의 x = 10
*/
```

### 2. 참조로 전달
- 매개변수가 인수의 별칭이 된다.
- 호출되는 함수에서 매개변수 변경 시 원본 변경
- 스왑 등 구현에 최적
- 복사 불필요

```cpp
//참조로 전달 확인하기
#include <iostream>
using namespace std;

void fun(int& y); // & 기호 : y가 참조라는것을 나타냄
int main(){
    int  x = 10;
    fun(x);
    cout << "main 함수 내부의 x = " << x << endl;
    return 0;
}

void fun(int& y){
    y++;
    cout << "fun함수 내부의 y = " << y << endl;
    return;
}

/*
fun함수 내부의 y = 11
main함수 내부의 x = 11 -> y의 값이 바뀌면 x의 값도 바뀐다.
*/
```

```cpp
//변수 스왑
#include <iostream>
using namespace std;

void swap(int& first, int& second);

int main(){
    int first = 10;
    int second = 20;
    swap(first, second);
	
    cout << "mian함수의 first값 = " << first << endl;
    cout << "main 함수의 second 값 = " << second;
    return 0;
}

void swap(int& fst, int& snd){
    int temp = fst;
    fst = snd;
    snd = temp;
    return;
}
```

### 3. 포인터로 전달
- 인수로 메모리 주소 전달
- 매개변수를 사용 -> 인수의 메모리 위치에 접근
- 참조로 전달과 유사한 장점
- C언어의 문자열, 배열등 포인터 특성을 가진 자료에 사용

## 자료 리턴

### 1. 값으로 리턴
- 가장 일반적인 매커니즘
- 호출되는 함수에서 표현식 생성 후 리턴
- 값이 필요한 위치에 함수 활용
- ex) 리터럴 값 리턴

```cpp
//리터럴 값 리턴하기
#include <iostream>
using namespace std;

bool isEven(int y);

int main(){
    cout << boolalpha << isEven(5) << endl;
    cout << boolalpha << isEven(10);
    return 0;
}

bool isEven(int y){
    return((y%2)==0);
}
```

### 2. 참조로 리턴
- 크기가 큰 객체 리턴 시 복사 비용 절감
- 호출되는 함수에서 객체 생성 시 주의(함수 종료 후 객체 소멸)

```cpp
//점수를 기반으로 등급 계산
#include <iostream>
using namespace std;

int getScore();
char findGrade(int score);
void printResult(int score, char grade);

int main(){
    int score;
    char grade;

    score = getScore();
    grade = findGrade(score);
    printResult(score, grade);
    return 0;
}

int getScore(){
    int score;
    do{
        cout << "점수를 입력하세요 (0~100) : ";
        cin >> score;
    }while(score < 0 || score > 100);
    return score;
}

char findGrade(int score){
    char grade;
    if(score >= 90){
        grade = 'A';
    }
    else if(score >= 80){
        grade = 'B';
    }else if(score >= 70){
        grade = 'C';
    }else if(score >= 60){
        grade = 'D';
    }else{
        grade = 'F';
    }
    return grade;
}

void printResult(int score, char grade){
    cout << endl << "시험결과 : " << endl;
    cout << "점수 = " << score << "/100" << endl;
    cout << "등급  = " << grade << endl;
}
```

### 3. 포인터로 리턴
- 참조로 리턴과 효과와 메커니즘이 같지만 잘 사용 X

## 기본 매개변수
- 매개변수에 기본값 저장
- 일부 매개변수만 적용 시 오른쪽에 위치하는 매개변수에만 적용 가능

```cpp
//ex
double calcEarnings(double rate, double hours = 40.0);

//함수 호출
calcEarnings(payRate); //기본 매개변수 hours 는 명시된 대로 40.0으로 들어가서 계산됨
calcEarnings(payRate, hourWorked); //hourWorked는 40.0이 아닌 따로 명시된 값으로 변경됨 
```


```cpp
//기본 값 사용하기
#include <iostream>
using namespace std;

double calcEarnings(double rate, double hours = 40);

int main(){
    cout << "직원1의 임금 : " << calcEarnings(22.0) << endl;
    cout << "직원2의 임금 : " << calcEarnings(12.50, 18);
    return 0;
}

double calcEarnings(double rate, double hours){
    double pay;
    pay = hours * rate;
    return pay;
}
```

## 함수 오버로딩
- 이름이 같은 함수 2개 이상 정의 가능
- 조건 : 매개변수(자료형, 개수, 순서)가 달라야 함
- 함수 시그니처(function signature)
	- 매개변수들의 자료형과 조합으로 함수 구분
	- 리턴 자료형은 함수 시그니처에 포함 X
- ex_) `int max(int a, int b);` VS `double max(double a, double b);` => 오버로딩 가능
- ex_) `int get()` VS `double get()` => 오버로딩 불가능
- 매개면수만 다른 여러 max 함수 오버로딩 예시

```cpp
//함수 3개 오버로딩하기
#include <iostream>
using namespace std;

int max(int num1, int num2);
int max(int num1, int num2, int num3);
int max(int num1, int num2, int num3, int num4);

int main(){
    cout << "maximum(5,7) = " << max(5,7) << endl;
    cout << "maximum(7,9,8) = " << max(7,9,8) << endl;
    cout << "maximum(14,4,12,11) = " << max(14,3,12,11);
    return 0;
}

int max(int num1, int num2){
    int larger;
    if(num1 >= num2){
        larger = num1;
    }else{
        larger = num2;
    }
    return larger;
}

int max(int num1, int num2, int num3){
    return max(max(num1, num2), num3);
}

int max(int num1, int num2, int num3 , int num4){
    return max(max(num1, num2, num3), num4);
}
```

## 함수의 사용범위와 유지 기간
- 스코프 : 엔티티(상수, 변수, 객체 , 함수 등)를 사용할수 있는 범위

### 1. 지역 스코프
- 선언된 위치부터 블록 끝까지 유효
- 블록 내 동일 이름 엔티티 2개 불가(컴파일 오류)

```cpp
int calculate(int num){
	int num = 0; // 오류 발생
}
```

- 스코프 겹침(셰도잉) : 중첩 블록에서 외부 변수 가림
	- 스코프 바깥에 있는 동일한 이름의 변수가 있어도 스코프 내에서는 정상 작동함.
	- 바깥에 있는 변수값은 반영 X

```cpp
//지역 스코프의 셰도잉
#include <iostream>
using namespace std;

int main(){
    int sum = 5;
    cout << sum << endl;
    {
        int sum = 3;
        cout << sum << endl;
    }
    cout << sum << endl;
    return 0;
}
/* 결과
5
3
5
*/
```
### 2. 전역 스코프
- 프로그램 전체에서 접근 가능
- 셰도잉 : 지역 변수가 전역 변수 가림
- 범위 해결 연산자 ('::') : 전역 엔티티에 명시적으로 접근

```cpp
//전역스코프의 셰도잉
#include <iostream>
using namespace std;

int num = 5;
int main(){
    cout << num << endl;
    int num = 25;
    cout << num;
    return 0;
}
/*
5
25
*/
```

```cpp
//범위 해결 연산자 사용하기
#include <iostream>
using namespace std;

int num = 5;
int main(){
    int num = 25;
    cout << "전역변수 num의 값 = " << :: num << endl;
    cout << "지역 변수 num의 값 = " << num << endl;
    return 0;
}
/*
전역 변수 num의 값 = 5
지역변수 num의 값 = 25
*/
```

### 3. 함수 이름의 스코프
- 선언 시점부터 프로그램 마지막 부분까지

### 4. 함수 매개변수의 스코프
- 함수 헤더부터 함수 블록 종료까지

### 5. 수명

#### 1. 자동 지역변수(atomatic local variable)
- 대부분 함수 내부의 모든 지역 변수들
	- 함수 호출 시 생성
	- 함수 종료 시 소멸

#### 2. 정적 지역 변수(static local variable)
- static 변경자 앞에 붙여서 생성
- 프로그램 종료시까지 유지
- 한번만 초기화, 모든 함수가 같은 변수 공유

```cpp
//정적 지역변수 확인하기
#include <iostream>
using namespace std;

void fun();
int main(){
    fun();
    fun();
    fun();
    return 0;
}

void fun(){
    static int count  = 0;
    count ++;
    cout << "count = " << count << endl;
}
/*
count = 1
count = 2
count  = 3
*/
```


### 6. 초기화 비교
- 자동 지역 변수 : 초기화 안하면 쓰레기 값
- 전역 변수 , 정적 지역 변수 : 초기화 안 하면 기본값(0,0.0, false)

```cpp
//3가지 종류의 변수를 초기화 하지 않은 경우의 값
#include <iostream>
using namespace std;

int global;
int main(){
    static int sLocal;
    int aLocal;

    cout << "전역변수 = " << global << endl;
    cout << "정적 지역 변수 = " << sLocal << endl;
    cout << "자동 지역 변수 = " << aLocal << endl;
}
/*
전역변수 = 0
지역 변수 = 0
자동 지역 변수 =  2034912 //쓰레기값
*/
```



---

# 연습문제 
1. 다음 함수들을 실행할수 있는 짧은 프로그램을 작성하세요
	a. abs(25) 와 abs(-23)
	b. floor(44.56)과 floor(-23.78)
	c.ceil(25.33)과 ceil(-2.89)

```cpp
int main(){
    cout << "abs(25) = " << abs(25) << endl;
    cout << "abs(-23) = "  << abs(-23) << endl;
    cout << "floor(44.56) = " << floor(44.56) << endl;
    cout << "floor(-23.78) = " << floor(-23.78) << endl;
    cout << "ceil(25.33) = " << ceil(25.33) << endl;
    cout << "ceil(-2.89) = " << ceil(-2.89) << endl;
}
/* 결과 : 
abs(25) = 25
abs(-23) = 23
floor(44.56) = 44
floor(-23.78) = -24
ceil(25.33) = 26
ceil(-2.89) = -2
*/
```

2. 다음 함수들을 실행할수 있는 짧은 프로그램을 작성하세요
	a. pow(5.0, 3)과 pow(5,-3)
	b. sqrt(44.56)
	c. exp(-6.2)와 exp(44.26)
	d. log(16.2)와 log10(14.24

```cpp
#include <iostream>
#include <cmath>
using namespace std;
int main(){
    cout << "pow(5.0, 3) = " << pow(5.0, 3) << endl;
    cout << "pow(5,-3) = " << pow(5,-3) << endl;
    cout << "sqrt(44.56) = " << sqrt(44.56) << endl;
    cout << "exp(-6.2) = " << exp(-6.2) << endl;
    cout << "exp(44.26) = " << exp(44.26) << endl;
    cout << "log(16.2) = " << log(16.2) << endl;
}
/* 결과
pow(5.0, 3) = 125
pow(5,-3) = 0.008
sqrt(44.56) = 6.67533
exp(-6.2) = 0.00202943
exp(44.26) = 1.66676e+19
log(16.2) = 2.78501
*/
```

3. 다음 함수들을 실행할수 있는 짧은 프로그램을 작성하세요
	a.sin(0)과 sin(PI)
	b. cos(0)과 cos(PI)
	c. tan(0)과 tan(1)
	d.asin(0)과 asin(1)
	e.acos(0)과 asin(1)
	f.atan(0)과 atan(1)

```cpp
#include<iostream>
#include <cmath>
using namespace std;

int main(){
    const double PI = 3.141592653589793238462;
    cout << "sin(0) = " << sin(0) << endl;
    cout << "sin(PI) = " << sin(PI) << endl;
    cout << "cos(0) = " << cos(0) << endl;
    cout << "cos(PI) = " << cos(PI) << endl;
    cout << "tan(0) = " << tan(0) << endl;
    cout << "tan(1) = " << tan(1) << endl;
    cout << "asin(0) = " << asin(0) << endl;
    cout << "asin(1) = " << asin(1) << endl;
    cout << "acos(0) = " << acos(0) << endl;
    cout << "acos(1) = " << acos(1) << endl;
    cout << "atan(0) = " << atan(0) << endl;
    cout << "atan(1) = " << atan(1) << endl;
}
/* 결과
sin(0) = 0
sin(PI) = 1.22465e-16
cos(0) = 1
cos(PI) = -1
tan(0) = 0
tan(1) = 1.55741
asin(0) = 0
asin(1) = 1.5708
acos(0) = 1.5708
acos(1) = 0
atan(0) = 0
atan(1) = 0.785398
*/
```

4. round 함수의 동작을 확인하는 프로그램
	23.2 => 23
	23.8 => 24
	-23.2 => 23
	-23.8 => -24
로 만드세요

```cpp
#include <iostream>
#include <cmath>
using namespace std;

int  main(){
    cout << "23.2 => " << abs(23.2) << endl;
    cout << "23.8 => " << ceil(23.8) << endl;
    cout << "-23.2 => " << floor(abs(-23.2)) << endl;
    cout << "-23.8 => " << floor(-23.8) << endl;
}
```

