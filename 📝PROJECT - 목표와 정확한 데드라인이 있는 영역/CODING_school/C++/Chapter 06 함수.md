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

```cpp

```