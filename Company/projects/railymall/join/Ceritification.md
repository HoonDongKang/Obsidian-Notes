
1. KCP 본인인증
2. `_certification` DB 연락처, 성명, 생년월일 저장
3. `CI` 값 return;

### case 1 (일반 유저)
1. `/certify?type=PERSON/COMPANY` 로 접속
2. 본인인증 후, `CI, type` 중복 확인
3. 중복 없을 시에 `/agree?_certification=123&type=PERSON/COMPANY`

### case 2 (소셜 로그인 유저)

[CI 값의 유저가 존재한다 - 이미 계정의 생성된 유저]
1. `const user = ci 값으로 찾은 유저`
2. `const tempUser = social id로 찾은 임시 유저`
3. `user {social} && tempUser {social}`  
   -> 동일 플랫폼 다른 계정으로 로그인 되어있음
4. `user {social} = tempUser {social}` 
5. `user.save(); tempUser.remove();`
6. user login

[CI 값의 유저가 없다 - 소설 회원가입]
1. `/agree?_certification=123`