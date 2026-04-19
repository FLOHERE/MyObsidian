>[!note] 테스트를 위한 프롬프트
>

# 1. 백엔드 서비스의 포트 번호
- 8080

# 2. 관리자 아이디/비번
- 아이디: admin@example.com
- 비번: 1234

# 3. 로그인 인증 방식
- 세션(session) 방식을 사용해야 함.
- 로그인 응답 헤더(response header) 내에 Set-Cookie 필드가 있어야 하며, JSESSIONID값이 들어 있어야 함.

# 4. 테스트용 PDF 파일의 이름
- test.pdf

# 5. 테스트용 URL 링크의 주소
-  [https://www.saramin.co.kr/zf_user/jobs/relay/view?view_type=list&rec_idx=53510601&t_ref=jobcategory_recruit&t_ref_content=general#seq=0](https://www.saramin.co.kr/zf_user/jobs/relay/view?view_type=list&rec_idx=53510601&t_ref=jobcategory_recruit&t_ref_content=general#seq=0)

# 6. 이메일 POP3 정보
- 서버 주소: mail.cakory.com
 - 아이디: jobinfo
 - 비번: swjob1234!

- (주의!!) mail.cakory.com 에 대한 접근은 교내의 무선랜을 통해서만 가능합니다.
	- 프로토콜: pop3
	- 포트번호: 110
	- ssl: disable
	- startttls: disable
 - inbox.open() 메서드에서 READ_ONLY를 사용할 것
 - inbox.close() 메서드에서는 false를 사용할 것

# 7. 테스트 컬렉션의 이름은 다음과 같이 정합니다.
  - test-번호.json
  - 예) test-1.json, test-2.json
  - 채점을 할 때는 이 번호 순서대로 컬렉션을 실행할 것입니다.


# 8. 테스트를 위한 샘플 파일

- newman을 사용하여 다음과 같이 테스트합니다.
- test.pdf, test-1.json, test-2.json, test-3.json 파일을 미리 다운로드 받아야 하고, newman이 설치되어 있어야 합니다.

`$ newman run test-1.json`

`$ newman run test-2.json` 

`$ newman run test-3.json`

