```CPP
//리터럴 표현식을 몇가지 보여주는 프로그램

#include <iostream>
using namespace std;

int main(){
    cout << false << " " << 'A' << "Hello" << endl;
    cout << 23412 << " " << 12897234L << endl;
    cout << 245.78F << " " << 114.782 << " " << 2.051L;
}
```

```CPP
//괄효 표현식을 몇가지 보여주는 프로그램

#include <iostream>
using namespace std;

int main(){
    int x = 4;
    
    cout << "괄호가 있는 경우 : " << (x+3) *5 << endl;
    cout << "괄호가 없는 경우 : " << x + 3 *5 << endl;
}
```

```CPP
//덧셈 뺄셈 표현식을 몇가지 보여주는 프로그램

#include <iostream>
using namespace std;

int main(){
    int x = 4; 
    int y = -10;

    cout << "x에 양수 연산자 적용하기 : " << +x <<endl;
    cout << "x에 음수 연산자 적용하기 : " << -x <<endl;

    cout << "y에 양수 연산자 적용하기 : " << +y <<endl;
    cout << "y에 음수 연산자 적용하기 : " << -y << endl;

    return 0;
}
```

```CPP
#include <iostream>
using namespace std;

int main(){
    cout << "곱셈 연산자 확인하기" << endl;
    cout << "3*4 = " << 3*4 << endl;
    cout << "2.4*4.1 = " << 2.4*4.1 << endl;
    cout << "-3 *4 = " << -3 *4 << endl;

    cout << "나눗셈 연산자 확인하기" << endl;
    cout << "30/5 = " << 30/5 << endl;
    cout << "4/7 = " << 4/7 << endl;

    cout << "나머지 연산자 확인하기" << endl;
    cout << "30%5 = " << 30%5 << endl;
    cout << "30%4 = " << 30%4 << endl;

    return 0;
}
```

```CPP
//덧셈 뺄셈 표현식 확인하기
#include <iostream>
using namespace std;

int main(){
    cout << "Some addition operations" << endl;
    cout << "Value fo 30+5 = " << 30+5 << endl;
    cout << "Somesubtraction operations" << endl;
    cout << "Value of 5 - 30 = " << 5 - 30 << endl;
    cout << "Value of 51.2 - 30.4" << 51.2 - 30.4 << endl;
    return 0;
}
```

```CPP
//단순할당 연산자 예제

#include <iostream>
using namespace std;

int main(){
    int x;
    int y;

    cout << "Return value of assignment expression : " << (x = 14) << endl;
    cout << "Value of variable x : " << x << endl;

    cout << "Return value of assignment expression : " << (y = 87) << endl;
    cout << "Value of variable y : " << y;
}
```

```CPP
//복합 할당 예제
#include <iostream>
using namespace std;

int main(){
    int x = 20;
    int y = 30;
    int z = 40;
    int t = 50;
    int u = 60;

    x += 5;
    y -= 3;
    z *= 10;
    t /= 8;
    u %= 7;

    cout << "Value of x : " << x << endl;
    cout << "Value of y : " << y << endl;
    cout << "Value of z : " << z << endl;
    cout << "Value of t : "  << t << endl;
    cout << "Value of u : " << u << endl;
    return 0; 
}
```

```CPP
// 암묵적 자료형 승격 예제
#include <iostream>
#include <typeinfo>
using namespace std;

int main(){
    bool x = true;
    char y = 'A';
    short z = 14;
    float t = 24.5;

    cout << "Type of x + 100 : " << typeid (x + 100).name() << endl; //int type
    cout << "Value of x + 100 : " << x + 100 << endl;

    cout << "Type of y + 1000 : " << typeid (y+1000).name() << endl; // int type
    cout << "Value of y + 1000 : " << y + 1000 << endl;

    cout << "Type of z * 100 : " << typeid (z *100).name() << endl; //int type
    cout << "Value of z * 100 : " << z * 100 << endl;

    cout << "Type of t + 15000.2 : " << typeid (t +15000.2).name() << endl; //double
    cout << "Value of t + 15000.2 : " << t + 15000.2;
    return 0;
}
```

```CPP
// 암묵적 자료형 변환 (부가 작용 없음)
#include <iostream>
#include <typeinfo>
using namespace std;

int main(){
    int x = 123;
    long y = 140;
    double z = 114.56;

    cout << "Type of x +y : " << typeid (x+y).name() << endl; //long type
    cout << "Value of x +y : " <<  x+y << endl << endl;

    cout << "Type of x + y + z : " << typeid(x+y+z).name() << endl; // double type
    cout << "Value of x +y +z : " << x + y+ z << endl;  
}
```

