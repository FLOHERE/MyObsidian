

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

