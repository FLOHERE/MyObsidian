>[!note] 테스트를 위한 프롬프트
>
>백엔드 테스트 사전 검증 및 디버깅 가이드 (제미나이 활용)
>
>이 가이드는 제공된 테스트 케이스(test-\*.json, test.pdf)와 시스템 요구사항을 바탕으로, 작성한 코드가 채점 기준을 통과하는지 제미나이를 통해 효율적으로 검증하는 방법을 다룹니다.
>
> # 1. 🎯 주요 채점 기준 체크리스트
>- 코드를 작성할 때 다음 항목들이 정확히 반영되었는지 확인해야 합니다. 이 항목들이 테스트 통과의 핵심입니다.
>
> 🌐 서버 및 인증 (항목 1, 2, 3)
>
>- [ ] 서버 포트 번호가 8080인가?
>
>- [ ] 관리자 계정 하드코딩 또는 DB 설정 완료 
>
>- [ ] 세션(Session) 기반 인증 사용 (JWT 사용 불가)
>
>- [ ] 로그인 성공 시 HTTP Response Header에 Set-Cookie 필드가 존재하는가?
>
>- [ ] 해당 쿠키에 JSESSIONID 값이 포함되어 있는가?
>
>📧 메일 서버 연동 (항목 6)
>
>- [ ] 접근 환경: 교내 무선랜 사용 필수 (외부망 접속 시 Timeout 발생)
>
>- [ ] 프로토콜 및 포트: pop3, 110
>
>- [ ] 서버 주소: 
>
>- [ ] 계정 정보: 
>
>- [ ] 보안 설정 해제: ssl: disable, startttls: disable
>
>- [ ] 메서드 파라미터 준수 (중요):
>
>inbox.open() 호출 시 Folder.READ_ONLY 옵션 사용
>
>inbox.close() 호출 시 false 전달 (메일 서버에서 메일 삭제 안 함)



# 1. 백엔드 서비스의 포트 번호
- 8080

# 2. 관리자 아이디/비번
- 아이디: ppt 참조
- 비번: ppt 참조

# 3. 로그인 인증 방식
- 세션(session) 방식을 사용해야 함.
- 로그인 응답 헤더(response header) 내에 Set-Cookie 필드가 있어야 하며, JSESSIONID값이 들어 있어야 함.

# 4. 테스트용 PDF 파일의 이름
- test.pdf

# 5. 테스트용 URL 링크의 주소
-  [https://www.saramin.co.kr/zf_user/jobs/relay/view?view_type=list&rec_idx=53510601&t_ref=jobcategory_recruit&t_ref_content=general#seq=0](https://www.saramin.co.kr/zf_user/jobs/relay/view?view_type=list&rec_idx=53510601&t_ref=jobcategory_recruit&t_ref_content=general#seq=0)

# 6. 이메일 POP3 정보
- 서버 주소: ppt 참조
 - 아이디: ppt 참조
 - 비번: ppt 참조

- (주의!!) (ppt 참조) 에 대한 접근은 교내의 무선랜을 통해서만 가능합니다.
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

