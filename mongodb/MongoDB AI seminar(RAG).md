
정형 비정형 / 백터 데이터 등 새롭게 나오는 데이터의 종류들을 레거시를 기반으로 구축된 관계형 DB 기반으로 어려움

1. VPC Peering
2. Private Service Connect

운영 DB / 백터 DB 따로 운영?  
=> 통합 by atlas 
-> 하나의 데이터에 백터 데이터를 함께 저장

--> 하나의 데이터에 대한 리소스 용량 크기 증가
-> mongo에서 내부적으로 검색 노드를 생성 (내부적으로 자동 생성)
-> 하나의 DB로 보이지만 내부적으로는 search node가 백터 서치 / 나머지 production 


# Vertex AI Agent Builder

전통 소프트웨어 : 입력 / 연산 / 출력이 엄격함 -> 결정론적
LLM: 입력에 제한이 없음(텍스트 / 이미지,,,) -> 출력도 제한이 없음 

가장 큰 차이점 : 전통은 코딩이 필요 / LLM은 일반인도 자연어로 작업 가능

Model / Tool / Orchestrion

1. Model : AI 모델
2. Tool : AI 모델을 통해서 사용되는 다른 도구들 (API, ,,,)
3. Orchestrion: request / response을 매니징

Request에 따라 LLM(model)을 통해 prompt를 바로 request / response로 줄지, 해당 prompt를 LLM이 또 다른 Tool에 request 후 response로 보내줄 지 결정


google cloud - agent build - api activation enable



