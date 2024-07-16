```javascript
const RESERVATION_STATUS = {
    RESERVATION_AWAITING : { value : "RESERVATION_AWAITING", text : "예약대기" },
    RESERVATION_COMPLETED : { value : "RESERVATION_COMPLETED", text : "예약확정" },
    RESERVATION_CANCELED : { value : "RESERVATION_CANCELED", text : "예약취소" },
};

const PAYMENT_STATUS = {
    PAYMENT_AWAITING : { value : "PAYMENT_AWAITING", text : "결제대기" },
    PAYMENT_COMPLETED : { value : "PAYMENT_COMPLETED", text : "결제완료" },
    PAYMENT_CANCELED : { value : "PAYMENT_CANCELED", text : "결제취소" },
};
```

1. **예약대기**
    - 사용자가 예약폼은 작성하였지만 결제하지 않았을 경우
    - 사용자가 결제를 완료하였지만, 입점사 회원이 예약확정을 하지 않았을 경우
	- `RESERVATION_STATUS = RESERVATION_AWAITING`
	-  `PAYMENT_STATUS = PAYMENT_AWAITING || PAYMENT_COMPLETED`
2. **예약확정** 
	- 사용자가 예약폼을 작성하였고 결제를 완료한 상황이며
	- 입점사 회원이 예약확정을 결정하였을 경우
	- `RESERVATION_STATUS = RESERVATION_COMPLETED`
	- `PAYMENT_STATUS = PAYMENT_COMPLETED`
3. **예약취소**
	- 입점사 회원이 예약확정을 결정하기 전, 사용자가 예약취소를 결정하였을 경우,
	- `RESERVATION_STATUS = RESERVATION_CANCELED`
	- `PAYMENT_STATUS = PAYMENT_COMPLETED`
	- 사용자가 결제를 완료하였지만 입점사 회원이 예약취소를 결정하였을 경우,
	- `RESERVATION_STATUS = RESERVATION_CANCELED`
	- `PAYMENT_STATUS = PAYMENT_COMPLETED`
4. **결제취소**
	- 추후 PG 결제 취소 붙이기
	- `RESERVATION_STATUS = RESERVATION_CANCELED`
	- `PAYMENT_STATUS = PAYMENT_CANCELED`
5. **미결제**
	- 사용자가 예약폼을 작성하였지만 결제를 하지 않았을 경우,
	- `RESERVATION_STATUS = RESERVATION_AWAITING`
	- `PAYMENT_STATUS = PAYMENT_AWAITING`
	- 30 분 후 자동 삭제 (mongodb 서버에 따라 1~2분 차이는 발생)