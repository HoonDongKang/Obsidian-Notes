
`User` -> `Workers` -> `scope`으로 분류

#### 등급 설정
1. Level로 새로운 등급 생성 (scope)
2. 새로운 담당자 생성(worker)시에 scope 설정
3. scope가 설정되어있지 않은 worker는 해당 user의 scope를 따라간다.

#### 구현
1. 로그인 시, Certification 값으로 **Store에 핸드폰 번호 / 성함 / 권한(scope)** 저장
	-> 같은 계정으로 접속하여도 어떤 worker인지 확인
2. 접속 worker 계정에 저장된 scope 값으로 메뉴 및 권한 설정
	-> 만약 권한 설정 안된 worker의 경우, `user scope`로 취급


#### 문제
1. worker로 접속하는 사람이 아니라면?
2. store 새로 고침 시에 worker 정보가 날라간다.
	=> `AppConsole`에서 `state.payload`의 `phone`으로 worker 추출