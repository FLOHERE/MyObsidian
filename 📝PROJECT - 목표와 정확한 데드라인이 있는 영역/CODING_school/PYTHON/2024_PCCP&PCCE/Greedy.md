- Greedy(탐욕 알고리즘) : 선택의 순간마다 최고의 선택을 하는것.
- [[익명함수(Lambda)]] : 긴 def코드를 한줄로 줄여줌
	- 경우에 따라 callback함수와 비슷한 역할을 할수도 있음.
```python
def add(x, y):
    return x + y
-> 
add = lambda x,y : (x+y)
```
- [[재귀 함수]] : 자기 자신을 호출하는 함수
	- 반복문처럼 사용할수 있음
	- 재귀함수는 무한 루프에 빠질수 있으니 반드시 조건문을 작성할것(while과 유사)
	- 