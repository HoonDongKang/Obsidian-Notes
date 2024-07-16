
```javascript
_id,
_user : 결제해야할 사람,
_seller : 요금을 청구한 사람,
_product : 해당 상품,

code: 개인결제 인덱스
status: AWAITING / CONFIRM
expire: {
	startsAt,
	endsAt
},
price : 주문금액

payedAt: 결제일시
createdAt: 생성일시
```

1. 회원 요청으로 관리자가 개인 결제를 생성
2. 판매자, 상품, 금액, 유효기간으로 개인 결제 생성
3. 개인 결제 페이지에서 나이스 페이로 바로 결제
4. 기업 회원 페이지 -> 리스트, 결제 현황만 보여
5. 정산

	관리자 
	- 개인 결제 리스트 ( 관리자, 기업회원 )
	- 개인 결제 생성 ( 관리자만 )

	 클라
	 - 개인결제 리스트
	 - 결제창 (나이스페이)