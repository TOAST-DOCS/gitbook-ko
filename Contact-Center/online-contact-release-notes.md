## Contact Center > Online Contact > 릴리스 노트

### 2023. 10. 17.

#### 기능 개선

- 트리거 실행 결과 추가 : 티켓 그룹 전달
- 티켓 생성 시 답변 템플릿을 미리 지정할 수 있는 기능 추가
- 티켓 목록 조회 성능 개선

### 2023. 09. 26.

#### 기능 개선

- 트리거 실행 결과 추가 : 접수유형 할당
- 모든 종류의 필드 속성에 대해 '노출 여부' 옵션 추가
- '담당그룹/담당자' 컴포넌트에 검색 기능 추가

### 2023. 09. 12.

#### 기능 개선

- 이슈관리 서비스에서 '이메일' 필드 제거 가능하도록 개선
- 티켓관리에서 접속 중인 메뉴 클릭 시 재접속 가능하도록 개선

### 2023. 08. 29.

#### 기능 개선

- 검색 기간 기본값 6개월로 변경
- 티켓관리 최대 조회 기간 6개월로 확대
- 티켓관리 템플릿관리 기능 개선
- 티켓관리 문의내역 검색 기능 추가
- 트리거 설정 시 두레이, 이메일 알림 '답변내용' 치환코드 추가 
- 외부 메일 계정으로 인입된 문의를 실시간으로 수집하도록 개선

### 2023. 08. 22.

#### 기능 개선

- 전반적인 검색 기능 강화

### 2023. 08. 08.

#### 기능 개선

- '장문 텍스트 박스' 유형에서 입력 글자수 확대
- 티켓관리 상단에 사용 채널별로 미니 전광판이 노출되도록 수정
- 티켓관리 내 티켓처리 영역 하단의 상담원 필드 정렬 개선
- OC 모바일 버전 제공을 위한 Push, API 등 시스템 업데이트

### 2023. 07. 25.

#### 기능 개선

- 티켓관리 미니전광판을 사용 채널에 따라 노출여부 적용
- 티켓관리 하단 프레임을 우측으로 이동하고 순서 조정 및 펼침/접힘 기능 추가
- 서비스 구분 탭 순서 조정 가능하도록 변경
- 헬프센터 문의하기 이메일 및 전화번호 작성 후 마스킹 처리 방식 변경

### 2023. 07. 11.

#### 기능 개선

- 토스트바 표시 위치 및 색상 변경
- 이슈이관 시 티켓정보에 이관한 서비스 또는 이관 받은 서비스 표시
- 헬프센터 POST 회원인증 방식에 옵션 기능 추가
- 티켓 목록에서 툴팁 및 새창 아이콘 삭제

### 2023. 06. 27.

#### 기능 개선

- 헬프센터 공지사항 검색엔진 추가
- 상담원 관리 '그룹 추가' 팝업 화면 UI 개선
- 첨부 파일 확장자별 아이콘 추가

### 2023. 06. 13.

#### 기능 개선

- 본문 이미지를 첨부로 전환되지 않도록 로직 변경
- 티켓관리/서비스관리/헬프센터 메뉴 내 UI 개선

### 2023. 05. 31.

#### 기능 개선

- 티켓 추출 시 마이그레이션 여부(Y/N) 표시
- 가이드 작성 시 글 본문 최대 길이 30,000 바이트로 제한

### 2023. 05. 23.

#### 기능 개선

- 공지사항 분 단위 예약 기능 추가
- 티켓 상세 화면 접수유형 검색 정렬 기준 수정
- 지식관리 상세 페이지 본문 높이 개선

### 2023. 05. 09.

#### 티켓관리 Main 화면 변경

- 목록/티켓정보/티켓상세 및 처리/문의, 지식관리 영역 frame 구분
- 각 frame에 대한 개인별 영역 설정 가능(frame 줄이기/와이드 스크린/펼침 고정 등)
- 전체 인입 현황 및 전화 인입 현황 미니 전광판 제공
- My 현황(처리중, 보류중, 약속콜, 이관중)을 통한 quick 검색
- '중요' 티켓 설정 후 모아보기 가능
- 티켓 처리 진행 시, 처리 상세 내용에 처리값이 함께 표시되도록 개선

#### 티켓관리 메뉴 정렬기준 변경 및 메뉴 추가/변경

- 개인화 영역/전체 영역에 대한 분리
- 그룹 내 전체 티켓: 하위 그룹별 티켓 확인 가능
- 전체 이관한 티켓: 이관(이슈 이관, Dooray! 이관)별 티켓 확인 가능

#### 전화 부문

- 서비스 관리 > 전화 > IVR Route 경로에 맞춰서 접수유형 자동 지정 가능
- 전화 티켓 통화시간 표시 기능 추가
- 호전환 시 메모 기능 추가
- 통화 예약 시(약속콜) 알림 기능 추가
- O/B 실행 시, 티켓 즉시 생성 기능 보완
- 상담 이력 저장 후 대기 상태 전환 기능 보완
- 통화중 상태에서, CTI 팝업에 전화 티켓이 생성된 서비스명 표시되도록 개선

#### Online Contact Main 대시보드 개선

- 금일 개인/채널별 티켓 현황 추가, 최근 24시간 티켓 현황 그래프에 '채널' 조건 추가되어 채널별로 데이터 조회 가능