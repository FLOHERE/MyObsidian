# 4.0 기본 API 프로그래밍
## 1. API
- 애플리케이션은 외부에서 제공되는 서비스를 자신의 프로젝트에 사용 가능
- API (Application programming Interface) : 애플리케이션을 제작하는 과정에서 외부 서비스를 사용할때 사용하는 일련의 규칙들의 집합

### 1. 라이브러리 API
- 애플리케이션이 라이브러리를 통해 서비스를 제공받을때 사용하는 API
- 애플리케이션은 자신의 프로젝트에 해당 라이브러리를 포함 시켜야 한다. 

- 기본 API
	- JRE가 제공하는 기본 클래스 라이브러리를 사용하는 API
	- 애플리케이션 실행에 기초가 되는 클래스
	- 프로젝트 생성시, 기본 포함
- 응용 API
	- 기본 클래스 이외의 라이브러리들을 자신의 프로젝트에 별도의 방법으로 포함 시켜야 함.
		- ex_) JAVA 테스트 프로그램, JavaFx 윈도 프로그램, JSP 서버 프로그램, Spring 프레임워크, 표준 프레임 워크 등...
		- ex_) 프로젝트 생성 과정중 포함, 메이븐의 \<dependency> 등을 사용
- 서버 API
	- 필요한 서비스를 그때그때 제공자인 서버에 요청하여 결과를 문서로 반환받는 방법
	- 인터페이스 : 클라이언트 애플리케이션과 서버 프로그램 상의 서비스 계약
		- 클라이언트 등의 요청과 서버의 응답 구성하는 방법에 대한 프로토콜
		- ex_) JSON, XML 등의 문서로 구현
- 기본 API 도큐먼트
	- 기본 클래스 라이브러리에서 제공하는 개발자 정의타입들에 대한 설명을 HTML 문서로 만든것.
	- 일종의 사용 설명서

# 4.1 예외 처리
## 1. 실행 오류
- 실행 과정에서 발생할 수 있는 오류는 에러와 예외로 구분

### 1. 에러와 예외
1. 에러(Error)
	- JVM(Java Virtual Machine)에 비정상적인 상황이 발생했을 때 오류 발생
	- ex_) 
		- OutOfMemoryError : 메모리 할당량이 모두 사용중일때
		- InternalError : 메모리 부족
		- StackOverflowError : 원래 있는 메모리 보다 더 많은 메모리를 불러올때
	- 개발자가 이를 미리 예측할수 없음 -> 시스템에 변화줘서 해결
2. 예외(Exception)
	- 개발자가 구현한 애플리케이션 코드에서 발생하는 오류
	- 이를 미리 예측 -> 대처
	- 주로 사용자의 잘못된 애플리케이션 조작 or 개발자의 잘못된 코딩으로 발생
		- 예외발생에 대한 대처가 없을때 : 에러 발생
			- JVM에 의해 강제 종료
	- 예외 처리를 수행 -> 이를 대처 -> 프로그램 종료 없이 정상실행 유지.

### 2. 예외
- JRE는 애플리케이션 실행 도중 예외 발생시, 해당 예외 클래스 사용 -> 예외 객체를 생성 -> 애플리케이션에게 던짐
	- 개발 코드에서도 수행 가능
>[!note] 던진다의 의미
>프로그래밍에서 던진다는 의미는 오류가 발생되었다고 말하는것임.

- 일반 예외와 런타임 예외
	- 일반예외(Compiler Exception, Checked Exception) : 예외처리 필수
	- 런타임 예외(Runtime Exception, Unchecked Exception) : 예외처리 개발자 선택(그래도 하는게 낫다)

#### 1. 일반예외
- Exception클래스를 상속하는 예외
	- (Exception 클래스는 자바의 기본 클래스 라이브러리에 존재.)
- 예외 발생 가능 코드에 대해 예외처리 코드의 존재 유무를 컴파일러가 체크
- 해당 코드가 존재하지 않으면 컴파일 오류 발생

