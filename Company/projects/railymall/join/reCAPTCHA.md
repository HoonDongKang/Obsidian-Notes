https://cloud.google.com/recaptcha-enterprise/docs/overview?hl=ko
Googld Cloud에서 제공하는 캡챠 시스템

## reCAPTCHA vs reCAPTCHA Enterprise

![[Pasted image 20240307103656.png]]

## reCAPTCHA v2,v3

v2 - 이미지 방지
v3 - 자동 점수 매김 0 ~ 1 (4단계)  <--> enterprise (11단계)

![[Pasted image 20240307104801.png]]
form 을 보낼 때, google 서버로부터 token을 받아서 같이  back으로 전송
back에서 토큰 + secret 조합해서 구글 서버에 인증 -> 점수 제공