

Filtering Code / Key 값 변경 시, 영향 받는 components

## Console
1. `filteringValueProps` : `src/components/console/shop/filterings`
	- 관리자 필터링 생성 폼
	- `Colour` / `Collections` 코드 값
2. `shop-product-properties` : `src/components/console/shop/products/properties`
	- 관리자 상품 필터링 옵션
	- 모든 코드 값 존재
3. `filteringForm` : `src/components/console/shop/filterings`
	- `setFilteringValue` : `keyCode` 값으로 입력 폼 초기화

4. `product controller` : `src/routers/api/console/shop/products`
	- 상품 저장 시, `Dimensions` 코드 값으로 숫자 타입 변경
## V1
1. `product-list-filter` : `src/compononets/client/shop/products/filter`
	- 상품 필터 chip -> text customizing
	- `methods - sync()` : 쿼리 값으로 filter chip 생성
	- `methods- remove()` : filter chip 제거 시, 쿼리 값 제거
1. `filter-menu` : `src/components/shop/products/filter/product-list-filter`
	- 각 `code` 에 따른 component 분류
	- `computed - count()` : 각 메뉴 별 선택 개수
	- `Colour - remove()` : 전체 삭제 기능
3. `filter-color`: `src/components/client/shop/products/filter/product-list-filter`
	- `mdi-check` : `하얀색` 일 경우, `border / black`
	- `methods - setItems()` : `Multi-colors -> custom background` 