#### 2. 런타임 예외
- Runtime Exception 클래스를 상속하는 예외
- 예외 발생 가능 코드에 대해 예외 처리를 개발자가 선택
- 만약 예외가 발생했는데 예외 처리를 하지 않았다면 ? 
	  -> 계속 넘겨지다가 결국 JVM에서 애플리케이션 중단.
- 런타임 예외에 대한 예외 처리 코드의 사용 여부는 개발자의 능력과 경험에 의해 이를 결정

- 주요 런타임 예외
	1. NullPointerException
	2. ClassCastException
	3. ArrayIndexOutOfBoundsException
	4. NumberFormatException

1. NullPointerException
	- 참조가 없는 상태에서 객체 멤버에 접근 할때
		- 멤버 접근 방법 : 점(.) 연산자
2. ClassCastException
	- 타입 변환이 불가능한 타입으로 타입 변환을 시도할때 발생하는 Exception

```JAVA
public class RuntimeExceptionExample{
	public static void main(String[] args){
		Dog dog = new Dog();
		changeDog(dog);
		System.out.println("첫번째 다운 캐스팅 수행 완료");
		
		Cat cat = new Cat();
		changeDog(cat); //ClassCastException 발생.
		System.out.println("두번째 다운 캐스팅 수행 완료");
	}
}
// Dog 클래스와 Cat 클래스는 형제 클래스로, 하나의 상속 라인 상에 위치하지 않아 두 클래스 사이의 타입 변환은 불가능. 즉 animal이 Cat 타입의 업캐스팅인 경우 (Dog)타입으로의 다운 캐스팅은 불가능.
```

3. ArrayIndexOutOfBoundsException
	- 배열에 대해 인덱스 범위를 초과한 원소를 접근하려고 할때 발생
		- 존재하지 않는 원소를 접근하려 할때 발생하는 Exception

4. NumberFormatException
	- 숫자로 변환할수 없는 문자열을 숫자로 변환하려고 할때 발생하는 Exception

## 2. 예외 처리
### 1. try-catch-finally
- 예외처리(Exception Handing)코드 : 프로그램이 비정상 실행될 때(예외가 발생 했을때) 프로그램 수행의 종료를 막고 정상 실행을 유지 할수 있도록 발생한 예외를 처리하는 코드
- try 블록 : 예외 발생 코드들 기술
	- 혼자 사용 X , 무조건 catch와 한세트
- catch블록 : 예외 발생시 해결하는 코드들 기술
- finally 블록 : 예외 발생 여부와 상관없이 무조건 실행하는 코드 기술(생략 가능)

- try 블록
	1. 예외 발생 
	2. 블록에 포함된 예외발생 이후의 문장들은 수행X
	3. 발생 예외를 받아들이는 catch로 이동
	- 만약 정상 수행되면 바로 finally로 이동
- catch 블록
	1. 블록 이전 위치의 소괄호"()"에 자신이 받아들일 예외의 종류를 기술
		1. catch 예약어 이후에 위치하면서 블록 이전에 위치하는 소괄호 블록은 
		   반드시 try블록과 한쌍.
	2. catch가 수행
	3. finally로 이동
- finally 블록
	- try블록에서 예외가 발생하면 catch 블록을 거쳐 수행
	- try블록에서 예외가 발생 X -> catch 생략 후 수행
	- finally 블록은 생략 가능(필요에 따라 구현)
	- 예외 발생 여부와 상관 X. 반드시 수행해야 하는 블록이 있으면 사용

### 2. 다중 catch와 멀티 catch
- 다중catch : 하나의 try에 여러개의 catch를 사용 
- 멀티 catch : 하나의 catch에서 여러 종류의 예외를 받아들임

- 다중 catch
	- 복수개의 catch를 사용 -> 각 catch가 받아들이는 예외들에 대한 비교 검토는 순차적으로 실행
		- 1번째 catch 예외인지 검토 -> 현재의 예외가 그 catch에서 제시한 예외가 아니면 다음으로 넘어감.(순차적)
	- catch의 위치
		1. 가장 작은 범위의 예외(후손 예외 클래스)를 가장 먼저 생성
		2. 넒은 범위의 예외(조상 예외 클래스)를 뒤에 위치
		-> try에 대한 catch는 복수 개가 존재하더라도 하나의 catch만 수행.
		(if 넓은 범위 -> 작은 범위 = 작은 범위 실행 x)

