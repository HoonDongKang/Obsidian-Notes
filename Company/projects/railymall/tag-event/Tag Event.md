
### 개요 
태그 이벤트에 등록된 상품을 
- 태그된 상품 링크로 상품 상세페이지에 접속하거나 `( to visitor, to author )`
- 태그된 상품 링크에서 상품을 구매하면 `( to author )`
마일리지를 적립한다.

### 상세
#### 상품 등록
```javascript
//tag.js
startsAt: { type: Date, default: null },
endsAt: { type: Date, default: null },

author: {
    _user: { type: mongoose.Schema.Types.ObjectId },
    value: { type: String, default: null },
    unit : { type: String, enum: [null,...Object.keys(SHOP_POINT_UNITS)]},
    buy_value: { type: String, default: null },
    buy_unit : { type: String, enum: [null,...Object.keys(SHOP_POINT_UNITS)]}
},

visitor: {
    _user: { type: mongoose.Schema.Types.ObjectId },
    value: { type: String, default: null },
    unit : { type: String, enum: [null,...Object.keys(SHOP_POINT_UNITS)]}

},
```

`startsAt / endsAt`  : 해당 상품 이벤트 유효 기간
`author / visitor` : 작성자 / 방문자
`value / unit` : 마일리지 금액, 단위 (원, 비율)
`buy_value / buy_unit` 구매 시, 작성자가 받게 될 마일리지

#### 설계
1.  태그된 제품에 방문하였을 시,
	- 해당 제품 링크에 `_tag`,`_board` 값 쿼리 추가
	- 상품 페이지에 접속 시,  `_tag`,`accessToken`이 존재할 경우, `tag-log` 생성
	- `pre("save")` 를 통해 수동적으로 `userPoint` 생성
		1. 태그 이벤트에 존재하는가
		2. 작성자와 방문자가 같은가
		3. 사용자가 포인트를 받은 적이 있는가
		4. 상품의 이벤트 기간이 유효한가
	 - 모두 유효할 경우, 방문자, 작성자에게 각 마일리지 적립

2.  해당 링크에서 바로 구매하였을 시, 
	-  주문서로 넘어갈 때, `_tag`, `_board?` 값 같이
	- 결제 창에서 `purchase schema`에서 `validation` 후, `userPoint` 적립