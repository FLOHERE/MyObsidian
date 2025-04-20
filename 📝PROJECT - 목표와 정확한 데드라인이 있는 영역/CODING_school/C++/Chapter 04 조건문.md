```CPP
//if 조건문 사용해서 절대값 계산, 출력
#include <iostream>
using namespace std;

int main(){
    int number;
    cout << "정수를 입력하세요 : ";
    cin >> number;

    if(number<0){
        number = -number;
    }

    cout << "입력한 숫자의 절대값 = " << number;
    return 0;
}
```

```CPP
//if 조건문 사용 -> 초과근무 시간이 있는 급여 계산
#include <iostream>
#include <iomanip> //얘는 뭐하는 라이브러리인교
using namespace std;

int main(){
    double hours;
    double rate;
    double regularPay;
    double overPay;
    double totalPay;

    cout<< "업무 시간을 입력하세요 : ";
    cin >> hours;
    cout << "시간당 급여를 입력하세요 : ";
    cin >> rate;

    regularPay = hours *rate;
    overPay = 0.0;
    if(hours > 40.0){
        overPay = (hours - 40.0) *rate * 0.03;
    }
    totalPay = regularPay + overPay;
    cout << fixed << showpoint;
    cout << "일반급여 = " << setprecision(2) << regularPay << endl;
    cout << "초과 근무에 대한 급여 : " << setprecision(2) << overPay << endl;
    cout << "전체 급여 = " << setprecision(2) << totalPay << endl;
    return 0;
}
```

```CPP
//if-else 조건문 사용으로 P/F 학점 찾기
#include <iostream>
using namespace std;

int main(){
    int score;
    cout << "0~100점 사이의 점수를 입력하세요 : ";
    cin >> score;

    if(score >= 70){
        cout << "pass 입니다." << endl;
    }else{
        cout << "fail입니다." << endl;
    }
    return 0;
}
```

```CPP
//더큰 숫자 또는 숫자가 같은 경우 첫번째 숫자 출력하는 if-else문
#include <iostream>
using namespace std;

int main(){
    int num1, num2;
    int larger;

    cout << "첫번째 숫자 입력 : ";
    cin >> num1;
    cout << "두번째 숫자 입력 : ";
    cin >> num2;

    if(num1>=num2){
        larger = num1;
    }else{
        larger = num2;
    }
    cout << "더 큰숫자 : " << larger;
    return 0;
}
```

```CPP
// 입력받은 숫자가 왼쪽이 더 큰지, 같은지, 작은지 출력
#include <iostream>
using namespace std;

int main(){
    int num1, num2;
    cout << "첫번째 숫자 입력 : ";
    cin >> num1;
    cout << "두번쨰 숫자 입력 : ";
    cin >> num2;

    if(num1 >= num2){
        if(num1 > num2){
            cout << num1 << ">" << num2;
        }else{
            cout << num1 << "==" << num2;
        }
    }else{
        cout << num1 << "<" << num2;
    }
}
```

```CPP
// 여러 방향 조건 분기를 사용해서 학점 구하는 프로그램
#include <iostream>
using namespace std;

int main(){
    int score;
    char grade;
    cout << "0~100점 사이의 점수 입력 : ";
    cin >> score;

    if(score >=90){
        grade = 'A';
    }else if(score >= 80){
        grade = 'B';
    }else if(score >= 70){
        grade = 'C';
    }else if(score >= 60){
        grade = 'D';
    }else{
        grade = 'F';
    }

    cout << "최종 학점 = " << grade;
    return 0;
}
```

```CPP
//자동차를 대여할수 있는 나이 범위를 확인하는 프로그램
#include <iostream>
using namespace std;

int main(){
    int age;
    bool eligible;

    cout<<"나이를 입력하세요 : ";
    cin >> age;

    eligible = (age>=25) && (age<=100);

    if(eligible){
        cout << "자동차 대여 가능";
    }else{
        cout << "죄송합니다. 자동차 대여 불가능 합니다.";
    }
    return 0;
}
```

```CPP
//특정한 온도 범위에 따라 에어컨을 난방 또는 냉방으로 가동
#include <iostream>
using namespace std;

int main(){
    int temperature;
    bool hot;
    bool cold;

    cout << "현재 온도를 입력하세요 : ";
    cin >> temperature;

    hot = temperature >=23;
    cold = temperature <= 15;

    if(hot||cold){
        cout << "에어컨이 켜집니다." << endl;
        if(hot){
            cout << "냉방 모드로 작동" << endl;
        }else{
            cout << "난방 모드로 작동" << endl;
        }
    }else{
        cout << "에어컨이 꺼집니다." << endl;
    }
    return 0;
}
```

