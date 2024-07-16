
```javascript
//shop-alarm
_id: ObjectId
name: String
code: String
category: ALARM_CATEGORIES
type: ALARM_TYPES
template: String
taget: ALARM_TARGETS

//NOTI - discriminator


//TALK - discriminator
templateCode: String
receiverName: String
receiverNumber: String
sendAtFail: Boolean
```


```javascript
const ALARM_CATEGORIES = {
    PRODUCT: { text: "주문/배송", value: "PRODUCT" },
    COMMUNITY: { text: "커뮤니티", value: "COMMUNITY" },
    EVENT: { text: "이벤트/혜택", value: "EVENT" },
    MILEAGE: { text: "마일리지", value: "MILEAGE" },
    MONEY: { text: "정산", value: "MONEY" },
}

const ALARM_TYPES ={
	NOTI: { text: "플랫폼 알람", value: "NOTI" },
	TALK: { text: "알림톡", value: "TALK" }
}

const ALARM_TARGETS = {
	USER: { text: "고객", value: "USER" },
	SELLER: { text: "판매자", value: "SELLER" },
};
```
