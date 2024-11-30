- git ignore 이란? 보안상이나 굳이 깃허브에 올리지 않아도 되는 파일들을 모아 놓은곳. 여기에 파일들을 넣어놓으면 깃에서 보이지 않는다.

# 1. .idea 파일
- .idea 파일 : 각 OS에 따라 다른 환경변수 파일이다.(intelij 설정파일)
- idea 파일을 ignore 해야 하는 이유 : 해당 파일을 깃으로 올리게 되면 서로 다른 IDE를 사용하는 사용자의 환경변수 파일이 의미가 없기 때문이다.(+버전 충돌) 따라서 git ignore 파일에 넣어 놓자.
	- git 폴더는 프로젝트의 모든 커밋 이력이 담겨 있는 폴더입니다.
	- .vscode 폴더는 vscode 개발도구 설정 정보
	- .settings 폴더는 eclipse 개발도구 설정 정보, .project .classpath 파일도 포함

# 2. git ignore 파일 생성(gitignore.io)
https://www.toptal.com/developers/gitignore
위 링크에 들어가면 git ignore 파일을 자동으로 생성해 준다.

검색창에 순서대로
1. 본인 컴퓨터 운영체제
2. 개발 툴 이름(eclipse, intelij ...)
3. 개발하고 있는 언어(java, python)
![[Pasted image 20241130180706.png]]

4. 그러면 이렇게 생긴 엄청 긴 텍스트 파일이 생긴다.
![[Pasted image 20241130180754.png]]

5. 다시 인텔리제이로 돌아와서 .gitignore 파일을 프로젝트 최상단으로 옮겨준다.(.idea 파일 밑)
	- 만약 gitignore 파일이 없다면 하나 만들어 주자.

6. .gitignore에 위 텍스트를 붙여넣기 해준다.
![[Pasted image 20241130182428.png]]

# 3. 문제 발생
- 참고로, 이미 작업을 완료한 후에 .gitignore 파일에 작성하면 계속해서 제외한 파일이 stage상에 올라가는 현상이 발생할 수 있다. 

- 그럴 때는 콘솔에  해당 명령어를 입력함으로써 문제 해결이 가능하다...고 하는데 나는 안되네

```git
git rm –cached .idea .iml -r
```

그래서 그냥 sourceTree에서 직접 무시를 하기로 함.
1. stage에 무시할 파일 (점세개) 클릭
2. 파일 무시 클릭
3. 확인 누르면 없어진다.

![[스크린샷 2024-11-30 오후 6.32.51.png]]
![[스크린샷 2024-11-30 오후 6.32.57.png]]![[스크린샷 2024-11-30 오후 6.33.02.png]]

해결 ㅎㅎ