## Schma

```javascript
//COMMON_LOG
_id
_user //null 허용(로그인하지 않은 사람)
_createdAt

//COMMON_TAG_LOG
tag: "String"

//COMMON_SEARCH_LOG
value: "String"

//Optional
type: (TAG / SEARCH)
```
#### 검색 시 / 조회 시, 태그를 찍어준다.

#### `COMMON_TAG_LOG`
1. 태그 클릭 시, "#태그" 로 검색 -> `TAG_LOG` 생성
2. 태그가 걸린 스토리, 상품, 미니샵 조회 시 => 해당 대상의 태그 수 만큼 `TAG_LOG` 생성

- **로그인하지 않은 상태에서 태그 추천**
  -> 모든 태그에 대해 `count` 값으로 추천
- **로그인한 유저에 대한 태그 추천**
  -> 해당 유저가 남긴 태그의 `count` 값 추천

#### `COMMON_SEARCH_LOG`
1. 사용자가 검색 시, 검색어 -> `SEARCH_LOG` 생성

- **실시간 검색어**
  -> "현재"를 기준으로 파악
  -> 현재로부터 기준값(하루 전) 이전에 검색된 1~10등 데이터와 현재 1~10등 데이터 비교
	 - 순위값 함께 저장해서 증감 표시
	 - 새로 생겼을 시, new
	 -  `type: SEARCH`

```javascript
//GETS
- 추천 태그
//POST
- 태그 조회, 검색 시 저장
```