```CPP
//암묵적 자료형 변환(부가작용X)
#include <iostream>
#include <typeinfo>
using namespace std;

int main(){
    int x;
    double y;

    x = 23.67;
    y = 130;

    cout << "Type of x = 23.67 : " << typeid (x = 23.67).name() << endl; //type int
    cout << "Value of after assignment : " << x << endl << endl; //23 -> 소수점 뒷자리는 짤림(값 유실)

    cout << "Type of y = 130 : " << typeid(y=130).name() << endl;
    cout << "Value of y after assignment : " << y << endl;
    return 0;
}
```

```CPP
// 명시적 자료형 반환 예제
#include <iostream>
using namespace std;

int main(){
    double x = 23.56;
    int y = 30;
    cout << "Without casting : " << x + y << endl; // (>> 53.56)
    cout << "With casting : " << static_cast<int> (x) + y; //double -> int (>> 53)
    return 0;
}
```

```CPP
//단순 표현식의 평가 예제
#include <iostream>
using namespace std;

int main(){
    cout << "Result of expresstion : " << 5+7*4 << endl;
    return 0;
}
```

```CPP
// 복잡한 표현식의 평가 예제
#include <iostream>
using namespace std;

int main(){
    int result;
    result = 5-15 %4;
    cout << "The value stored in result : " << result;
    return 0;
}
```

```CPP
// 괄호를 가진 간단한 표현식 예제
#include <iostream>
using namespace std;

int main(){
    int x = 5;
    cout << "Value of (x+6) * 7 : " << (x+6)*7;
    return 0;
}
```

```CPP
// 부가효과를 가진 표현식 예제

#include <iostream>
using namespace std;

int main(){
    int x = 8;
    int y = 10;

    y *= x + 5; //답 : 130
    cout << "Value of y : " << y;
    return 0;
}
```


```CPP
//우선 순위와 결합 방향 예제
#include <iostream>
using namespace std;

int main(){
    cout << "Value of expression : " << 5 - 30 / 4 * 8 + 10; // -41
    return 0;
}
```

```CPP
// 같은 우선순위를 갖는 표현식들 예제
#include <iostream>
using  namespace std;

int main(){
    int x = 10;
    int y = 20;

    y += x *= 40; // 여기서도 마찬가지로 곱셈이 먼저다.
    cout << "Value of x : " << x << endl; // 400
    cout << "Value of y : " << y << endl; // 420
    return 0;
}
```

```CPP
// unsigned int 자료형의 오버플로우와 언더플로우 예제
#include <iostream>
#include <limits>
using namespace std;

int main(){
    unsigned int num1 = numeric_limits <unsigned int> :: max();
    unsigned int num2 = numeric_limits <unsigned int> :: min();

    cout << "The value of maximum unsigned int : " << num1<< endl;
    cout << "The value of minimum unsigned int : " << num2 << endl;

    num1 += 1;
    num2 -= 1;

    cout << "The value of num1 +1 after overflow : " << num1 << endl;
    cout << "The value of num2 -1 after under flow : "<< num2 << endl;
}
/* 결과 :
The value of maximum unsigned int : 4294967295
The value of minimum unsigned int : 0
The value of num1 +1 after overflow : 0
The value of num2 -1 after under flow : 4294967295 
*/
```

```CPP
// int 자료형의 오버플로우와 언더플로우 예제
#include <iostream>
#include <limits>
using namespace std;

int main(){
    int num1 = numeric_limits <int> :: max();
    int num2 = numeric_limits <int> :: min();
    
    cout << "Value of maximum signed int : " << num1 << endl;
    cout << "Value of minimum  signed int : " << num2 << endl;

    num1 += 1;
    num2 -= 1;

    cout<< "The value of num1 + 1 after overflow : " << num1 << endl;
    cout << "The value of num2 -1 after underflow : " << num2 << endl;
    return 0;
}
/* 결과 : 
Value of maximum signed int : 2147483647
Value of minimum  signed int : -2147483648
The value of num1 + 1 after overflow : -2147483648
The value of num2 -1 after underflow : 2147483647
*/
```

```CPP
//double 자료형의 오버플로우와 언더플로우
#include <iostream>
#include <limits>
using namespace std;

int main(){
    double num1 = +numeric_limits <double> :: max();
    double num2 = -numeric_limits <double> :: max();

    cout << "The value of maximum double : " << num1 << endl;
    cout << "the value of minimum double : " << num2 << endl;

    num1 *= 1000.00;
    num2 *= 1000.00;

    cout << "The value of num1 * 1000 after overflow : " << num1 << endl;
    cout << "the value of num2 * 1000 after underflow : " << num2 << endl;
    return 0;
}
/* 결과 : 
The value of maximum double : 1.79769e+308
the value of minimum double : -1.79769e+308
The value of num1 * 1000 after overflow : inf
the value of num2 * 1000 after underflow : -inf
*/
```


