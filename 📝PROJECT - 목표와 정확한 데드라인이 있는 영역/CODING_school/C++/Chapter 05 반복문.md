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
//정수 0~n-1까지 반복문으로 출력하기
#include <iostream>
using namespace std;

int main(){
    int n, count;
    cout << "출력할 정수를 입력 하세요 : ";
    cin >> n;

    count = 0;
    while(count < n){
        cout << count << endl;
        count ++;
    }
    return 0;
}
```

```CPP
//while 반복문으로 수열의 합 구하기
#include <iostream>
using namespace std;

int main(){
    int sum1 = 0, sum2 = 0, sum3 = 0;
    int n;
    cout << "n의 값 입력 : ";
    cin >> n;

    int counter = 1;
    while(counter <= n){
        sum1 += counter;
        sum2 += counter * counter;
        sum3 += counter * counter *counter;
        counter++;
    }
    cout << "n의 값 : " << n << endl;
    cout << "sum1의 값 : " << sum1 << endl;
    cout << "sum2의 값 : " << sum2 << endl;
    cout << "sum3의 값 : " << sum3 << endl;
    return 0;
}
```

```CPP
//센티넬 제어 반복문으로 입력한 수의 합 구하기
//센티넬 : 처리 중지를 나타내기 위해 데이터 리스트에 존재하는 특별한 항목
#include <iostream>
using namespace std;

int main(){
    int sum = 0;
    int num;

    cout << "정수를 입력하세요 (종료하려면 -1 입력) : ";
    cin >> num;
    while(num != -1){
        sum = sum + num;
        cout << "정수를 입력하세요 (종료하려면 -1) : ";
        cin >> num;
    }
    cout << "합 = " << sum;
    return 0;
}
```

```CPP
//EOF 제어 반복문으로 숫자의 합 구하기
//EOF : Ctrl + z or Ctrl + d 
#include <iostream>
using namespace std;

int main(){
    int sum = 0;
    int num;

    cout << "첫번째 숫자를 입력하세요(종료 : EOF 입력) : ";
    while(cin>>num){
        sum = sum + num;
        cout << "다음 숫자를 입력하세요 : ";
    }
    cout << "합 = " << sum;
    return 0;
}
```

```CPP
//파일의 EOF 사용하여 숫자의 합 구하기 - 파일 열어서 값 더하기
#include <iostream>
#include <fstream>
using namespace std;

int main(){
    int sum = 0;
    int num;
    ifstream infile;
    infile.open("numbers.dat");
    
    while(infile >> num){
        sum = sum + num;
    }

    cout << "합 = " << sum;
    infile.close();
    return 0;
}
```

```CPP
// 플래그 사용하기
#include <iostream>
#include <fstream>
using namespace std;

int main(){
    ifstream infile;
    int num;
    bool flag;

    infile.open("numbers.dat");

    flag = false;
    while(infile >> num && !flag){ 
    // 1. flag가 false이므로 !flag == true → 반복 시작
	// 3. flag가 true로 바뀌면 !flag == false → 반복 종료
        if(num>=150){
            cout << "찾는 숫자 = " << num;
            flag = true; //2. 조건 만족 → 찾음 → flag를 true로 설정
        }
    }
    if(!flag){ //반복이 끝난 후에도 flag가 false면 (즉, 조건 만족 못했으면)
        cout << "찾는 숫자가 파일에 존재하지 않습니다.";
    }
    infile.close();
    return 0;

}
```

```CPP
// for 반복문으로 0~n-1 까지 출력하기
#include <iostream>
using namespace std;

int main(){
    int n;
    cout << "출력할 정수 입력하세요 : ";
    cin >> n;

    for(int counter = 0; counter < n; counter++){
        cout << counter << " ";
    }
    return 0;
}
```

```CPP
//7로 나눌수 잇는 숫자 출력하기
#include <iostream>
#include <iomanip>
using namespace std;

