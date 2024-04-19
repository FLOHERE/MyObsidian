R 설치

![[Pasted image 20231113085228.png]]
1. https://cran.r-project.org/bin/windows/base/ 에 접속
2. 맨 위에  Download R-4.3.2 for Window를 클릭
(설치가 끝나면 한번더 클릭해서 계속 Next 항목 선택)

## R 실행

![[Pasted image 20231113085900.png]]
3. 콘솔창에 1+2 를 적어본다.실행이 잘 되는지 확인한다.

## Rtools 설치
![[Pasted image 20231113090447.png]]
4. Rtools 소프트웨어 설치
	- Rtools 소프트웨어 : R패키지에 필요한 시스템 라이브러리
	- https://cran.r-project.org/bin/windows/Rtools/
![[Pasted image 20231113090621.png]]

## Rtools 실행

5. R 운영 환경을 설정한다. 
	- 윈도우의 파일 탐색기를 이용하여 시스템의 운영 디렉터리를 설정한다. 
	- 운영 디렉터리 명 : C:/WORK_R
	- 설정한 시스템 운영 디렉터리를 getwd() 명령으로 확인한다.
![[Pasted image 20231113093747.png]]

![[Pasted image 20231113094726.png]]
- 경로가 이상한 곳으로 되어 있으면 C:/WORK_R로 바꿔줍니다.

![[Pasted image 20231113094808.png]]
- 작업 디렉토리 변경을 클릭해 줍니다.
![[Pasted image 20231113095020.png]]
- WORK_R 디렉토리를 선택해 줍니다.

![[Pasted image 20231113095059.png]]
- getwd() 명령어로 한번더 확인해 줍니다.
- 정상적으로 디렉토리 설정이 완료된것을 알수 있습니다.

## prettyR 패키지 설치

![[Pasted image 20231113095253.png]]
- install.packages("PrettyR") 
	-  명령어를 입력하고 확인을 누릅니다.

![[Pasted image 20231113095446.png]]
- 그럼 이런 창이 나오는데 korea를 찾아서 OK 버튼을 눌러줍니다.

7. 설치 되어있는 R 패키지를 확인한다.
- installed.packages