```CPP
//세가지 조건을 확인하여 윤년을 찾는 프로그램
#include <iostream>
using namespace std;

int main(){
    int year;
    bool divBy400, divBy4, divBy100;
    bool leapYear;

    cout << "연도를 입력하세요 : ";
    cin >> year;

    divBy400 = ((year%400)==0);
    divBy4 = ((year%4)==0);
    divBy100 = ((year%100)==0);
    leapYear = (divBy400) || (divBy4 && !(divBy100));

    if(leapYear){
        cout << year << "년은 윤년 입니다." << endl;
    }else{
        cout << year << "년은 윤년이 아닙니다. " << endl;
    }
    return 0;
}
```

```CPP
//요일 출력하기
#include <iostream>
using namespace std;

int main(){
    int day;
    cout << "0~6범위의 정수를 입력하세요 : ";
    cin >> day;

    switch(day){
        case 0 : cout << "일요일" << endl;
        case 1 : cout << "월요일" << endl;
        case 2 : cout << "화요일" << endl;
        case 3 : cout << "수요일" << endl;
        case 4 : cout << "목요일" << endl;
        case 5 : cout << "금요일" << endl;
        case 6 : cout << "토요일" << endl;
    }
    return 0;
}
```

```CPP
//주어진 날짜의 요일 출력
#include <iostream>
using namespace std;

int main(){
    int day;
    cout << "0~6 범위의 정수 입력 : ";
    cin >> day;

    switch(day){
        case 0:cout << "일요일" << endl;
            cout << "한주의 첫번째 요일입니다." <<endl;
            break;
        case 1:cout << "월요일" << endl;
            break;
        case 2: cout << "화요일" << endl;
            break;
        case 3: cout << "수요일" << endl;
            break;
        case 4: cout << "목요일" << endl;
            break;
        case 5: cout << "금요일" << endl;
            break;
        case 6: cout << "토요일" << endl;
            cout << "한주의 마지막 요일입니다." << endl;
            break;  
    }
    return 0;
}
```

```CPP
#include <iostream>
using namespace std;

int main(){
    int score;
    char grade;

    cout << "0~100점 사이의 점수 입력 : ";
    cin >> score;

    switch(score/10){
        case 10: grade = 'A';
            break;
        case 9: grade = 'B';
            break;
        case 8: grade = 'C';
            break;
        case 7: grade = 'D';
            break;
        default:grade = 'F';
    }
    cout << "Score : " << score << endl;
    cout << "Grade : " << grade << endl;
    return 0;
}
```

```CPP
// 학점 기반 pass/fail 출력
#include <iostream>
using namespace std;

int main(){
    char grade;
    cout << "학점을 입력하세요(A,B,C,D,F) : ";
    cin >> grade;

    switch(grade){
        case 'A':
        case 'B':
        case 'C': cout << "pass입니다.";
            break;
        case 'D':
        case 'F': cout << "fail입니다.";
            break;
        default : cout << "입력 오류입니다. 다시 시도하세요.";
    }
    return 0;
}
```

```CPP
//두 숫자를 입력받은 뒤에 두 숫자 중 더 큰 숫자 또는 같을 경우 첫번째 숫자를 조건부 표현실으로 찾아 출력하기
#include <iostream>
using namespace std;

int main(){
    int num1, num2;
    int larger;

    cout << "첫번째 숫자 입력 : ";
    cin >> num1;
    cout << "두번쨰 숫자 입력 : ";
    cin >> num2;

    larger = num1 >= num2 ? num1: num2;

    cout << "더 큰 숫자 = " << larger;

    return 0;
}
```

