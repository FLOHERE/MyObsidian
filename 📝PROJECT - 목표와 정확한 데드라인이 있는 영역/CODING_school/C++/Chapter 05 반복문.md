```CPP
//while 반복문으로 특정 수만큼 반복하기 1
#include <iostream>
using namespace std;

int main(){
    int counter = 0;

    while(counter <10){
        cout << "Hello world" << endl;
        counter++;
    }
    return 0;
}
```

```CPP
//while 반복문으로 특정 수만큼 반복하기
#include <iostream>
#include <iomanip>
using namespace std;

int main(){
    int score;
    int sum = 0;
    double average;

    int counter = 0;
    while(counter < 4){
        cout << "정수를 하나 입력하세요(0~100) : ";
        cin >> score;
        sum = sum + score;
        counter++;
    }
    average = static_cast <double>(sum) / 4;
    cout << fixed << setprecision(2) << showpoint;
    cout << "평균 점수 : " << average;
}
```

```CPP

```