```CPP
// boolalpha 조정자 사용하기
#include <iostream>
using namespace std;

int main(){
    bool x = true;
    bool y = false;

    cout << "Value of x using default : " << x << endl;
    cout << "Value of y using default : " << y << endl;

    cout << "Value of x using mainpulator : " << boolalpha << x << endl; //boolalpha : boolean 값을 True, False로 나타나게 해줌(원래는 1,0으로 나타남)
    cout << "Value of y : " << y;
    return 0;
}
/* 결과 : 
Value of x using default : 1
Value of y using default : 0
Value of x using mainpulator : true
Value of y : false
*/
```

```CPP
#include <iostream>
using namespace std;

int main(){
    int x = 1237;

    cout << "x  in decimal : " << x << endl;
    cout << "x in octal : " << oct << x << endl;
    cout << "x in hexadecimal : " << hex << x << endl;

    cout << "x in decimal : " << x << endl;
    cout << "x in octal : " << showbase << oct << x << endl; //showbase : 8진수인지, 16진수인지 앞에 표시해줌(0,0x)
    cout << "x in hexadecimal : " << showbase << hex << x;
    return 0;
}
/* 결과 : 
x  in decimal : 1237
x in octal : 2325
x in hexadecimal : 4d5
x in decimal : 4d5
x in octal : 02325
x in hexadecimal : 0x4d5
*/
```


```CPP
// 부동 소수점 조정자 사용하기
#include <iostream>
using namespace std;

int main(){
    double x = 1237;
    double y = 12376745.5623;

    cout << "x in fixed_point format : " << x << endl;
    cout << "x in fixed_point format : " << showpoint << x << endl; //소수점이 없어도 두자리까지 보여준다.

    cout << "y in scientific format : " << y << scientific;// 지수형식으로 보여줌
    return 0;
}
/* 결과 : 
x in fixed_point format : 1237
x in fixed_point format : 1237.00
y in scientific format : 1.23767e+07 => 123767 * 10^7
*/
```

```CPP
// 매개 변수가 있는 조정자
#include <iostream>
#include <iomanip>
using namespace std;

int main(){
    double x = 1237234.1235;

    cout << fixed << setprecision(2) << showpos << setfill('*');
    // fixed : 기본 소수점 6번째 자리까지 보여줌
    // setprecision(n) : 소수점 이하 n자리까지 고정
    // showpos : 양수에도 + 부호를 붙인다
    // setfill('') : 빈칸을 ‘ ’ 으로 채운다

    cout << setw(15) << left << x << endl; // setw(n) : 출력 너비 폭을 n칸으로 지정
    // left : 전체 데이터 왼쪽 정렬
    cout << setw(15) << internal << x << endl;
    // internal: 부호는 맨 왼쪽 , 숫자 값은 오른쪽으로 바짝 붙는다.가운데에 공간생김.
    cout << setw(15) << right << x;
    // right : 전체 데이터를 오른쪽 정렬
    return 0;
}
/* 결과 : 
+1237234.12****
+****1237234.12
****+1237234.12
*/
```

```CPP
//불 자료형으로 입력하기
#include <iostream>
using namespace std;

int main(){
    bool flag;
    cout << "Enter true or false for flag : ";
    cin >> boolalpha >> flag; // 입력할때는 True, False 였지만...

    cout << flag; // 출력할때는 boolalpha 안쓰면 그냥 0, 1 이렇게 나옴 ㅋㅋ;;
    return 0;
}
```

```CPP
//여러 진법으로 정수 입력 받기
#include <iostream>
using namespace std;

int main(){
    int num1, num2, num3;

    cout << "Enter the first number in decimal : ";
    cin >> num1;

    cout << "Enter the second number in octal : ";
    cin >> oct >> num2;

    cout << "Enter the third number in hexadicimal : ";
    cin >> hex >> num3;

    cout << num1 << endl;
    cout << num2 << endl;
    cout << num3;
    return 0;
}
/* 결과 : 
Enter the first number in decimal : 124
Enter the second number in octal : 76
Enter the third number in hexadicimal : 2ab
124
62
683
*/
```

```CPP
#include <iostream>
#include <iomanip>
using namespace std;

int main(){
    int first, second , third , sum;

    cout << "Enter the first integer : ";
    cin >> first;

    cout << "Enter the second integer : ";
    cin >> second;

    cout << "Enter the third integer : ";
    cin >> third;

    sum = first + second + third;
    cout << "The sum of the three integers is : " << sum;
    return 0;
}
/* 결과 : 
Enter the first integer : 99
Enter the second integer : 9487
Enter the third integer : 234
The sum of the three integers is : 9820
*/
```