```CPP
//세개의 시험을 통한 학생의 점수 찾기(max 스코어와 min 스코어의 평균값 찾기)
#include <iostream>
using namespace std;

int main(){
    int score1, score2, score3, maxScore , minScore , score;

    cout << "Enter the first score : ";
    cin >> score1;
    cout << "Enter the second score : ";
    cin >> score2;
    cout << "Enter the third score : ";
    cin >> score3;

    if(score1 > score2 && score1 > score3){
        maxScore = score1;
    }else if(score2 > score1 && score2 > score3){
        maxScore = score2;
    }else{
        maxScore = score3;
    }

    if(score1 < score2 && score1 < score3){
        minScore = score1;
    }else if(score2 < score1 && score2 <= score3){
        minScore = score2;
    }else{
        minScore = score3;
    }

    int temp = maxScore + minScore;
    if(temp % 2 == 1){
        temp+=1;
    }
    score = temp/2;

    cout << "Scores : " << score1 << " " << score2 << " " << score3 << endl;
    cout << "minimum and maximum score : ";
    cout << minScore << " " << maxScore << endl;
    cout << "Student score : " << score;
    return 0;
}
```

```CPP
// 소득 범위에 따른 세금 구하기
#include <iostream>
using namespace std;

int main(){
    double income, tax;
    bool bracket1, bracket2, bracket3, bracket4;
    double limit1 = 10000.00, limit2 = 50000.00, limit3 = 100000.00;
    double rate1 = 0.05, rate2 = 0.10, rate3 = 0.15, rate4 = 0.20;

    cout << "Enter income in dollars : ";
    cin >> income;

    bracket1 = (income <= limit1) && (income >= 0);
    bracket2 = (income > limit1) && (income <= limit2);
    bracket3 = (income > limit2) && (income <= limit3);
    bracket4 = (income >limit3);

    if(bracket1){
        tax = income * rate1;
    }else if(bracket2){
        tax = limit1 * rate1 + (income-limit1) * rate2;
    }else if(bracket3){
        tax = limit1 * rate1 + (limit2 - limit1) * rate2 + (income - limit2) *rate3;
    }else if(bracket4){
        tax = limit1 * rate1 + (limit2-limit1) * rate2 + (limit3-limit2) * rate3 + (income - limit3) *rate4;
    }else{
        cout << "Error! Invalid income!";
        return 0;
    }
    cout << "Income : " << income << endl;
    cout << "Tax due : " << tax;
    return 0;
}
```

```CPP
//날수 구하기
#include <iostream>
using namespace std;

int main(){
    int month;
    int day;
    int totalDays = 0;

    cout << "Enter month : ";
    cin >> month;
    cout << "Enter day of month : ";
    cin >> day;

    int m01 = 31;
    int m02 = 28;
    int m03 = 31;
    int m04 = 30;
    int m05 = 31;
    int m06 = 30;
    int m07 = 31;
    int m08 = 31;
    int m09 = 30;
    int m10 = 31;
    int m11 = 30;

    switch (month)
    {
        case 12 : totalDays += m11;
        case 11 : totalDays += m10;
        case 10 : totalDays += m09;
        case 9 : totalDays += m08;
        case 8 : totalDays += m07;
        case 7 : totalDays += m06;
        case 6 : totalDays += m05;
        case 5 : totalDays += m04;
        case 4 : totalDays += m03;
        case 3 : totalDays += m02;
        case 2 : totalDays += m01;
        case 1 : totalDays += 0;
    }
    totalDays += day;

    cout << "Day number : " << totalDays;
    return 0;
}
```



---

# 연습문제 코드 모음집

```CPP
//사용자로부터 부호 없는 두 자리 정수를 입력받고, 자리수의 값을 바꿔 출력하는 프로그램을 만드세요.
#include <iostream>
using namespace std;

int main(){
    int  num1;

    cout << "두자리수 숫자를 입력 하세요 : ";
    cin >> num1;

    int result1 = num1%10;
    int result2 = num1/10;

    cout << result1 << result2;
}
```

```CPP
//3개의 정수를 입력받고, 가장 작은것을 출력하는 프로그램을 만드세요
#include <iostream>
using namespace std;

int main(){
    int result;
    int num1, num2, num3;

    cout << "숫자 1 : ";
    cin >> num1;
    cout << "숫자 2 : " ;
    cin >> num2 ;
    cout << "숫자 3 : ";
    cin >> num3 ;

    if(num1 < num2 && num1 < num3){
        result = num1;
    }else if(num2 < num1 && num2 < num3){
        result = num2;
    }else if(num3 < num1 && num3 < num2){
        result = num3;
    }

    cout << "가장 작은 숫자는 : " << result << "입니다.";
}

```

