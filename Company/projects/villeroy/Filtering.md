
## Flow
1. 사전에 `Key`, `Value` 모두 저장 후, 상품에서 해당 필터링될 `key` `value` 선택해서 저장
2. 상품 리스트에서 해당 카테고리에 모든 상품들의 필터링 `Key` `Value` 리스트 생성
## List
| Key                         | Value                                 | 값 정형화   |
| --------------------------- | ------------------------------------- | ------- |
| 면적 (Dimensions)             | `{ diameter, length, width, height }` | `false` |
| 색상 (Color)                  | `{ rgb, image, name }`                | `true`  |
| 가격 (Price)                  | `{ price, name }`                     | `false` |
| 브랜드 (Collections)           | `{ _category, name }`                 | `true`  |
| 재료 (Material)               | `{ name }`                            | `true`  |
| 식기세척기 안정성 (Dishwasher Safe) | `{ name }`                            | `true`  |
| 전자레인지 안정성 (Microwave Safe)  | `{ name }`                            | `true`  |
| 스타일 (Style)                 | `{ name }`                            | `true`  |
| 모양 (Shape)                  | `{ image, name }`                     | `true`  |
| 용량 (Volume)                 | `{ name }`                            | `false` |
| 카테고리 (Category)             | `{ name }`                            | `true`  |