int main(){
    int lower = 1;
    int higher = 300;
    int divisor = 7;
    int col = 1;

    for(int i = lower; i < higher; i++){
        if(i % divisor == 0){
            cout << setw(4) << i; //공백 4칸
            col++;
            if(col > 10){ // 10개 출력했으면 줄 바꿈
                cout << endl;
                col = 1;// 다시 처음부터 셈
            }
        }
    }
    return 0;
}
```

```CPP
//한달을  달력 형태로 출력하기
#include <iostream>
#include <iomanip>
using namespace std;

int main(){
    int startDay;
    int daysInMonth;
    int col = 1;

    do{
        cout << "한달의 날짜 수를 입력하세요(28,29,30,31) : ";
        cin >> daysInMonth;
    }while (daysInMonth < 28 || daysInMonth > 31);
    do{
        cout << "첫날의 요일을 입력하세요 (0~6): ";
        cin >> startDay;
    }while(startDay < 0 || startDay > 6);

    cout << endl;
    cout << "Sun Mon Tue Wed Thr Fri Sat" << endl;
    cout << "--- --- --- --- --- --- ---" << endl;

    for(int space = 0; space < startDay; space++){
        cout << "    ";
        col++;
    }

    for(int day = 1; day <=daysInMonth; day++){
        cout << setw(3) << day << " ";
        col++;

        if(col > 7){
            cout << endl;
            col = 1;
        }
    }
    return 0;
}
```

```CPP
//음수가 아닌 정수에서 가장 왼쪽의 숫자 추출하기
#include <iostream>
using namespace std;

int main(){
    int num;
    short leftDigit;

    cout << "음수가 아닌 정수를 입력하세요 : ";
    cin >> num;

    do{
        leftDigit = num %10; // 1%10이면 나머지가 1...
        num = num / 10;
    }while(num > 0);

    cout << "가장 왼쪽의 숫자 : " << leftDigit << endl;
    return 0;
}

/*  
1. do {} 안의 코드를 먼저 실행
2. while (조건)을 확인  
- 조건이 true면 → do 다시 실행 (반복)
- 조건이 false면 → 종료
*/
```

```CPP
//유효성 검사에 do - while 반복문 사용하기
#include <iostream>
using namespace std;

int main(){
    int score;
    char grade;

    do{
        cout << "0~100의 범위에 있는 점수 입력 : ";
        cin >> score;
    }while(score < 0 || score > 100);

    switch(score / 10){
        case 10 : grade = 'A';
            break;
        case 9 : grade = 'A';
            break;
        case 8 : grade = 'B';
            break;
        case 7 : grade = 'C';
            break;
        case 6 : grade = 'D';
            break;
        default : grade = 'F';
    }

    cout << "학점 = " << grade << endl;
    return 0;
}
```

```CPP
//반복문을 중첩

#include <iostream>
using namespace std;

int main(){
    int rows; //열
    int cols; //행

    cout << "행의 수를 입력하세요 : ";
    cin >> rows;
    cout << "열의 수를 입력하세요 : ";
    cin >> cols;

    for(int count1 = 1; count1 <= rows; count1++){
        for(int count2 = 1; count2 <= cols; count2++){
            cout << "*";
        }
        cout << endl;
    }
    return 0;
}
```

```CPP
// 숫자 패턴 출력하기
#include <iostream>
using namespace std;

int main(){
    int rows;
    int cols;

    cout << "행의 수를 입력하세요 : ";
    cin >> rows;
    cout << "열의 수를 입력하세요 : ";
    cin >> cols;

    for(int i = 1; i <= rows; i++){
        for(int j = i; j <= i + cols -1; j++){
            cout << j << " ";
        }
        cout << endl;
    }
    return 0;
}
```

```CPP
//곱셈 표 만들기
#include<iostream>
#include<iomanip>
using namespace std;

