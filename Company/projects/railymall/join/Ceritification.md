
1. KCP 본인인증
2. `_certification` DB 연락처, 성명, 생년월일 저장
3. `CI` 값 return;

### case 1 (일반 유저)
1. `/certify?type=PERSON/COMPANY` 로 접속
2. 본인인증 후, `CI, type` 중복 확인
3. 중복 없을 시에 `/agree?_certification=123&type=PERSON/COMPANY`

### case 2 (카카오 유저)
1.  카카오 서버로부터 kakao_id, info 받아옴
2. `isTemporal`로 해당 정보 저장 
3. `/certify?accessToken=123123` 로 접속 (type은 코드 상 person 고정)
4. 본인인증 후, `CI, type` 회원 정보 get (`user`)
5. `accessToken`의 `_user`로 회원 정보 get (`tempUser`)
6. `user` 와 `tempUser` 가 같으면 로그인 / 다르면 다른 카카오 ID로 계정이 생성되었다는 알림
7. `user`가 존재하지 않으면 회원가입 진행 (`/agree?_certification=123&accessToken=123`)