```CPP
//사용자로부터 1~12 사이의 숫자를 입력 받고, 해당 월을 January, Feburary....와 같은 형태의 영어로 출력하는 프로그램을 만드세요
#include <iostream>
using namespace std;

int main(){
    int month;
    cout << "1~12까지의 숫자 중 하나를 입력하세요 : ";
    cin >> month;

    switch(month){
        case 1 : cout << "January";
                break;
        case 2 : cout << "Feburary";
                break;
        case 3 : cout << "March";
                break;
        case 4 : cout << "April";
                break;
        case 5 : cout << "May";
                break;
        case 6 : cout << "June";
                break;
        case 7 : cout << "July";
                break;
        case 8 : cout << "August";
                break;
        case 9 : cout << "Septenber";
                break;
        case 10 : cout << "Octover";
                break;
        case 11 : cout << "November";
                break;
        case 12 : cout << "December";
                break;
    }
}
```

```CPP
// 차량의 종류(일반 승용차는 'c' , 버스는 'b', 트럭은 't')와 주차장에서 차량이 있었던 시간을 입력받은 뒤, 다음과 같은 주차 요금에 따라 요금을 계산하는 프로그램을 작성하세요
//일반 승용차 : 시간당 2달러 , 버스 : 시간당 3달러, 트럭 : 시간당 4달러
#include <iostream>
using namespace std;

int main(){
    char Car;
    cout << "자동차 종류 : ";
    cin >> Car;

    int time;
    cout << "주차 시간 : ";
    cin >> time;

    switch(Car){
        case 'c':time *= 2;
                cout << "요금은 : " << time << "입니다";
                break;
        case 'b' : time *= 3;
                cout << "요금은 : " << time << "입니다";
                break;
        case 't' : time *= 4;
                cout << "요금은 : " << time << "입니다";
                break;
    }
}
```

```CPP
//학생의 점수를 기반으로 학점을 구하는 프로그램을 만드세요. 점수(0~100)를 3개 읽어서 다음과 같은 기준에 따라 학점 계산
#include <iostream>
using namespace std;

int main(){
    int score1, score2, score3, avg;
    cout << "과목 1 점수 입력(0~100) : ";
    cin >> score1;

    cout << "과목 2 점수 입력(0~100) : ";
    cin >> score2;

    cout << "과목 3 점수 입력(0~100) : ";
    cin >> score3;

    avg = (score1+score2+score3) / 3;

    if(avg >= 90){
        cout << "A";
    }else if(avg <= 90 || avg>=80){
        cout << "B";
    }else if(avg < 80 || avg >=70){
        cout << "C";
    }else if(avg < 70 || avg >=60){
        cout << "D";
    }else{
        cout << "F";
    }
}
```

```CPP
//대학교에서 학생의 총 수업료를 계산하고 출력하는 프로그램을 만드세요. 학생들은 최대 12학점에 대해 학점당 10달러의 수수료를 지불합니다. 12학점을 넘는 분량은 수수료가 없습니다. 등록비는 학생당 10달러라고 가정합니다.
#include <iostream>
using namespace std;

int main(){
    int Class, grade;
    cout << "학점 : ";
    cin >> grade;
	
    cout << "듣고 있는 수업의 개수 : ";
    cin >> Class;
	
    if(grade > 12){
        cout << grade * 10;
    }else{
        cout << grade * Class * 10;
    }
	
}
```

```CPP
//도매점에서 물건을 구매할때, 다음과 같이 수량에 따라 추가적인 할인이 들어갑니다. 물건 하나의 가격과 구매 수량을 입력받고, 할인이 적용된 전체 가격을 출력하는 프로그램을 작성하세요
#include <iostream>
using namespace std;

int main(){
    float price, quntity, sum;
    cout << "물건 하나의 가격 : ";
    cin >> price;
    cout << "물건 수량 : ";
    cin >> quntity;

    if(quntity>=1 && quntity <= 9){
        //할인율 : 0%
        sum = price * quntity;
        cout << sum;
    }else if(quntity >= 10 && quntity <=49){
        //할인율 : 3%
        sum = (price * quntity) * 0.07;
        cout << sum;
    }else if(quntity >= 50 && quntity <= 99){
        //할인율 : 5%
        sum = (price * quntity) * 0.05;
        cout << sum;
    }else if(quntity >= 100){
        //할인율 : 10%
        sum = (price * quntity) * 0.1;
        cout << sum << "입니다!" << endl;
    }
}
```