```CPP
//숫자에서 정수 부분과 소수점 아래 부분을 분리해서 추출하는 프로그램
#include <iostream>
#include <iomanip>
using namespace std;

int main(){
    double number;
    int intPart;
    double fractPart;

    cout << "Enter a floating-point number : ";
    cin >> number;

    intPart = static_cast <int> (number); // 정수 부분 = 강제 타입 변환, double -> int
    fractPart = number - intPart; // (.~~)실수 부분 = double(실수 전체) - int(정수부분)

    cout << fixed << showpoint << setprecision(2); // showpoint : 소수점 뒷자리가 0아더라도 무조건 실수 형태로 보여주는것
    cout << "The original number : " << number << endl; // 입력한 실수
    cout << "the integral part : " << intPart << endl; // 정수부분
    cout << "the fractional part : " << fractPart; // 실수 부분
}
```


```CPP
// 정수의 첫번째 자릿수 추출하기
#include <iostream>
using namespace std;

int main(){
    unsigned int givenInt, firstDigit;

    cout << "Enter a positive integer : ";
    cin >> givenInt;

    firstDigit = givenInt % 10;

    cout << "Entered integer : " << givenInt << endl;
    cout << "Extracted first digit : " << firstDigit << endl;
    return 0;
}
/* 결과 : 
Enter a positive integer : 102
Entered integer : 102
Extracted first digit : 2
*/
```

```CPP
//초 단위의 시간을 시, 분, 초 단위로 나누어 변환하기
#include <iostream>
using namespace std;

int main(){
    unsigned long duration, hours, minutes, seconds;

    cout << "Enter a positive integer for the number of seconds : ";
    cin >> duration;

    hours = duration / 3600L;
    minutes = (duration - (hours * 3600L)) / 60L;
    seconds = duration - (hours * 3600L) - (minutes * 60);

    cout << "Given Duration in seconds : " << duration << endl;

    cout << "Result : ";
    cout << hours << "hours, ";
    cout << minutes << "minutes, and ";
    cout << seconds << " seconds. ";
}
/* 결과 : 
Enter a positive integer for the number of seconds : 120000
Given Duration in seconds : 120000
Result : 33hours, 20minutes, and 0 seconds
*/
```

```CPP
//총합, 평균, 분산 구하기
#include <iostream>
#include <iomanip>
using namespace std;

int main(){
    int num1, num2, num3;
    int sum;
    double average;
    double dev1, dev2, dev3;

    cout << "Enter the first integer : ";
    cin >> num1;
    cout << "Enter the second integer : ";
    cin >> num2;
    cout << "Enter the third integer : ";
    cin >> num3;

    sum = num1 + num2 + num3;
    average = static_cast <double> (sum) /3;
    dev1 = num1 - average;
    dev2 = num2 - average;
    dev3 = num3 - average;

    cout << fixed << setprecision (2) << showpos;
    cout << "Sum of three numbers : " << sum << endl;
    cout << "Average : " << setw(9) << average << endl;
    cout << "deviation of number 1: " << setw(9) << dev1 << endl;
    cout << "deviation of number 2: " << setw(9) << dev2 << endl;
    cout << "deviation of number 3: " << setw(9) << dev3 << endl;
    return 0;
}
/*결과 : 
Enter the first integer : 43
Enter the second integer : 22
Enter the third integer : 81
Sum of three numbers : +146
Average :    +48.67
deviation of number 1:     -5.67
deviation of number 2:    -26.67
deviation of number 3:    +32.33
*/
```

```CPP
//세금 구하기
#include <iostream>
#include<iomanip>
using namespace std;

int main(){
    const double TAXRATE = 8.5;

    int quantity;
    double unitPrice;
    double subTotal, tax, total;

    cout << "Enter the quantity of the items bought : ";
    cin >> quantity;
    cout << "Enter the unit price of the item : ";
    cin >> unitPrice;

    subTotal = quantity * unitPrice; // 세금 없는 ver.
    tax = subTotal * (TAXRATE / 100); // 세금 계산
    total = subTotal + tax; // 총 = 세금 없는 가격 + 세금

    cout << endl;
    cout << fixed << setprecision(2);
    cout << "Quantity : " << quantity << endl;
    cout << "Unit price :  " << unitPrice << endl;
    cout << "Subtotal : " << subTotal << endl;
    cout << "Tax : " << tax << endl;
    cout << "Total : " << total << endl;
}

/*
Enter the quantity of the items bought : 54
Enter the unit price of the item : 4700

Quantity : 54
Unit price :  4700.00
Subtotal : 253800.00
Tax : 21573.00
Total : 275373.00
*/
```

---

# 연습문제 코드 모음집

```CPP
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



```CPP
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

```CPP
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

```CPP
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

```CPP
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

```CPP
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

```CPP
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

```CPP
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


```CPP
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