int main(){
    int size;

    do{
        cout << "표의 크기를 입력하세요 (2~10): " << endl;
        cin >> size;
    }while(size < 2 || size > 10);

    for(int i = 1; i <= size; i++){
        for(int j = 1; j<=size; j++){
            cout << setw(4) << i * j;
        }
        cout << endl;
    }
    return 0;
}
```

```CPP
// 소수인지 확인하는 프로그램
#include <iostream>
using namespace std;

int main(){
    int num;

    do{
        cout << "양의 정수를 입력하세요 : ";
        cin >> num;
    }while(num <= 0);

    if(num == 1){
        cout << "1은 소수도 합성수도 아닙니다. ";
        return 0;
    }
    for(int i = 2; i<num; i++){
        if(num % i == 0){
            cout << num << " 은/는 합성수 입니다." << endl;
            cout << i << " 로/으로 나누어집니다." << endl;
            return 0;
        }
    }
    cout << num << " 은/는 소수입니다. " << endl;
    return 0;
}
```


---

# 연습문제 코드 모음집

```CPP
//사용자의 패턴의 종류(1~4)와 크기 (1~9)를 입력받고 다음과 같은 출력을 하는 프로그램을 만드세요
#include <iostream>
using namespace std;

int main(){
    int type, size;

    cout << "패턴 종류(1~4) : ";
    cin >> type;
    cout << "크기(1~9) : ";
    cin >> size;

    char star = '*';
    char space = ' ';

    if(type==1){
        cout << "<<Type1>>" << endl;
        for(int i = 0; i < size; i++){
            for(int j = 0; j < i; j++){
                cout << star;
            }   
            cout << star << endl;
        }

    }

    if(type==2){
        cout << "<<Type2>>" << endl;
        for(int i = size; i > 0; i--){
            for(int j = i; j-1>0 ; j--){
                cout << star;
            }
            cout << star << endl;
        }
    }

    if(type==3){
        cout << "<<Type3>>" << endl;
        for(int i = 0; i<size; i++ ){
            for(int j = 0; j < i; j++){
                cout << space;
            }
            for(int k = 0; k < (size-1)-i; k++){
                cout << star;
            }
            cout << star << endl;
        }
    }

    if(type==4){
        cout << "<<Type4>>" << endl;
        for(int i = size; i > 0; i--){
            for(int j = 0; j < i-1; j++){
                cout << space;
            }
            for(int k = 0; k < (size+1)-i; k++){
                cout << star;
            }
            cout << space << endl;
        }
    }
}
```

Type 1 : 

```
패턴 종류(1~4) : 1
크기(1~9) : 4
<<Type1>>
*
**
***
****
```

Type 2 :

```
패턴 종류(1~4) : 2
크기(1~9) : 4
<<Type2>>
****
***
**
*
```

Type 3 :

```
패턴 종류(1~4) : 3
크기(1~9) : 4
<<Type3>>
****
 ***
  **
   *
```

Type 4:

```
패턴 종류(1~4) : 4
크기(1~9) : 4
<<Type4>>
   * 
  ** 
 *** 
**** 
```


```CPP
// 사용자로부터 패턴의 종류와 크기(줄 수)를 입력받고 다음과 같은 패턴을 출력하는 프로그램을 만드세요
#include <iostream>
using namespace std;

int main(){
    int type,size;
    cout << "패턴의 종류(1,2) : ";
    cin >> type;
    cout << "크기(줄 수) : ";
    cin >> size;

    if(type==1){ //역삼각형
        for(int i = 0; i < size; i++){
            for(int j = 0; j < i; j++){
                cout << " ";
            }
            for(int k = i*2; k < (size*2)-1; k++){
                cout << "*";
            }
            cout << "\n";
        }   
    }else{
        for(int i = 0; i < size; i++){
            for(int j = i; j < size; j++){
                cout << " ";
            }
            for(int k = 0; k<i*2+1; k++){
                cout << "*";
            }
            cout << "\n";
        }
    }
}
```

1번 패턴 : 

```
패턴의 종류(1,2) : 1
크기(줄 수) : 4
*******
 *****
  ***
   *

