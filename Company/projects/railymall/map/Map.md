
## Main
#### Flow
1. 사용자 접속 시, 위치정보값 도출
2. `lng`, `lat` store에 저장 후, 카카오 맵 위치
3.  `lng`, `lat` 로 `clusters` 값 도출 => 카카오 맵 레이어, 리스트 emit
4.  리스트 항목 클릭 시, 카카오 맵 중심 변경 및 레이어 팝업
5. `isSynced`값은 항목과 지도가 동일할 경우에 sync


좌표 클릭 