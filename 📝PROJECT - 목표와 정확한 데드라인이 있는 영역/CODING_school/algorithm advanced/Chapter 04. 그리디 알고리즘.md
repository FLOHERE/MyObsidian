- 그리디 알고리즘이란 ? 
	- 매 순간 가장 좋은선택을 하는 알고리즘(최적의 선택)
	- 그리디가 유용한 경우 : 탐욕적 선택
		- 최적해 : 최적 부분 구조 + 가장 좋은 선택

## 1. 동전 거스름돈
- 거스름돈을 줄때 동전 개수가 최저가 되도록 한다.
- ex_) 거스름돈 : 730원
	1. 500원 : 1개
	2. 100원 : 2개
	3. 10원 : 3개
	=>>> 총 6개
- 최적해 : 모든 동전이 큰 단위가 작은 단위의 배수이기 때문에 큰 단위부터 거슬러 준다.

- 최소 코인 얻기 코드
	1. 리스트 사용 -> 큰 단위의 동전부터 처리
	2. 리스트 길이 정하기
	3. 빠진 만큼 재정의

```java
package MiddleTest;

import java.util.Scanner;

//물건을 사고 거스름돈을 동전으로 받아야 한다면?
//대부분의 경우 가장 적은 수의 동전을 원한다.
//거스름돈이 730원이라면?
//500원 동전 1개, 100원 동전 2개, 10원동전 3개인 총 6개를 거슬러 받는다.
public class Coins {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
		
        System.out.print("거스름돈을 입력하세요 : ");
        int coins = sc.nextInt();
        vending(coins);
    }
		
    public static void vending(int coins){
        int change[] = {500,100,50,10};
        int count = 0;
        for(int i=0;i<change.length;i++){
            count = coins/change[i];
            coins = coins%change[i];
				
            if(count != 0){
                System.out.println("%d 원짜리 동전 %d개".formatted(change[i],count));
            }
        }
		
    }
}

```
## 2. 다익스트라 알고리즘(최단거리 경로)
- a -> b -> c
- (a -> b 최단 경로) + (b -> c의 최단 경로) = (a -> c 의 최단 경로)

![[Pasted image 20250424094855.png]]