```

2번 패턴 : 

```
패턴의 종류(1,2) : 2
크기(줄 수) : 4
.   *
   ***
  *****
 *******
```

```CPP
//1000보다 작은 숫자들을 키보드로 읽어들인 후 그 합과 평균을 구하는 프로그램을 만드세요.입력은 1000이라는 센티넬을 만날때 정지 합니다.
#include <iostream>
using namespace std;

int main(){
    int count = 0;
    int num = 0;
    int sum = 0;
    
    while(true){
        cout << "1000 이하의 숫자 입력 : ";
        cin >> num;

        if(num < 1000){
            sum += num;
            count++;
        }else{
            break;
        }
    }
    cout << "합 : " << sum << endl;
    cout << "평균 : " <<(sum/count) << endl;
}
```

```
1000 이하의 숫자 입력 : 22
1000 이하의 숫자 입력 : 456
1000 이하의 숫자 입력 : 993
1000 이하의 숫자 입력 : 340
1000 이하의 숫자 입력 : 1000
합 : 1811
평균 : 452
```

```CPP
//0을 센티넬로 사용해서 사용자로부터 양의 정수와 음의 정수 리스트를 읽어오는 프로그램을 만드세요. 양의 정수가 몇개 입력되었는지, 음의 정수가 몇개 입력되었는지 출력합니다.
#include <iostream>
using namespace std;

int main(){
    int num = 1;
    int Pcount = 0;
    int Mcount = 0;
    int n = 0;

    int plus[100];
    int minus[100];

    while(num!=0){
        cout << "양의 정수 혹은 음의 정수 입력(0입력시 종료) : ";
        cin >> num;
        if(num > 0){
            plus[n] = num;
            Pcount++;
            n++;
            
        }else if(num < 0){
            minus[n] = num;
            Mcount++;
            n++;
            
        }
    }
    cout << "총 입력된 양의 정수 : " << Pcount << endl;
    cout << "총 입력된 음의 정수 : " << Mcount << endl;
 
}
```

```CPP
//사용자에게 두 양의 정수를 입력받고 두 정수를 범위로 내부에 있는 홀수와 짝수를 출력하는 프로그램을 만드세요
#include <iostream>
using namespace std;

int main(){
    int num1 = 0;
    int num2 = 0;
    int result = 0;

    cout << "범위 1 : ";
    cin >> num1;
    cout << "범위 2 : ";
    cin >> num2;
    
    for(int i = num1; i<num2; i++){
        result = i;
        if(result%2==0){
            cout << "짝수 : " << result << endl;
        }else{
            cout << "홀수 : " << result << endl;
        }
    }
}
```

```
범위 1 : 3
범위 2 : 23
홀수 : 3
짝수 : 4
홀수 : 5
짝수 : 6
홀수 : 7
짝수 : 8
홀수 : 9
짝수 : 10
홀수 : 11
짝수 : 12
홀수 : 13
짝수 : 14
홀수 : 15
짝수 : 16
홀수 : 17
짝수 : 18
홀수 : 19
짝수 : 20
홀수 : 21
짝수 : 22

```

```CPP
//1~100의 범위에 있는 정수 중 7로 나눌수 있는 숫자들을 출력하세요
#include<iostream>
using namespace std;

int main(){
    for(int i = 1; i<=100; i++){
        if(i%7==0){
            cout << i << " / ";
        }
    }
}
```

```CPP
//1~100의 범위에 있는 정수 중에서 5와 7로 동시에 나눌수 있는 숫자들을 출력하세요.
#include<iostream>
using namespace std;

int main(){
    for(int i = 1; i<=100; i++){
       if(i%5==0 && i%7==0){
            cout << i << " / ";
       } 
    }
}
```

