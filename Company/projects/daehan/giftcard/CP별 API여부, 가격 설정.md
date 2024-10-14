
### 목적
CP 별로 제공되는 API 상품권 사용 여부 및 가격 설정 기능 추가.


#### 기능 ( 5 ~ 8일 )
1. (FE) 상품권 리스트 / 상세 페이지 dialog -> CP list -> API 가격 / 사용 여부 저장 폼  (1일)
2. (BE) CP 스키마 설계 (1일) 
	1.  apiDiscount : { \_id: salePrice }
	2.  findOne cp -> cp.apiDiscount.find(\_giftcard === \_id) => discount  || giftcard.cpamt
3. (BE) API 구매 설계 (2)
	1. `faceamt` : 액면가(권 종) / `cpamt` : api 가격 / `salesAmount` : `cpamt` * `quantity`
	2. CP확인 => api 가격 및 사용 여부 validation 추가
4. (FE&BE) 로그 (1)
	1. CP 캐시내역 구체화 (권 종, 차감 가격, 주문 정보,,)


#### Structure
`giftcard.cpamtOptions`
```javascript
_cp: { type: mongoose.Schema.Types.ObjectId },
price: { type: Number, default: 0 },
isApi: { type: Boolean, default: false },
```

### 

#### 1. isApi
 - `giftcard.isApi = false` - 조회, 구매 불가
 - `giftcard.isApi = true`
	 - `giftcard.cpamtOptions` 
		 -  `_cp 존재 X` - 조회, 구매 가능
	 - `giftcard.cpamtOptions` 
		-   `_cp 존재 O`
			 - `isApi = true` - 조회, 구매 가능
			 - `isApi = false` - 조회, 구매 불가

#### 2. cpamt
- `giftcard.cpamtOptions`
	- `_cp 존재 X` - `giftcard.cpamt`
	- `_cp 존재 O` 
		- `price > 0` - `giftcard.cpamt = 해당 price`
		- `price <= 0` - `gittcard.cpamt`