```JAVA
try{
	String[] str = {"노근배", "이승익"};
	System.out.println(str[0] + " , " + str[2]);
} catch(ArrayIndexOfBoundsException e){
	System.out.println("ArrayIndexOutOfBoundsException 실행");
} catch(Exception e){
	System.out.println("Exception 실행");
```

- 멀티 catch
	- 하나의 catch에서 여러 종류의 예외들을 받아들임

```JAVA
try{
	String[] str = {"노근배", "이승익"};
	System.out.println(str[0] + " , " + str[2]);
} catch(ArrayIndexOfBoundsException e | NumberFormatException e){
	System.out.println("숫자 문자열 사용 혹은 첨자 사용이 잘못됨");
} catch(Exception e){
	System.out.println("무언가 잘못됨");
```

## 3. 예외 해결
- catch에서 수행
- catch는 try에 종속
- try가 던지는 예외를 받아서 해결
	- try는 예외 발생 가능 코드를 수행 -> 예외 발생 -> catch로 던짐
	- catch는 항상 try와연결되어 함께 위치
- catch 구현 -> 발생 예외는 처리된 것으로 간주 -> 오류가 없는것으로 판단
  -> 프로그램 정상 실행 유지

- catch의 예외 해결 방법
	1. 예외 복구 : 문제의 원인 찾아 해결.
	2. 예외 떠넘기기(회피) : 발생한 예외를 자신이 호출한 메서드에게 해결하도록 넘겨줌.
	3. 예외 전환 : 발생한 예외를 일관된 방법으로 해결하도록 예외를 발생시켜서 던짐.
### 1. 예외 복구
- 어떤 시도에 의해 발생한 예외들에 대해 catch에서 이를 다시 시도하여 예외가 발생하지 않는 상황을 만드는 방법
- EX_) catch에서 재시도를 통해 예외 복구
	- 네트워크 구림 -> 서버 접속 어려움 -> 여러번 반복수행

```JAVA
while(maxRetry--> 0){
	try{
		if(success-- <= 0)
			break;
		System.out.println("서버 접속 시도");
		
		if(maxRetry <= 0)
			throw new SomeException();
	}catch(SomeException e){
		System.out.println("정해진 시간을 기다림");
		acessServer();
	}
}
```

### 2. 예외 떠넘기기
- 예외가 발생된 메서드에서 이를 해결하지 않고, 그 메서드를 호출한 메서드로 발생된 예외를 떠넘기는 방법
	- try-catch 미사용시 -> 자동으로 그 메서드를 호출한 메서드로 발생 예외가 떠넘겨짐.
	- 이때, 예외 발생 메서드의 머리에서 throws(throw가 아님)예약어 사용
	  -> 그 메서드 호출과 관련하여 try-catch 사용 여부를 판단할때 도움됨.

>\[ 예외 떠넘기기와 try-catch ]
> - 예외 발생 가능 코드 블록(try블록)의 내부 코드에서 다른 메서드를 호출하고 있을때
>   예외 해결을 위한 catch 블록을 어느 메서드에서 구현하느냐
>   => try블록의 위치에 따라 달라짐(try-catch는 한쌍이기 때문)
>   
> - 메서드 내부에서 다른 메서드 호출 -> 호출된 메서드에서 발생한 예외를 처리-> try-catch를 사용한 예외 처리 코드를 _호출한 메서드에 구현_ or _호출된 메서드에서 구현 하느냐_ 에 대한 문제 
>   
> 결론 : 예외 발생 가능 코드들에 대한 블록의 범위를 고려, try-catch의 위치를 결정
> 주의 : catch 블록에서 발생예외를 해결할때 사용할 정보가 어느 위치에 존재하는지도 생각해서 결정.

<2주차> 할차례
